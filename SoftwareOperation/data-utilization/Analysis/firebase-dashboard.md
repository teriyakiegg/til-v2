# firebase dashboard
モバイルアプリで使ってるfirebaseの分析のダッシュボード見た感じ、  
手軽に大体みたい情報が見れるからすごい

## user_id
```
Swift

Analytics.setUserID("123456")

ユーザー ID を設定すると、今後のすべてのイベントにはこの値が自動的にタグ付けされます。
BigQuery で user_id の値を照会すると、その ID にアクセスできます。
```
https://firebase.google.com/docs/analytics/userid?hl=ja

## firebaseとBigQueryの連携
https://support.google.com/firebase/answer/6318765?hl=ja