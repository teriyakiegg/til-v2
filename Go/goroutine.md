# goroutine
最大並列処理数を管理するsemaphore的なチャネルを使って都度都度、goroutineを生んで殺して生んで殺してをforでやるより、  
最大並列処理数分の無限ループするgoroutineを最初に生み出して、  
mainのgoroutineからforでチャネルを通して必要データ送信する実装の方が、  
都度goroutine生み出さないから効率が良さげ。  
例)
```
package main

import (
	"fmt"
	"sync"
)

func main() {
	loop := func(n int, ch <-chan int, wg *sync.WaitGroup) {
		for e := range ch {

			fmt.Printf("goroutine(%d): %v\n", n, e)
			wg.Done()
		}
	}
	ch := make(chan int)
	defer close(ch)
	wg := &sync.WaitGroup{}
	for i := 0; i < 4; i++ {
		go loop(i, ch, wg)
	}
	for i := 0; i < 1000; i++ {
		wg.Add(1)
		ch <- i
	}

	wg.Wait()
}

```

## errgroup
上の書き方でやるとerrgroupはうまく使えなさそう  
逆にgoroutineを何個もボコボコ生み出すやつならerrgroupを使えば楽にwaitgroup + エラーハンドリングが出来そう

## slice
goroutineで同一のsliceをappendする時とか、mutex使わないと変な挙動になるっぽいので辛さがありそう。mapも同じ  
『Go言語 | goroutine で slice を安全に扱う』  
https://qiita.com/YumaInaura/items/24aeac6dbb80b74f8410  
同一のslice云々ならchannel使うのが良さそう

そもそも
```
共有メモリを使った通信は行わず、代わりに通信を使うことでメモリを共有するようにしてください。
Communicating by sharing memory.  ではなく
Share memory by communicating  が推奨

この手法は、過剰となる側面もあります。参照カウンタであれば、たとえば整数型の変数とミューテックスを併用するほうが最適かもしれません。
しかし、高水準な手法として、アクセス制御のためにチャネルを使うことは、明解で正確なプログラムを記述することをより容易くします。
```
という思想の模様。そのためにchannelがおる  
http://golang.jp/effective_go#sharing
