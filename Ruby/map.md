# map
## 配列を順番に処理するとき、"object.method"の代わりに"&:method"を使う
https://qiita.com/jnchito/items/dedb3b889ab226933ccf#%E9%85%8D%E5%88%97%E3%82%92%E9%A0%86%E7%95%AA%E3%81%AB%E5%87%A6%E7%90%86%E3%81%99%E3%82%8B%E3%81%A8%E3%81%8Dobjectmethod%E3%81%AE%E4%BB%A3%E3%82%8F%E3%82%8A%E3%81%ABmethod%E3%82%92%E4%BD%BF%E3%81%86

```
names = users.map{|user| user.name }
names = users.map(&:name)
mapに限らず、eachやselectなどブロックで配列の中身を受け取るようなメソッドは同じように&:methodで処理できます。
```
便利これ