# instance variables
@が変数名の頭につく

https://qiita.com/mogulla3/items/cd4d6e188c34c6819709

```
インスタンスごとに独立して持つ変数。

インスタンス変数にアクセスできるのは、initializeメソッドとオブジェクトのインスタンスメソッドだけ
initializeメソッドで初期化されて、その後各インスタンスメソッドから参照・変更される使い方が多い（と思う）
PHPやJavaみたいに事前にクラス定義内で定義する必要がない⇦ここ注目
```


## RailsのActiveRecordで
@でアクセスとか出来ないので勘違い注意
```
self.nameとした場合、attr_accessorで作成されたメソッドを呼び出します（ローカルに同じnameがない場合かつ代入でない場合は、nameとだけ書いても同じ動作となります）。self.name = ''のような代入メソッドを呼びたい場合はselfが必須です（selfなしだとローカル変数を作るものとみなされます）。

@nameとした場合は、attr_accessorが裏で保管しているインスタンス変数を読みに行きます。

attr_accessorの場合はどちらも同じですが、アクセサがなくインスタンス変数しかない場合、@nameでのアクセスしかできません。逆に、RailsのActiveRecordでは、@nameのような変数に格納しているわけではないので、nameというメソッド形式のアクセスが必要となります。
```
https://teratail.com/questions/202474