# json serializer
この記事の比較が良さげだった  
『Rails における JSON のシリアライズと向き合う 🦜』  
https://qiita.com/sakuraya/items/924ec3c3001938071407

## 所感
APIからリクエスト元にjson返す時、  
jsonで何を返すかを定義してる、という感覚

## Fast JSON API
速度は早いらしいが、正規化されていて、フロント側でjsonのパースするのが面倒...  
これだけでマイナスポイント高い。  
パース楽にするライブラリもクライアント毎にあるようだがとりあえず日本語記事だいぶ少ない  
JSON:API の仕様に沿ったシリアライズらしい。  
https://qiita.com/natsuokawai/items/fe56d9b665ed1d1c52e8