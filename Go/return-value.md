# return value

## 名前付き返り値

Goは返り値の変数を仮引数と同じノリで定義できちゃう。  
ただし、脳死で全部この名前付き返り値で宣言するのはNG

https://github.com/golang/go/wiki/CodeReviewComments#named-result-parameters

同じ型が複数ある場合や、型や関数名だけでは戻り値の正体がわかりにくい時のみ使用した方が良し。  
宣言を省きたいとか裸リターンしたい、という理由だけで名前付き返り値使うのは微妙

## 自明の nil

```
返り値でnilが自明な場合は、変数(errや普通の変数)ではなくnilそのものの固定値を返したほうが、レビュー時の脳内メモリを減らせて助かる
```
https://future-architect.github.io/articles/20200709/
