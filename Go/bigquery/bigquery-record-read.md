# bigquery record read

1. まずパッケージ落とす (google cloud sdkのインストール&認証周りは済んでる前提)

```
$ go get cloud.google.com/go/bigquery
```
2. 公式ドキュメントのコードを参考に疎通確認してみる
```
$ go run hoge.go
bigquery.NewClient: bigquery: constructing client: google: could not find default credentials. See https://developers.google.com/accounts/docs/application-default-credentials for more information.
exit status 1
```
3. ↑こんなの出たら、デフォルト認証なるものが設定されていないということ。
↓の記事が認証周りの説明が詳しかった  
https://medium.com/google-cloud-jp/gcp-%E3%81%A8-oauth2-91476f2b3d7f
```
$ gcloud auth application-default login
```
このコマンド叩けば~/.config/gcloud/application_default_credentials.json ここにトークンが保存され、プログラムからGCPのapi叩けるようになる

locationはセットしなくても動いた。

バッククォートを使って複数行の文字列としてsql文宣言しておくと良い感じ。  
sql文内にバッククォートがある場合は頑張って別の文字列として結合すればok
```
const query = `
SELECT
  hoge
FROM
  ` + "`hoge`" + `
WHERE
  hoge = hoge
`
```

## クライアント用意
```
import ( // 必須のやつは以下三つ
        "context"
        "cloud.google.com/go/bigquery"
        "google.golang.org/api/iterator"
)

projectID := "my-project-id"
ctx := context.Background()
client, err := bigquery.NewClient(ctx, projectID)
if err != nil {
        return fmt.Errorf("bigquery.NewClient: %v", err)
}
defer client.Close()
```
## クエリ発行
```
q := client.Query(`
    SELECT year, SUM(number) as num
    FROM ` + "`bigquery-public-data.usa_names.usa_1910_2013`" + `
    WHERE name = "William"
    GROUP BY year
    ORDER BY year
`)
it, err := q.Read(ctx)
if err != nil {
    // TODO: Handle error.
}
```
client.Query()でbigquery.Query作成して、  
bigquery.Query.Read()してiteratorを取得するのが一番シンプルな方法。  

あと、
```
You can also start the query running and get the results later. Create the query as above,
but call Run instead of Read. This returns a Job, which represents an asynchronous operation.
```
というのものある。google公式ドキュメントのサンプルではこっちで書かれてる。  
Run()だとクエリの実行を非同期で走らせて、好きなタイミングで結果の取得できる模様(別プロセスからでも)。  
Run()で取得できるjobからjob.ID()でジョブのIDを取得でき、clientとcontextとjobIDがあればどっからでもjobを取得できる  
job.Read()すると、query.Read()と同じでiterator取得できる。  
query.Read()は実は、query.Run()とjob.Read()をまとめたもの。  
なので、直列でquery.Run()とjob.Read()するならquery.Read()すれば良いということだと思われる  
公式ドキュメントはjob.Wait()してるのが味噌っぽい。こいつあると同期的に動くっぽい。じゃあquery.Read()で良いのでは?を解明したい。が、どっちでも良さそうなので深掘りしない

## 取得レコード
```
[111 1111 11 11 2020-09-04 20:53:42]
```
こんな感じで、1レコード1配列で取得できる。  
配列の中のデータ取得する際は、型のbigquery.Valueはinterface{}なので、
```
hoge, ok := row[0].(float64)
if !ok {
  log.Print("convert hoge error: value=", row[0])
}
```
てな感じで型アサーションで取得する。(型はbigqueryで定義された型が渡される)

Bigqueryとgolangでの型の互換↓  
https://godoc.org/cloud.google.com/go/bigquery#RowIterator.Next

bigquery.Valueではなくて、クエリ結果のカラムに対応する構造体を用意してそれにはめ込むことも可能  
https://godoc.org/cloud.google.com/go/bigquery#RowIterator.Next

構造体のフィールドは先頭文字大文字じゃないと認識されないので注意  
errはちゃんと仕事してるのか不安になったが、パースエラーとかだとちゃんとエラー出た。  
先頭大文字じゃない場合は単にそのフィールドは無視されるだけなのでエラーにならない、と考えると納得

- APIから取得したレコードの総数はRowiterator.TotalRowsで取得できる

## 割当と上限
```
jobs.query リクエスト
jobs.query メソッドは SQL クエリを同期的に実行し、指定したタイムアウト期間内にクエリが完了した場合はクエリ結果を返します。

レスポンスの最大サイズ: 10 MB: デフォルトでは、結果のページあたりに返されるデータ行の最大行数は設定されていません。
ただし、レスポンスの最大サイズは 10 MB に制限されています。返される行数は maxResults パラメータを使用して変更できます。
```
https://cloud.google.com/bigquery/quotas?hl=ja#jobsquery_requests

試しに結果が30MBぐらいあるSQLをgoから発行したところエラーは発生せず正常に実行が完了。  
調査したところ、APIへの一回のリクエストで取得できる最大サイズが10MBなだけで、  
クライアント的には普通にfor文でiteratorのNext()を呼んでおけば、  
```
1. jobs.query(API)で一回で取ってこれる分のレコードを取得。iteratorではそれを参照する
2. 取得したレコードを参照しきったらjobs.getQueryResults(API)で取って来れなかった続きのレコードを取得
3. 全てのレコードを取得し切るまで2のループ
```
という挙動をする模様  
https://cloud.google.com/bigquery/docs/reference/rest/v2/jobs/query
結論としては、10MB上限を回避するための対策は必要なさそう

## API仕様
https://cloud.google.com/bigquery/docs/reference/rest/v2/jobs/query
