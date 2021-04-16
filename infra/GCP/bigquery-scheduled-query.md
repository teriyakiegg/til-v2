# bigquery scheduled query
- スケジュールされたクエリを設定する際は、誰のアカウントでそのクエリを実行するか設定できる。
- 設定を省いたらそのクエリを設定したアカウント情報が使われる模様
- スケジュールされたクエリで「Access denied」のエラーが出たらアカウントの権限周りを疑うべし
  - スケジュールされたクエリ詳細画面の右上にある「さらに表示」をクリックして認証情報を更新→BigQuery Data Transfer Service の権限承認でクリアした
- サービスアカウントで実行するように設定しようとして、Requested entity was not found. エラーで沼にハマった
- 本当に沼。

```
注意: スケジュールされたクエリで使用される認証情報をサービス アカウントに変更する操作は、現在 Cloud Console ではサポートされていません。
```
https://cloud.google.com/bigquery/docs/scheduling-queries?hl=ja#updating-a-scheduled-query

- 顛末は上記のように変更は不可。初回でサービスアカウント設定すればok。ちゃんと設定されてるかは詳細画面からは見れない。クエリ履歴を見るとサービスアカウントで実行できたか確認できる。クエリ履歴確認が味噌だった

- スケジュールされたクエリの実行に必要なサービスアカウントの権限は以下必要っぽい
```
BigQuery Connection User
BigQuery データ編集者
BigQuery ジョブユーザー
BigQuery Data Transfer Service エージェント
```