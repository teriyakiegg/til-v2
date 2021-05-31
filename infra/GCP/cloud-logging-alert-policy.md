# cloud logging alert policy
## Stackdriver Alerting Policy - Need To Filter On JSON Payload
https://stackoverflow.com/questions/59755930/stackdriver-alerting-policy-need-to-filter-on-json-payload

- 日本語だと「ログの指標」だった
- https://cloud.google.com/logging/docs/logs-based-metrics/labels?hl=ja#create-label

## Metrics Explorer
- ログの指標を使ってMetrics Explorerでグラフ表示させようとする時、データが表示されなくて原因を探るハマりに遭った
- が、過去分は表示されず、指標を作って以降に指標の条件に合致するログが生まれたものだけが表示される模様。拍子抜けだった

## Alert Policy
- 例えば、Aggregatorをcountにして、Periodを1 minute、Condition triggers if "Any time series violates"でCondition is above Threshold 1 For 1 minuteとかでやると
- 1分おきに条件に合致するログをチェックして、合致するログが一分間に1つ以上あればすぐに通知発動、になるはず
- 通知先はメールとかSlackを指定できる