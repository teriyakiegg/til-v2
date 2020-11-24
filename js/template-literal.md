# template literal
https://chaika.hatenablog.com/entry/2018/10/02/090000

```
JavaScriptで変数を展開した文字列を作成する時、+で文字列連結をしていましたがES2015(ES6)からは``(バッククォート)で囲うテンプレート構文(Template literal)で書くことができるようです。
※ IEやAndroidでは未対応なブラウザもあるようなので、WEBサイト制作とかの場合はまだバベる必要がありそうです。
ブラウザ実装状況: テンプレート文字列 - JavaScript | MDN

テンプレート構文(Template literal)による文字列中での変数展開
var val = "JavaScript"
// 今までのやり方
var str1 = "Hello " + val + "!" // => Hello JavaScript!
// テンプレート構文
var str2 = `Hello ${val}!` // => Hello JavaScript!
文字列中で変数を展開させるプレースホルダーは${...}の形式で記述します。
```