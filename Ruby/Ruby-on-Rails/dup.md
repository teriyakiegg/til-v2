# dup
```
idはnilになる
新しいレコードになり、new_record?はtrueとなる
保存しないと永続化しない
新規レコードなので保存をするとbefore_save,before_createが呼ばれる
idがnilになるため、idをキーにしたhas_manyのアソシエーションなどは外れる
```
https://www.lanches.co.jp/blog/3327