# federated query

## 料金
- https://cloud.google.com/bigquery/docs/cloud-sql-federated-queries?hl=ja#pricing
- 基本的に、普通にBigQueryのデータセットにクエリ発行するのと同じ。
- Cloud SQLからとってきた分のデータサイズによって課金される

- https://cloud.google.com/sql/pricing?hl=ja#storage-networking-prices
- Cloud SQL側はBigQueryへの通信で、Googleプロダクトだからリージョンが同じであれば無料のはず