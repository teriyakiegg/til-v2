# slice
『全然わからない。俺たちは雰囲気でSliceを使っている』  
https://note.crohaco.net/2019/golang-slice/

- 配列  
関数に配列を渡す場合には値を丸ごと渡す事になるので、メモリ的に非効率になる。
- スライス  
スライスは配列への参照なので、値を変更すると元の配列も値が変更される。関数に渡す時も値渡しではなく参照渡しになる

lengthとcapacityについてはこれが分かりやすかった  
『Go slice ベストプラクティス』  
https://qiita.com/imoty/items/bb18fb50d526474d2d10


```
When declaring an empty slice, prefer

var t []string
over

t := []string{}
```
https://github.com/golang/go/wiki/CodeReviewComments#declaring-empty-slices

## sliceの中身を全消ししたい時
nil代入で良さげ

## 関数の引数に渡した時の挙動
スライスは参照型だから呼び出し先の関数内でスライスの中身を変更すると、呼び出し元のスライスも中身変わるのはok  
若干ハマったのは、呼び出し先でスライスにnil代入しても呼び出し元の方に反映されなかったこと  
これはスライスの中身は参照が同じだが、スライス自体(ポインター)は値渡しされているためだった。味わい深い  
https://christina04.hatenablog.com/entry/2017/09/26/190000
