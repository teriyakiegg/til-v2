# components import
```
1. component を作る
2. それを使用するコンポーネントで読み込む (import 変数名 from "場所")
3. 読み込んだコンポーネントを使用する設定を書く export default { components: { Name } }
4. 上記設定をした上で、<Name /> を template 内に記述する (<name />でもok)
```
https://uncle-javascript.com/vue-component

## 親から子に変数を渡す時

```
親
子のコンポーネントを読み込みテンプレートで配置
message="渡したいデータを代入"
parent.vue
<template>
    <div>
        <child message="Hello Vue!!"></child>
    </div>
</template>
<script>
import Child from './child.vue';
export default {
    components: {
        Child
    }
}
</script>
子
propsに「message」を設定
child.vue
<template>
    <div>
        <p>{{ message }}</p>
    </div>
</template>
<script>
export default {
    props: ['message']
}
</script>
```
https://qiita.com/y_sasaki/items/5bbed5439fcfef9f8c40
