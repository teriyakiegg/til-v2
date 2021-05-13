# safe navigation operator
https://qiita.com/nashirox/items/0c885edf7d78fd5a83f1#-2

ボッチ演算子と呼ばれてるらしい。
```
# railsだと今までこう書いていた
user.try!(:profile).try!(:sns).try!(:twitter)

# オブジェクトがnilならnilが返る
something_nil&.profile&.sns&.twitter
#=> nil

# nilでないオブジェクトでも存在しないメソッドを呼ぶとNoMethodError
building&.profile&.sns&.twitter
#=> NoMethodError: undefined method `profile?' for "building":Building
```