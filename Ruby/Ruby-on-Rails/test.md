# test

## assert_response
- assert_response :success

## assert_select
- assert_select "title", "Home | Ruby on Rails Tutorial Sample App"
- titleタグに2つ目の引数の内容が含まれるか
- セレクタとも呼ぶらしい

## setupメソッド
- 定義すればテスト実行前に呼ばれる

## minitest reporters
- REDやGREENの表示が見やすくなるのでいれとくべし
```
test/test_helper.rb

require "minitest/reporters"
Minitest::Reporters.use!
```