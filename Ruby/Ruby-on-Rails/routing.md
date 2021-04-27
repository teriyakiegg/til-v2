# routing
これが分かりやすかった  
https://qiita.com/Yaruki00/items/d677e0751c90500afc8c

- config/routes.rbでルーティング設定する
- ルーティングされたやつは`app/controllers/`ココに割り振られる
- `$ bundle exec rake routes` でルーティング設定一覧が見れる

## 公式ドキュメント
https://railsdoc.com/routes

リソースベースのルーティングで生成されるURL、アクション、説明を読むと、  
railsのルーティングをどういう使い方して欲しいかという思想が垣間見れる

リソースの詳細表示に対してidを渡す場合、  
クエリパラメータではなくてURLにidを含める。  
クエリパラメータはオプション的なものを渡したい時に使う模様

## Railsガイド
```
HTTP動詞	パス	コントローラ#アクション	目的
GET	/photos	photos#index	すべての写真の一覧を表示
GET	/photos/new	photos#new	写真を1つ作成するためのHTMLフォームを返す
POST	/photos	photos#create	写真を1つ作成する
GET	/photos/:id	photos#show	特定の写真を表示する
GET	/photos/:id/edit	photos#edit	写真編集用のHTMLフォームを1つ返す
PATCH/PUT	/photos/:id	photos#update	特定の写真を更新する
DELETE	/photos/:id	photos#destroy	特定の写真を削除する
```

## Railsのroutingにおけるscope / namespace / module の違い
https://qiita.com/ryosuketter/items/9240d8c2561b5989f049

urlとディレクトリ構造を別のを指定したい場合をやりたくて、  
色々要員重なって結構ハマったが、下記のようにすれば実現できた  
```
scope :hoge do
    scope module: :fuga do

    end
end
```

# memberとcollectionの違い
https://qiita.com/k152744/items/141345e34fc0095217fe