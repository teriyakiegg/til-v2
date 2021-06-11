# rubocop
## compatibility
https://docs.rubocop.org/rubocop/compatibility.html

最新のversionではrubyの2.4はサポートしていない。  
2.4をターゲットにできる最後のversionは1.12

## vscodeで使う
rubyの拡張と、globalのgemにrubocop入れとくのは必要  
あとはsetting.jsonで以下追加すればOK
```
"ruby.lint": {
    "rubocop": true
},
```