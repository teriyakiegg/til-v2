# arrow operator
```
ラムダ式で用いるリテラルで、「lambdaリテラル」や「アロー演算子」と呼ばれます。

# 定義
foo = -> (x) { x + x }
# 呼び出し
foo[5]   # => 10
foo.(5)  # => 10
foo.call 5 # => 10

# 通常のlambdaの書き方   
bar = lambda { |x| x + x }
bar.call 5 # => 10
Railsだとモデルのスコープで使われたりしていますね。

app/modes/comment.rb
class Comment < ActiveRecord::Base
  scope :created_before, ->(date) { where("created_at < ?", date) }
end

```
https://qiita.com/nashirox/items/0c885edf7d78fd5a83f1#-