# nohup
コマンドの最後に&つけてバックグラウンド実行しても、ターミナルを閉じると処理終わってしまう。それを避けるにはnohup

普通に
```
$ nohup ./hoge.sh &
```
するとnohup.outが生まれるので、うまれさせたく無かったら
```
nohup ./hoge.sh > /dev/null 2>&1 &
```

https://qiita.com/iNaoya/items/eb1d09ee8e6d2323edd4
