# static local variable
そのクラスのメンバ変数が持つメンバ変数の参照を戻り値に返す関数で、そのクラスのメンバ変数が存在しない場合に返す変数として、静的ローカル変数使えそう。  
staticの宣言の行が呼ばれない限り静的領域にも確保されないようなので、メモリを過度に心配しなくても良さそう。  
https://stackoverflow.com/questions/12186857/on-local-and-global-static-variables-in-c
