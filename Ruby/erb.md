# erb
- 今はrailsをAPIサーバーにしてフロントはjsのパターンが主流
- 今後ほぼ触ることは無さそう
- テンプレートエンジンはsmarty、mobasif、xslate等やってたのが懐かしい

## provideとyield
```
<% provide(:title, "Home") %>

<title><%= yield(:title) %> | Ruby on Rails Tutorial Sample App</title>
```