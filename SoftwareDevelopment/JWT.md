# JWT
## JSON Web Token の効用
https://qiita.com/kaiinui/items/21ec7cc8a1130a1a103a

## JWTの仕様
```
token = encode_base64url(header) + "." + encode_base64url(payload) + "." + encode_base64url(signature)

header = JWTの署名アルゴリズム等に関するメタデータが入ったJSON文字列

payload = 任意のデータが含められるJSON文字列

signature = 署名 = sign(signingKey, encode_base64url(header) + "." + encode_base64url(payload))
sign = 署名に使うアルゴリズム（headerにて指定されている）
```
https://qiita.com/take4s5i/items/009b0b6797b752921a78

headerとpayloadはBase64urlエンコードした文字列なので、デコードが容易にできる

## デメリットっぽいこと
```
JWTのデメリットはリアルタイムでユーザー無効化ができないこと
https://auth0.hatenablog.com/entry/2018/09/21/004131
```
理由は、DBにユーザーIDやアクセストークン自体を保存せず、アクセストークンは有効期限が切れるまでは有効だから。  
そのためトークンの有効期限は短く設定する模様

## セキュリティ注意点
### algの改ざん
https://www.wakuwakubank.com/posts/523-it-jwt/
```
対策
利用可能な alg をホワイトリスト形式で制限するなどの対応が必要です。

e.g.) RS256 のみ取り扱うように実装する。
```