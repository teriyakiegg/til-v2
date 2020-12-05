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