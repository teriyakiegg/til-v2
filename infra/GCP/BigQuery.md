# BigQuery

まずこの記事読むのが良さげ  
https://www.apps-gcp.com/bigquery-introduction/  
ジョブ備忘
```
「ジョブ」はクエリ実行・データ追加・テーブルのコピー等の実行単位となります。ジョブは非同期で実行され、実行中ジョブのステータスも取得が可能です。
```

- BigQueryには更新の必要がない毎回追加だけのデータを送るのが基本の使い方っぽい
- BigQueryはカラム志向なので、SELECTでカラム指定は鉄則
- BigQueryは正規化は不要

この動画良かった  
https://www.youtube.com/watch?v=3c9oEZC83Bs

```
BigQueryはWHERE句やLIMITを考慮せずに最初に全件を読み込みします
このためWHERE句を指定して処理するデータ量を減らしたと考えていても読み込むデータ量が多ければ速度は遅くなります。
テーブルの行数(データ量)を減らすこと、SELECTする列を減らすことが非常に重要です。
```
らしい

```
BigQueryではクエリのたびに対象のテーブルをフルスキャンします
スキャンしたテーブルのサイズによって料金が請求されるので、コストの削減のために日付などの単位でテーブルを分割するのがベストプラクティスとして知られています
```
らしい。  
日付毎のパーティション↓  
http://sucrose.hatenablog.com/entry/2016/07/17/232638

パーティションの種類
```
https://developer.medley.jp/entry/2019/03/15/145338
- 「取り込み時間で分割」されたテーブル
- 「特定のカラムに基づいて分割」されたテーブル
- 「時間ベースの命名方法を使用して分割」したテーブル
```

### 日付別シャーディングテーブル hoge_yyyymmdd
https://cloud.google.com/bigquery/docs/partitioned-tables?hl=ja
```
日付別シャーディング テーブルではなく、日付 / タイムスタンプ / 日時パーティション分割テーブルを使用することをおすすめします。
```

1TB毎に$5。1TBまでは無料。良心的。  
https://qiita.com/kamujun/items/ab3cd3e6f8934a01cbc8

### 料金
https://cloud.google.com/bigquery/pricing?hl=ja
```
100 MB を半月格納した場合、支払い額は $0.001（1/10 セント）です
500 GB を半月格納した場合、支払い額は $5 です
1 TB を 1 か月格納した場合、支払い額は $20 です
```
上記はストレージ料金。

クエリ発行の分析料金に関しては、  
- オンデマンド
- 定額
の二つがある。  
オンデマンドの場合、  
毎月 1 TB まで無料。  
1TBを超えるクエリに関しては、  
```
$6.00 per TB
```
リージョンが東京だと$6.00、米国だと$5.00だったりする。  
10GBで6円と覚えておく

### タイムゾーンの挙動↓
https://qiita.com/mswnoemail/items/04c2e47f6ff44a2248ec

### 権限によるbigquery操作可能範囲↓
https://christina04.hatenablog.com/entry/2017/06/22/010755

## データの取り込み方法は2つ
- Data Loading  
データをジョブでまとめて取り込む
- Streaming Insert  
リアルタイムに近い方式で取り込む

Data Loadnigは基本GCS経由っぽい

Streaming Insertは10万行/秒

クオータは割当という意味

スタンダードとレガシーSQLの分かりやすい違いはfrom テーブル名の書き方。

https://www.slideshare.net/GoogleCloudPlatformJP/google-cloud-google-bigquery-02

## BigQuery テーブルを分割する方法は3つ
```
取り込み時間: データの取り込み（読み込み）時間や到着時間に基づいてテーブルが分割されます。
日付とタイムスタンプ: TIMESTAMP または DATE 列に基づいてテーブルが分割されます。
整数範囲: テーブルは整数列に基づいて分割されます。
```
https://cloud.google.com/bigquery/docs/partitioned-tables?hl=ja  
stringのカラムとかで分割は無理。  

パーティションはあくまで、一つのテーブル。それを内部的に分けてselectしやすくする機能  
別のテーブルに分けるのはテーブル名に日付つけて、プログラム側ではそのテーブル名を指定してinsertするやり方、っぽい

## TRUNCATE文
使えない模様。
DELETEで全部消すときも直近30分以内にtabledata.insertallでレコードinsertしてたら削除できない。
```
ストリーミング（tabledata.insertall メソッド）を使用して最近テーブルに書き込まれた行は、
UPDATE、DELETE、MERGE ステートメントを使用して変更することはできません。
最近の書き込みとは通常、30 分以内に行われたものを指します。
テーブルの他のすべての行は引き続き、UPDATE、DELETE、MERGE ステートメントを使用して変更できることに注意してください。
```
https://cloud.google.com/bigquery/docs/reference/standard-sql/data-manipulation-language#limitations  
テーブル再作成かselect LIMIT 0の結果で上書きするかの方法がある模様。  
https://snowsystem.net/cloud/gcp/bigqury/truncate/

アップデートでTRUNCATE文使えるようになったっぽい(まだ試してない)  
https://cloud.google.com/blog/ja/products/bigquery/smile-new-user-friendly-sql-capabilities-bigquery  
https://cloud.google.com/bigquery/docs/reference/standard-sql/dml-syntax#truncate_table_statement

## ネストされたkey valueの取り出し
UNNEST使って頑張る
```
SELECT (SELECT value FROM UNNEST(params) WHERE key = "hoge") AS hoge
```

https://aride.medium.com/approaches-to-store-key-value-pairs-in-google-bigquery-6840d036bc10

## connection not found
https://serverfault.com/questions/1047304/gcp-bigquery-fedarated-query-to-cloudsql-gives-connection-not-found-error

ロケーションの異なるデータセット間でクエリをいじると発生するっぽい

ロケーションがどうしても変えられない場合(firebaseと連携してるやつとか)、  
下記のドキュメントにあるように異なるロケーション間を跨ぐデータセットの定期コピーがあるので活用すべし。  
https://cloud.google.com/bigquery/docs/locations?hl=ja#moving-data  
料金は今は機能がベータ期間中なので無料、  
期間後はGB単位$0.08になる模様。  
毎日コピー走らせても毎回全テーブルではなく差分のみのコピーなので、1日分のデーブルのサイズがよほどデカく無ければコストは気になるほどではないはず

## SQL format
Cmd + Shift + f

## ASの後のクオーテーション
MySQLのSQL文だとクオーテーション必要だが、BigQueryのSQL文だとクオーテーションはエラーになるので不要

## NOW()
MySQLのSQL文だとNOW() - INTERVAL 7 DAYとかで書けるが、BigQueryのSQL文だとDATE_SUB(CURRENT_DATE(), INTERVAL 7 DAY)とかで書く必要あり

## 取り込み方法(大まかに)
- ログルーター経由。(不要なカラムも入ってくるのが残念ポイント)
- GoやRubyとかなんでもクライアントライブラリあるものでBigQueryのAPIを叩いて追加(これだと必要なカラムのみ指定できる)
- データ転送機能
- スケジュールされたクエリ(クエリ結果をテーブルに保存)
- あとは手動でcsvアップロードとか

## Firebaseログのevent_dateをパース
```
parse_date('%Y%m%d', event_date) AS event_date
```
https://medium.com/google-cloud-jp/firebase-event-analysis-2-sql-9877ca0b79b5

## 予約語がカラム名
カラム名をバッククォートで挟めばOK

## REQUIREDとNULLABLE
REQUIREDのSTRINGは空文字指定してエラーにならない。  
カラム自体に何も指定しなかったりNULLを指定した場合はエラー