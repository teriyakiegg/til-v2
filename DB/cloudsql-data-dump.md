# cloudsql data dump
https://cloud.google.com/sql/docs/mysql/import-export/exporting?hl=ja#gcloud_1

本番データをローカルにdumpして動作確認するのに使ったが、  
gtid周りで毎回warning出て、reset master; する手間が発生した  
--set-gtid-purged=OFFオプション付ければ回避できるのかも