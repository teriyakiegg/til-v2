# bigquery record insert
https://cloud.google.com/bigquery/streaming-data-into-bigquery?hl=ja

- Uploader()はdeprecated。今はInserter()
- Inserterの説明
```
An Inserter does streaming inserts into a BigQuery table. It is safe for concurrent use.
```
https://pkg.go.dev/cloud.google.com/go/bigquery

- Putの方法はSave()定義するのとしないのがある。詳細は上記リンクと以下リンク  
https://christina04.hatenablog.com/entry/2017/06/22/010755

insertIDを指定しないでも、isertID割り振ってくれるか心配だったが、色々試してた時に出た以下のエラーログを見る限り、insertIDは各行ごとに割り振られてそう
```
10000 row insertions failed (insertion of row [insertID: "hogehogehoge"; insertIndex: 0] failed with error:
{Location: "timestamp"; Message: "This field is not a record."; Reason: "invalid"},
```

## 呼び出してるAPI
```
Post "https://bigquery.googleapis.com/bigquery/v2/projects/projectName/datasets/datasetName/tables/tableName/insertAll?alt=json&prettyPrint=false"
```

## 全てのAPIリクエストの割当と上限
https://cloud.google.com/bigquery/quotas?hl=ja
- ユーザーごとの 1 秒あたり API リクエスト数 - 100 件
- 宛先テーブルの日次更新回数上限 - 1 日あたりテーブルごとに 1,500 回の更新  
*ただし以下に記載の通り、DMLステートメントはセーフらしい。逆に何が出来なくなるのかよく分からないが、insertとかでのapi呼び出し回数は気にしなくて良さそう
```
BigQuery の DML ステートメントに割り当ての上限はありません。
ただし、DML ステートメントは 1 日あたりのテーブル オペレーションの数と 1 日あたりのパーティション変更の数にカウントされます。DML ステートメントはこの上限により失敗することはありません。
```

## ストリーミング挿入の割当と上限
- リクエストあたりの最大行数: リクエストごとに 10,000 行  
越すと以下のエラーが返ってくる
```
googleapi: Error 400: too many rows present in the request, limit: 10000 row count: 10001., invalid
```
https://cloud.google.com/bigquery/quotas?hl=ja#streaming_inserts
```
最大行数は 500 行をおすすめします。
一括処理することでパフォーマンスとスループットをある程度向上させることはできますが、リクエストごとのレイテンシは高くなります。
リクエストごとの行数が少なく、各リクエストにオーバーヘッドがあると取り込みの効率が下がります。
また、リクエストごとの行数が多すぎるとスループットが下がります。

推奨される最大行数はリクエストごとに 500 行ですが、
代表データ（スキーマとデータサイズ）を使用したテストを実施すると適切なバッチサイズを判断しやすくなります。
```
- スループット  
時間あたりの処理能力
- レイテンシ

『[用語]スループットとレイテンシー』  
https://qiita.com/kkino1985/items/de3e852d9bd8f4deb01c  
『スループットとレイテンシ - 日報 #143』  
http://tom-rc.hatenablog.com/entry/2015/04/30/231232

- バッチサイズ  
全体のデータから個別に分けたサイズ
