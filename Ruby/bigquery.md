# bigquery
insertはこんな感じで書ける
```
def insert(dataset, table, rows)
  dataset = Google::Cloud::Bigquery.new(bq_args).dataset(dataset) # bq_argsは省略
  table = dataset.table(table)
  response = table.insert(rows)
  raise "BigQuery insert failed. dataset:#{dataset.dataset_id}, table:#{table.table_id}, error:#{response.insert_errors.inspect}" unless response.success?
end
```