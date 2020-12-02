# JWT
## JSON Web Token の効用
https://qiita.com/kaiinui/items/21ec7cc8a1130a1a103a

## デメリットっぽいこと
```
JWTのデメリットはリアルタイムでユーザー無効化ができないこと
https://auth0.hatenablog.com/entry/2018/09/21/004131
```
理由は、DBにユーザーIDやアクセストークン自体を保存せず、アクセストークンは有効期限が切れるまでは有効だから。  
そのためトークンの有効期限は短く設定する模様