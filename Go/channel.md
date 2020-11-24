# channel
- チャネルはキューの性質を備えるデータ構造。FIFO。
- チャネルのバッファ数指定しないとバッファ0で初期化される。受信側がスタンバイしとかないと、送信側はブロック。キューに溜めておけないから。
- チャネルの型宣言では受信専用、送信専用を定義できる
- 複数のチャネルの入出力を扱えるのがselect。片方がブロックされてるせいでもう片方も道連れでブロックを回避できる。defaultなかったら処理はブロックされる
https://www.slideshare.net/mobile/lestrrat/select-66633666
- チャネルをcloseした時は、そのチャネルに型の初期値, falseが送信される(受信側に終了を伝えられる)

- チャネルに対するrange forはチャネルがcloseされるまで無限ループ的に受信し続ける
```
The loop for i := range c receives values from the channel repeatedly until it is closed.
```
https://tour.golang.org/concurrency/4  
↓で実験してるように、range for対象のチャネルがcloseされたら、range forの無限ループは終わる。  
https://medium.com/better-programming/manging-go-channels-with-range-and-close-98f93f6e8c0c

## Go の channel 処理パターン集
よく纏まってる  
https://hori-ryota.com/blog/golang-channel-pattern/
