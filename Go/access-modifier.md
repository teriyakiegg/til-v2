# access modifier
アクセス修飾子は、無い。  
その代わり変数名、関数名が、  
lowerCamelCase で private、  
UpperCamelCase で public  
importして呼び出せるか呼び出せないか

例えば、main関数内で自作構造体を別パッケージの関数に渡す時、  
構造体のフィールドはpublicにしておかないと、別パッケージの関数内から構造体のフィールドにはアクセスできないの教訓。  
クラスのprivate変数にアクセスできない別言語のノリと思うとそりゃそうだという感じ
