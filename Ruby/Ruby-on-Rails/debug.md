# debug
dockerに乗っかってるrailsアプリとかだと、  
標準出力はdockerのlogに出力されるからpとかはdockerの方を見る

## docker + binding.pry
[docker上でbinding.pryを実行する](https://qiita.com/hb5kz/items/7c9d266480079910de5c)

## インスタンス変数確認
(class_name|object).instance_variables

## インスタンス関数確認
class_name.instance_methods(false)  
インスタンス化してると見れないので注意。以下も注意  
```
instance_methodsメソッドに引数を渡さないと出力されるインスタンスメソッドはスーパークラスやインクルードされているモジュールに定義されているインスタンスメソッドをすべて出力してしまいます。

対象となるクラスやモジュールで定義されているインスタンスメソッドだけを出力したい場合には引数にfalseを指定します。
```
https://techacademy.jp/magazine/20211