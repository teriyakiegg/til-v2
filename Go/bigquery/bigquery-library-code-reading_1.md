# bigquery library code reading 1

https://github.com/googleapis/google-cloud-go/tree/master/bigquery

## NewClient(ctx context.Context, projectID string, opts ...option.ClientOption)
```
// NewClient constructs a new Client which can perform BigQuery operations.
// Operations performed via the client are billed to the specified GCP project.
func NewClient(ctx context.Context, projectID string, opts ...option.ClientOption) (*Client, error) {
	o := []option.ClientOption{
		option.WithScopes(Scope),
		option.WithUserAgent(fmt.Sprintf("%s/%s", userAgentPrefix, version.Repo)),
	}
	o = append(o, opts...)
	bqs, err := bq.NewService(ctx, o...)
	if err != nil {
		return nil, fmt.Errorf("bigquery: constructing client: %v", err)
	}
	c := &Client{
		projectID: projectID,
		bqs:       bqs,
	}
	return c, nil
}
```
オプションは以下URLに載ってる諸々の情報を渡せそう    
https://pkg.go.dev/google.golang.org/api@v0.32.0/internal#DialSettings  
```
DialSettings holds information needed to establish a connection with a Google API service.
```
とあるようにGoogle API serviceに接続する際に渡せる情報のよう。
認証周り色々あるが、今のところアプリケーションデフォルト認証で少なくともローカル開発では問題無し  
今回のbigqueryクライアント使用ではこのオプションは活用場面は無いはずなので深入りしないでおく  


Clientの型宣言は以下
```
// Client may be used to perform BigQuery operations.
type Client struct {
	// Location, if set, will be used as the default location for all subsequent
	// dataset creation and job operations. A location specified directly in one of
	// those operations will override this value.
	Location string

	projectID string
	bqs       *bq.Service
}
```
bqは以下のimport
```
bq "google.golang.org/api/bigquery/v2"
```
https://pkg.go.dev/google.golang.org/api/bigquery/v2
```
Package bigquery provides access to the BigQuery API.
This package is DEPRECATED. Use package cloud.google.com/go/bigquery instead.
```
とあるように、このv2のpackageは古いやつの模様。  
新しくなった方から古い方のpackageを呼び出してるように見える

このpackageに定義されてるNewService()とそこから呼ばれてるNew()は以下  
https://github.com/googleapis/google-api-go-client/blob/master/bigquery/v2/bigquery-gen.go#L112-L159  
basePathは
```
const basePath = "https://bigquery.googleapis.com/bigquery/v2/"
```
でクライアント共通のbigqueryのAPI指定してる 　
処理内容はざっくりServiceを作って返してる  
Serviceの型宣言は以下
```
type Service struct {
	BasePath  string // API endpoint base URL
	UserAgent string // optional additional User-Agent fragment

	Datasets *DatasetsService

	Jobs *JobsService

	Models *ModelsService

	Projects *ProjectsService

	Routines *RoutinesService

	Tabledata *TabledataService

	Tables *TablesService
	// contains filtered or unexported fields
}
```
Projects -> Datasets -> Tables -> Tabledata があって、Jobsがあっては分かるが、ModelsとRoutinesが何かは分からぬ  
とりあえず、NewClient()が何してるかはぼやっと分かった  
