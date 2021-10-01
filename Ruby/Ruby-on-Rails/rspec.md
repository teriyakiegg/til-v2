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
`let` is not available from within an example (e.g. an `it` block) or from constructs that run in the scope of an example (e.g. `before`, `let`, etc). It is only available on an example group (e.g. a `describe` or `context` block).

## letの上書き
https://zenn.dev/yuji_developer/articles/52cc0e356b3748#4.-let-%2F-let!-%E3%81%AE%E4%B8%8A%E6%9B%B8%E3%81%8D%E3%82%92%E3%81%97%E3%81%AA%E3%81%84  
上書きした後のでテストで同じ状態が続くのでハマる原因になりやすいことを実感..................  
と思ったけどそんなことなかった

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

## context
describeで(#|.)関数名 で括って、  
条件分け毎の括りにcontextを使うとスラスラ書けそう  
説明文はwhen, with, withoutを使って表現すると良さげ

## let
は遅延評価される。便利。  
context毎に変わらないものはdescribe直下に直で宣言して、  
context毎に変わるものは変数書いといてcontext毎に代入すると記述量だいぶ減りそう  
let!で遅延無くすことも可能

## shared_context
別の関数で同じ用なcontextを使ってる場合、shared_context書いてinclude_context使うと楽ちんそう

## it, example, specify
全部同じ働き

## shared_examples
異なるcontextでexampleが同じものを多用する場合、shared_examples書いてit_behaves_likeで使い回すのがすっきりしそう

## subject
shared_examplesと違い、異なるcontextで期待する結果は別だがexpectする対象の関数が同じ場合、  
subjectを宣言してis_expectedで書くとスマートになりそう

## privateメソッドへのテスト
原則書かないほうが良い。publicメソッド経由でテストできるはず  
https://highwide.hatenablog.com/entry/2019/03/03/220653

## describeやcontext内での変数の扱い
```
`hoge` is not available on an example group (e.g. a `describe` or `context` block). It is only available from within individual examples (e.g. `it` blocks) or from constructs that run in the scope of an example (e.g. `before`, `let`, etc).
```

## contain_exactly
https://qiita.com/jnchito/items/2e79a1abe7cd8214caa5#%E9%85%8D%E5%88%97--include