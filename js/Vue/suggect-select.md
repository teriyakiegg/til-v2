# suggest select
https://note.com/kawa1228/n/n0f53a7670d1b

入力に対応して候補も表示して選択できる。  
楽に実装できる。

```
appendToBody="true"
```
にすると、ドロップダウンのcssが崩れてへんなとこに出る場合くっつけてくれる

検索条件に該当しない場合に表示される文言は↓でカスタマイズできる  
https://github.com/sagalbot/vue-select/issues/196
```
<vselect>
  <span slot="no-options">Nothing here.</span>
</vselect>
```