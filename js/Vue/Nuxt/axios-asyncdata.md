# axios asyncdata
だいぶ分かりやすかった  
https://reffect.co.jp/vue/nuxt-js-axios-asyncdata

axiosはプログレスバーの表示を行うことができる模様  
https://reffect.co.jp/vue/nuxt-js-axios-asyncdata#nuxtjsaxios-3
```
nuxtjs/axiosではデフォルト設定のままプログレスバーを表示させることができます。

プログレスバーはページを移動する際に移動先のページが表示されるまで上部に表示されます。
デフォルトでも設定されているのですが、colorが#fff(白)のため背景に隠れて存在を確認することができません。
nuxt.config.jsファイルで色の設定を変更します。
```

```
asyncDataの使用方法
サーバ側で実行される処理asyncDataの使い方を確認していきます。

asyncDataはサーバ側で行う処理なのでコンポーネントのdataプロパティの設定を行うことができます。
```
returnしたやつはdataプロパティとして使える模様
