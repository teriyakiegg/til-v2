# gcloud logging comannd
## STACKDRIVERのログをダウンロードする
http://blog.nizyu.xyz/blog/gcloud_logging_read/

```
$ gcloud beta logging read --format json '
resource.type="http_load_balancer"
httpRequest.requestUrl="https://hogehoge.com/aaa"
receiveTimestamp>="2017-10-10T00:00:00"
receiveTimestamp<="2017-10-10T23:59:59"
' | jq -r '.[] | .receiveTimestamp' | awk -F ':' '{print $1}' | sort | uniq -n | sort -n
```
こんな感じでシェル芸でログを自分の見たい形で集計して取得できる。

betaは今はいらなそう  
https://cloud.google.com/sdk/gcloud/reference/logging/read

## csvで取得
jsonじゃなくてcsvで取得する方が楽そう。整形はExcelで
```
$ gcloud logging read --format="csv[separator=', '](timestamp,httpRequest.requestUrl)" 'resource.type="http_load_balancer" timestamp>="2021-01-10T15:00:00" timestamp<="2021-01-11T14:59:59"' > test.csv
```