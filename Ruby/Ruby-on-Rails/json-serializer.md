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
json-api-normalizerとかいうライブラリ使ってる事例も見たが、結局あんま楽になってない。  
JSON:API の仕様に沿ったシリアライズらしい。  
https://qiita.com/natsuokawai/items/fe56d9b665ed1d1c52e8  

作成者のNetflixも今ではGraphQLに移行してるみたいなので、Fast JSON APIのことは金輪際覚えておかなくて良さそう

## ActiveModel::Serializersの痒い所に手が届く使い方
https://qiita.com/rh_taro/items/b09b3ebb68c2566c1ee5

## RailsデフォルトのJSONレンダリングは遅いので注意。Ruby/RailsでJSON生成時に最もパフォーマンスが良い方法を調べてみた。
https://qiita.com/ttiger55/items/d144b8094d61b70955bf