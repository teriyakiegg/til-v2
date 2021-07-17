# array
## nilか配列かを区別せず、Array( )で処理してしまう

https://qiita.com/jnchito/items/dedb3b889ab226933ccf#nil%E3%81%8B%E9%85%8D%E5%88%97%E3%81%8B%E3%82%92%E5%8C%BA%E5%88%A5%E3%81%9B%E3%81%9Aarray-%E3%81%A7%E5%87%A6%E7%90%86%E3%81%97%E3%81%A6%E3%81%97%E3%81%BE%E3%81%86

```
基本的に配列だが、nilが渡される場合もある変数を処理する場合、Array()（Kernel#Array）を使うと条件分岐を無くせます。

# usersはnilが渡される場合もあるので分岐する
if users
  users.each{|user| send_direct_mail(user) }
end 
# Array()を使うと、nilの場合は空の配列（[])が、それ以外は元の配列が返されるので分岐が不要 
Array(users).each{|user| send_direct_mail(user) }
```

便利これ

## Array()使うかぼっち演算子使うか
nilかもしれない配列に対してmapやeachする時、どっちを使うか悩んだが、  
よく考えたら配列かnilか以外の型のことも考慮すると挙動が分かれる  
Array()は大体どんな型が来てもその型のオブジェクトを含んだ配列を返すのに対して、  
ぼっち演算子はnilかどうかを判定してるだけ。例えばstringが来た場合eachはno method errorになる  
という点を見て使い分ければ良さそう。  
あとは、nilか配列かでしか可能性が無いのなら、Arrayは to_ary と to_a をするのに対してぼっち演算子はnil判定するだけのように見えるからぼっちの方が速そうなイメージはある