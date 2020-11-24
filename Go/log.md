# log
概要↓  
https://waman.hatenablog.com/entry/2017/09/29/011614

『【Go】log.Fatalは気軽に使わない』  
https://qiita.com/ryokky59/items/19fa212d1898dcb4bcfd  
log.Fatal(err)すると、os.Exit(1)が呼ばれ、プログラムは強制終了する。  
このタイトルにある通り、注意なのは、panicとかと違いos.Exitだとdeferも呼ばれないこと。

```
panicやlog.Fatalはmain関数でのみ利用し、その他の関数はreturn errする

Goのエラーハンドリングですが、よく言われるように、main関数以外でpanicやos.Exit(1)やlog.Fatalを行うのは原則禁止です。
テストがしにくいといったことが理由です。
```
https://future-architect.github.io/articles/20200709/

基本的にmain関数以外でlog.Fatal呼ばない。  
deferが必ず呼ばれるようにしたい箇所なら尚更log.Fatalは呼ばすerrをreturnで返すようにするべし

- logrus  
標準のlogに比べて、ログ出力レベルに割当やjsonフォーマット出力が楽にできる  
https://qiita.com/gold-kou/items/3143ab4622acacd33f8d
