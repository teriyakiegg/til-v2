# CloudLogging to BigQuery
https://cloud.google.com/logging/docs/export/configure_export_v2?hl=ja

Cloud Loggingにはログが溜まっているが、  
BigQuery側には蓄積されてない場合、Clound Loggingのみにあるデータの分析はだいぶ厳しい。  
gcloudコマンドで手元に落としてゴニョることはできるが、  
素直にログルーターの設定をしてBigQuery側に蓄積するのが良さそう