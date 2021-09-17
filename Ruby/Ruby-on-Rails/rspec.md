# rspec
[Ruby on Rails のテストフレームワーク RSpec 事始め](https://qiita.com/tatsurou313/items/c923338d2e3c07dfd9ee)

[使えるRSpec入門・その1「RSpecの基本的な構文や便利な機能を理解する」](https://qiita.com/jnchito/items/42193d066bd61c740612)

## satisfyマッチャ
配列に対してテストする時良さげだった  
https://qiita.com/ishidamakot/items/a23b86b9f59ab8e4fbb1

## factory_bot
[RailsアプリへのRspecとFactory_botの導入手順](https://qiita.com/Ushinji/items/522ed01c9c14b680222c)

## it
```
it "should return hoge" do

end
```
で書くと良い感じ

## let
インスタンス変数宣言出来る

## まとめ
これが分かりやすかった  
https://qiita.com/ea54595/items/459727ea8c32fed48b50

## seed
https://blog.toshimaru.net/rspec-occasional-fail/

## 特定のexampleだけ実行
もできる。こんな感じ
```
bin/rspec './spec/hoge_spec.rb[1:1:2:1:1]'
```