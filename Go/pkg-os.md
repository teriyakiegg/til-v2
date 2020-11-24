# pkg os
ファイルの読み込み、書き込み以外にも、osという名前通りosレベルの処理を色々できる  
https://golang.org/pkg/os/

ちなみに↓らしい  
『goのos.Openは~を見てくれないっぽい。』  
https://pod.hatenablog.com/entry/2017/06/01/090410

## 環境変数取得
```
hoge, ok := os.LookupEnv(HOGE_ENV)
if !ok {
  log.Fatal("HOGE_ENV is required")
}
```