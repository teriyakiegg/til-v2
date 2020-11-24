# bigquery library code reading 3

https://github.com/googleapis/google-cloud-go/tree/master/bigquery

## Query.Read(ctx context.Context)
```
// Read submits a query for execution and returns the results via a RowIterator.
// If the request can be satisfied by running using the optimized query path, it
// is used in place of the jobs.insert path as this path does not expose a job
// object.
```
https://github.com/googleapis/google-cloud-go/blob/master/bigquery/query.go#L328-L369  
traceは置いておいて、  
1. まずQuery.probeFastPath() (probeは探るという意味)
  - エラーあればQuery.Run()とJob.Read()した結果を返して終わり
2. Query.client.runQuery()
3. 必要最低限のJob型の変数を生成
4. runQuery()のジョブが完了してるか判定
  - 終わってなかったら直前に作ったjobを使ってjob.Read()した結果を返して終わり
5. rowSource型の変数を生成して、それを使ってnewRowIterator()した結果を返して終わり
