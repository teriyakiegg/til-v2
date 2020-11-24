# jq
## jq コマンドを使う日常のご紹介
https://qiita.com/takeshinoda@github/items/2dec7a72930ec1f658af

外側から順に取得したい値を指定していくイメージ

```
$ jq '.'
```
これが全てを指定

```
$  jq '.[]'
```
一番外側がリストになってたら[]指定の後に中身の要素指定できる

```
$ jq '.[].timestamp'
$ jq '.[] | .timestamp'
```
パイプを使うことも可能

-r オプションでjq後の出力のダブルクォートを消せる
```
$ jq -r '.[].timestamp'
```