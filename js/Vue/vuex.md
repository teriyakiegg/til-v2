# vuex
https://hafilog.com/nuxt-link-and-atag

## ブラウザのリロード
すると、vuexはリセットされる

## だいぶハマったこと
画面遷移の際に、a hrefの要素で遷移するとブラウザのリロードと同じで、vuexはリセットされる。  
リセットしたくない場合はrouter-link（またはnuxtだったらnuxt-link）で画面遷移するべし。  
初見殺しだった。

## State を直接参照せず、getter 経由で参照することを強く推奨する
https://uncle-javascript.com/vuex-getters