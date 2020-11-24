# default move constructor
危ない  
>クラス側でコピーコンストラクタを独自定義した場合にはムーブコンストラクタの暗黙的な定義（default定義）がされなくなるため注意したい。  
コピーコンストラクタのみが定義されている状態でムーブ処理（A b(std::move(A()));）を行うと、ムーブコンストラクタの代わりにコピーコンストラクタが呼ばれるようになる。  

https://marycore.jp/prog/cpp/move-constructor/
