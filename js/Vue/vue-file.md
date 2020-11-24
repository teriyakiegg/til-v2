# vue file
```
Vue ファイルには関連する HTML・JavaScript・CSS を1つのファイルにまとめて書きます。
（外部から読み込むことも可能）

HTML は <template> ブロックに書く
JavaScript は <script> ブロックに書く
CSS は <style> ブロックに書く
HTML・JavaScript・CSS それぞれでファイルを分けることと比較して、以下のような利点があります。

UI コンポーネントごとにコードが分離される
影響範囲を Vue ファイルの中に閉じ込めることができる
保守しやすくなる
```
https://qiita.com/shun91/items/eefe0009462b75301dd1

## 最小単位
1. ファイル内に記述無しが最小単位。  
urlから当該ページに遷移した場合エラーにはならず、共通のコンポーネントだけが表示される感じになるっぽい。(nuxtだけの挙動か確認してない)

2. <template>タグと一つのHTMLタグ
```
<template>
  <div>hoge</div>
</template>
```
HTML用の<template>タグは必ず必要。  
その中の要素は少なくとも一つはHTMLタグが必要っぽい。
