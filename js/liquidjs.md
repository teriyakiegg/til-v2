# liquidjs

## filter

### default
https://liquidjs.com/filters/default.html

なぜか引数に配列を渡せるようになってるが、実態は一番目の引数の値しか使われない  
他のfilterの作りと合わせてそうなってるんだと推察

## render
関数でSyncありと無しの違いは、無しだとPromiseのオブジェクトが返るのに対して、  
ありだとPromiseの結果を同期的に待って結果を返す、っぽい