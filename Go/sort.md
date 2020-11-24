# sort
普通の型とかだったら  
sort.Strings()  
sort.Ints()　ってな感じでいける  

https://golang.org/pkg/sort/

構造体のソートの場合はsort.Slice()を使う。  
複数条件でソートする時は以下の感じでいける
```
sort.Slice(structList, func(i, j int) bool {
  if structList[i].hoge == structList[j].hoge {
    return structList[i].fuga < structList[j].fuga
  }
  return structList[i].hoge < structList[j].hoge
})
```
