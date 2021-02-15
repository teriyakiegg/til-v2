# xargs
```
echo a b c d|xargs -I@ コマンド @
```
https://qiita.com/saa/items/a276782eb5e49892b33a

## よく使えそうな例
```
$ seq -w 31 | xargs -IDAY sh -c 'curl -H "Authorization: Bearer XXXXXXXXXXXXXXXX" "https://hoge?day=DAY" > DAY.txt'
```
1から31をDAY変数に渡して、API叩く例