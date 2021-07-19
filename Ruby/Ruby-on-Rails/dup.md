# dup
```
idはnilになる
新しいレコードになり、new_record?はtrueとなる
保存しないと永続化しない
新規レコードなので保存をするとbefore_save,before_createが呼ばれる
idがnilになるため、idをキーにしたhas_manyのアソシエーションなどは外れる
```
https://www.lanches.co.jp/blog/3327

## initialize_dup
クラス内で定義すれば、そのクラスに対してdupした際の挙動をoverride出来る  
特別に複製するものしないものの定義に便利