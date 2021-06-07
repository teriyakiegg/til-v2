# cloud scheduler
https://cloud.google.com/scheduler/docs/?hl=JA

- 普通にcronjob感覚で設定できる。ゴイス
- cronjobでサービスのステータスを取得できるAPI叩く→レスポンスのBODYに含まれるjsonをCloud Loggingで拾う→Cloud Monitoringで必要に応じて通知
- をやろうとしてみたが、レンスポンスのBODYはLoggingに拾われないので、上記の使い方は無理
- 同じこと質問してる人いるが↓ 「Stackdriver does not log the HTTP Response body.」
https://stackoverflow.com/questions/57099284/view-response-body-on-google-cloud-scheduler-logs