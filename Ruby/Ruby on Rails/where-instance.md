# where instance
```
Class.where(hoge_id: hoge_id)
```
のパターンと、
```
Class.where(hoge: hoge)
```
だと、後者はIN区でもいっちょSELECT走るからidで指定できるならidで指定する方がパフォーマンス良い気がしている