# context
```
ContextパッケージはGolangに標準で組み込まれているパッケージで、
このパッケージに含まれるContextなる型はプロセスをまたいで
デッドラインやキャンセルシグナルを伝達することができる機能群を提供している。
オライリーから出版されている「GO言語による並行処理」を参考にこれらを簡潔に説明するのならば、
Context型は並行処理内でアクションの通知以外にもキャンセルした理由やデッドラインの有無などという状態を付加するために使用される。
```
https://rabbitfoot141.hatenablog.com/entry/2019/05/28/021928

```
Do not store Contexts inside a struct type; instead, pass a Context explicitly to each function that needs it.
The Context should be the first parameter, typically named ctx:

(google翻訳) コンテキストを構造体の型の中に格納しないでください。
代わりに、コンテキストを必要とする各関数に明示的に渡します。
コンテキストは、最初にctxという名前の最初のパラメータにする必要があります。
```
https://qiita.com/convto/items/0f9e844a1775b80cdbd9
