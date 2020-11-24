# rest client
便利。Postman消した。  
『VS Code上でHTTPリクエストを送信し、VS Code上でレスポンスを確認できる「REST Client」拡張の紹介』  
https://qiita.com/toshi0607/items/c4440d3fbfa72eac840c

拡張子は.restか.httpで
```
POST http://hoge.com/api/hoge HTTP/1.1
Content-Type: application/json

{
  "email": "hoge@example.com",
  "password": "hoge"
}
```
こんな感じのをファイル内に書いて、VSCode画面左上の「Send Request」ポチるか、cmd + option + r でリクエスト送れる。  
レスポンスは右側に自動で表示される。  
テキストだから保存して使いまわせるし神。

## 区切り
`###` これ書いとけば同一ファイル内に複数のリクエスト書いておける。コメントも書ける

例:
```
### アクセストークン取得

POST http://hoge.com/api/hoge HTTP/1.1
Content-Type: application/json

{
  "email": "hoge@example.com",
  "password": "hoge"
}

### ほげ一覧情報取得
http://hoge.com/api/hoge
Authorization: Bearer hogehogehoge

```
