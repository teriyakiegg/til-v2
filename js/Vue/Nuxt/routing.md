# routing
```
下記のようなファイルの木構造のとき:

pages/
--| user/
-----| index.vue
-----| one.vue
--| index.vue
自動的に以下が生成されます:

router: {
  routes: [
    {
      name: 'index',
      path: '/',
      component: 'pages/index.vue'
    },
    {
      name: 'user',
      path: '/user',
      component: 'pages/user/index.vue'
    },
    {
      name: 'user-one',
      path: '/user/one',
      component: 'pages/user/one.vue'
    }
  ]
}
```
https://ja.nuxtjs.org/guide/routing/

```
ルーティングの設定
vue.jsでも Vue Router パッケージを個別にインストールすることでルーティング機能を追加することができますが、
新たにルーティングを追加するとルーティングに関する情報を設定ファイル(router.js)に追加していく必要があります。

Nuxt.jsではページ用のディレクトリのpagesにコンポーネントファイルを保存するだけでそのファイル名に対応するルーティングを自動で設定してくれます。
ページを追加する度にVue Routerのrouter.jsファイルを更新する必要がありません。
```
https://reffect.co.jp/vue/nuxt-js-first-step

## from
from.pathで遷移元のページ名取得できる  
https://zenn.dev/kokota/articles/486a5eed322bca