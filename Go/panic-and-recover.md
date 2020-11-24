# panic and recover

『panicはともかくrecoverに使いどころはほとんどない』  
https://qiita.com/ruiu/items/ff98ded599d97cf6646e#2-2

panicを使うべきか、errorを戻り値として返すか、どっちが良いかは大体errorを戻り値として返すで良さげ

```
Don't Panic
See https://golang.org/doc/effective_go.html#errors.
Don't use panic for normal error handling. Use error and multiple return values.
```
https://github.com/golang/go/wiki/CodeReviewComments#dont-panic


```
panicを使わない
Go言語開発者にとってはもはや当たり前ですが、Goに例外はないと考えたほうが良いでしょう。

panicという組み込みの関数はありますが、これは例外というよりも、本当に致命的な問題で終了するときに使われるもので、基本的には使いません。

その代わり、関数から値を返す際に、その末尾に組み込みのerror型を返し、それをnilと比較してエラー処理を行うことが基本の形となっています。

result, err := doSomething()
if err != nil {
    // エラー処理
}
if err != nil {の頻出は、他言語開発者がGoのアレルギーを起こしてしまいやすいポイントでもあります。

ただ、これもまた慣れの問題だと思うようになりました。このコードの流れの方が、エラーチェックを行っていることが明らかで、例外のキャッチ漏れなどを気にする必要がないという利点があるように感じています。

```
https://employment.en-japan.com/engineerhub/entry/2018/06/19/110000
