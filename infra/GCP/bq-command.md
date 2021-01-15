# bq command

## 初回実行

google cloud sdkをインストールして認証通してる状態で、
```
$ bq ls
```
実行すると、projectIdのデフォルト選べと促され、選んだら利用可能なdatasetIdが表示されて、↓のような感じの ~/.bigqueryrc が作成される
```
$ cat ~/.bigqueryrc
project_id = projectId
credential_file = ~/.config/gcloud/hoge/hoge/hoge.json
```
project_idは上でデフォルトで選んだやつ  
credential_fileは認証系のやつで、中身見るとトークンとか色々格納してある

## 前提

※前提としてgcloudで認証済み。以下のコマンドで操作出来るプロジェクト一覧が表示出来る状態
```
$ gcloud projects list
```
以下のコマンドでbqコマンド操作対象のデフォルトに設定されたprojectを表示できる
```
$ gcloud config list
```
デフォルトのプロジェクトを変更したい場合のコマンドは以下
```
$ gcloud config set project <project name>
```
bqの時だけプロジェクトを変更したい場合のコマンドは以下
```
$ bq --project_id <project id>
```

## コマンド

### ls
- データセット一覧表示
- -p 付ければプロジェクト一覧表示
- 引数にデータセット名を渡すとテーブル一覧表示
- -j 付ければジョブ一覧表示

### mk
データセットやテーブルを作成できる  
jsonスキーマを使ってテーブルを作成&DAYでパーティション設定する例:
```
bq mk --table --time_partitioning_field hoge_column --time_partitioning_type DAY hoge-dataset.hoge-table json-path
```
https://cloud.google.com/bigquery/docs/schemas?hl=ja#using_a_json_schema_file

### rm
データセットやテーブルを削除できる  
テーブル削除例:
```
bq rm hoge-dataset.hoge-table
```

### head
`bq head データセット名.テーブル名` でテーブルの一覧を一部表示できる

### shell
bqコマンド専用のシェル環境に切り替えれる。コマンドからbqを省略できようになる

### show
データセットやテーブルの詳細情報表示

### query
`bq query --nouse_legacy_sql 'SQL文'` でok

テーブルの全行数をカウントする例:
```
$ bq query --nouse_legacy_sql 'SELECT COUNT(*) FROM `hoge-project.hoge-dataset.hoge-table`'
```
aliasとして使う場合
```
alias hogealias='bq query --nouse_legacy_sql '\''SELECT COUNT(*) FROM `hoge-project.hoge-dataset.hoge-table`'\'''
```
テーブルの中身全削除する例:
```
$ bq query --destination_table hoge-project.hoge-dataset --replace --nouse_legacy_sql 'SELECT * FROM `hoge-project.hoge-dataset.hoge-table` LIMIT 0'
```
https://cloud.google.com/bigquery/docs/writing-results?hl=ja

※selectの結果で上書きするテーブルの中身全削除のやつ、  
実行した後すぐ(5分ぐらい経つまで?)にinsertすると挙動がおかしくなって、insert結果の件数が少なかったりする。  
ので、テーブルの削除&作成でテーブルの中身全削除する方が良さげ  
と思ったらテーブルの削除&作成でも同じだった。挙動がおかしくなる件は公式ドキュメントで説明されていた  
```
BigQuery のストリーミング API はインサート率が高くなるように設計されているため、
ストリーミング システムを操作する際、基盤となるテーブルのメタデータの変更は結果整合が保たれます。
ほとんどの場合、メタデータの変更は数分以内にプロパゲート(伝播)されますが、その間は API レスポンスで、対象テーブルの不整合な状態が反映されることがあります。
```
https://cloud.google.com/bigquery/docs/error-messages#metadata-errors-for-streaming-inserts

開発でも運用でもテーブルの中身全消ししてすぐinsertする必要がある場合は無いはずなので、(今回はたまたまやってただけで必要性は無かった)  
こういう仕様がある、ということだけ認識しておく

### update
パーティションの有効期限セットする時とかに使う  
https://cloud.google.com/bigquery/docs/managing-partitioned-tables?hl=ja#bq  
https://qiita.com/Fea/items/c6ea946ad07e294450d6