# join merge
https://qiita.com/TeruhisaFukumoto/items/007ad22cc170d297dbcc

こんな感じで書ける
```
Parent.joins(
  child: [
    great_grand_sons: :great_great_grand_son
  ]
).merge(GreatGreatGrandSon.where(id: funfun))
```