# rubocop
## compatibility
https://docs.rubocop.org/rubocop/compatibility.html

最新のversionではrubyの2.4はサポートしていない。  
2.4をターゲットにできる最後のversionは1.12

## vscodeで使う
rubyの拡張と、globalのgemにrubocop入れとくのは必要 `$ gem install rubocop`  
あとはsetting.jsonで以下追加すればOK
```
"ruby.lint": {
    "rubocop": true
},
```

## DisabledByDefault: true
デフォルトで全部 disable にして、有効にしたいやつだけ Enable にする、という設定  
https://hoshinotsuyoshi.com/post/rubocop_yaml/

## 絶対使っといた方が良い
- 絶対使っといた方が良い