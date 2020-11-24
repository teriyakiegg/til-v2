# map
作成にはmake()を使う。(使わないで{}でもいける書き方もある。実質的にリテラル? 生成してるというのを明示する意味でmakeの方使うで良さそう)  
生成と同時にキーと要素のペアを格納するリテラルというのもある。その場合make要らない。

『Go言語: いろいろなマップの作り方まとめ』  
https://qiita.com/suin/items/7225ab9f2aeb6f55c606

C++でいうところの、unordered_map。ordered_mapは標準ライブラリには無さげ  
ソートしたい時は別途リストを用意して頑張るしかない  
https://stackoverflow.com/questions/23330781/sort-go-map-values-by-keys

time.Time型をkeyにするのは無理

mapを入れ子にする時、  
こんな感じで初期化必要(== nilでも判定できるが、mapの値にはnilを代入できる作りになってるらしいので、okで判定するのが堅い)
```
if _, ok := hogeMap[5]; !ok {
        hogeMap[5] = make(map[int]string)
}
```

mapを入れ子にしないで、構造体をmapのkeyにすることもできる。目から鱗。  
https://qiita.com/ruiu/items/476f65e7cec07fd3d4d7

map4階層とかはさすがに辛い。valueに構造体使って回避もできるので覚えとくと良し
