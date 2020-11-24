# type
『[Go] Named typeとType aliasを使い分ける』  
https://budougumi0617.github.io/2020/02/01/go-named-type-and-type-alias/
```
Goには既存の型に新しい名前をつける方法が2つある。

type MyType intと宣言するNamed type
type MyType = intと宣言するType alias
```

```
Tl;DR

Goには型に違う名前をつける方法がある。
Named typeとType alias
Named typeを使うと完全に違う型として扱える
プリミティブな型に異なる型名をつけたり、メソッドを生やすこともできる
Value Object的な型を簡単に作ることができる
Type aliasを使うと異なる名前だが同じ型として扱われる
リファクタリングをするときに使われる
型付けを利用した使い分けをしたいならば向かない
基本的にNamed Typeを使えばよい。
```

構造体とmapにはtype付けて、sliceは付けなくても良いかも、という感触  
sliceはvalueにs付けた名前で、mapもkeyは無視でvalueにs付けた名前で良さげ  
そうするとmapが入れ子になった時に途中のmapの型名に悩むが、それは型名type付けなくて良い気がしてる
