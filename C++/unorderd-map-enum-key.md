# unorderd map enum key
C+11だとstd::hashの特殊化を自分で行う必要あり  
https://qiita.com/taskie/items/479d649ea1b20bacbe03  

と見せかけて、underlying_type<T>::typeを使って、enumの基底型を取得することで定義することは可能    
https://cpprefjp.github.io/reference/type_traits/underlying_type.html  
ただこれだと、厳密にenumの型名を要求される(暗黙的型変換が行われない)場合コンパイルエラーになってしまうので注意  
しかもenum classだとunderlying_typeでもアウツ  
C++17以降ならenum classもkeyに指定できる。C++17以降を崇めるべし
