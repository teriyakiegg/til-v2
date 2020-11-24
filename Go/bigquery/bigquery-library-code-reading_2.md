# bigquery library code reading 2

https://github.com/googleapis/google-cloud-go/tree/master/bigquery

## Client.Query(q string)
```
// Query creates a query with string q.
// The returned Query may optionally be further configured before its Run method is called.
func (c *Client) Query(q string) *Query {
	return &Query{
		client:      c,
		QueryConfig: QueryConfig{Q: q},
	}
}
```
構造体のQueryを返してるだけ  
Queryの型宣言は以下
```
// A Query queries data from a BigQuery table. Use Client.Query to create a Query.
type Query struct {
	JobIDConfig
	QueryConfig
	client *Client
}
```
このタイミングではJobIDConfig作ってないけど型は以下
```
type JobIDConfig struct {
	// JobID is the ID to use for the job. If empty, a random job ID will be generated.
	JobID string

	// If AddJobIDSuffix is true, then a random string will be appended to JobID.
	AddJobIDSuffix bool

	// Location is the location for the job.
	Location string
}
```
QueryConfigは無茶苦茶フィールドがある。色々指定できそう  
https://github.com/googleapis/google-cloud-go/blob/master/bigquery/query.go#L27-L135  
Qは実行するクエリ  
フィールド、一通り目を通してみて特に気になったのは以下
```
// Dst is the table into which the results of the query will be written.
// If this field is nil, a temporary table will be created.
Dst *Table
```
読み込むだけでDstが無い時は一時テーブルが作られる、という挙動っぽいのは知見  
Consoleの方でもクエリを発行したら結果が一時テーブルに保存されてるのが確認できる
```
// WriteDisposition specifies how existing data in the destination table is treated.
// The default is WriteEmpty.
WriteDisposition TableWriteDisposition
```
既存データを上書きしちゃいたい時に使える?  
→と思ったが、テーブルにあるデータ丸ごとだったから使い道なさそう  
https://cloud.google.com/bigquery/docs/reference/auditlogs/rest/Shared.Types/WriteDisposition
```
// AllowLargeResults allows the query to produce arbitrarily large result tables.
// The destination must be a table.
// When using this option, queries will take longer to execute, even if the result set is small.
// For additional limitations, see https://cloud.google.com/bigquery/querying-data#largequeryresults
AllowLargeResults bool
```
どういう風に使えるのかよく分からないが調べる価値ありそう  
→と思ったがdestがtableだから今のところ使い道なさそう
