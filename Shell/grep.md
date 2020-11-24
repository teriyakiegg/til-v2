# grep
コマンドラインから検索する時も便利だけど、  
shellスクリプトで使ってもだいぶ便利

hoge.goファイル内にportが3306と記載されてたら3307に書き換える例
```
if [ $(grep 3306 ~/hoge.go | wc -l) -ne 0 ]; then
  $(sed -i "" s/3306/3307/ ~/hoge.go)
  echo "hoge db port has been changed to 3307"
fi
```
