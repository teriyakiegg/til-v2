# push_back and emplace_back

引数が違う。  
コンテナの要素型を引数として要求するのか、コンテナの要素型のコンストラクタ引数を要求するのか

>emplace系の関数は、要素の生成をコンテナ内部で行うという特徴があります。そのため、emplace系の関数は要素を直接受け取るのではなく、要素型が取りうるコンストラクタ引数の値を受け取るようになっています。

https://marycore.jp/prog/cpp/emplace-functions/

↓はなるほどポイント

>emplace_backは実引数がコンテナの要素型と異なるときに、push_backよりも動作が早くなり、
それ以外の場合ではほとんど変わりません。（実引数が単に変数のときなど）

https://qiita.com/brackss1/items/e92da6458172397f7225
