# scope name
## Railsモデルのメソッドの命名について
https://qiita.com/qpSHiNqp/items/7bcb0492c777a488ceba#%E3%82%B9%E3%82%B3%E3%83%BC%E3%83%97%E5%90%8D

```
形容詞または形容詞句であるべき。
スコープ名がモデル名を後置修飾する。
「どんな〇〇」の「どんな」の部分をスコープ名にする。
〇〇にはモデル名が入る。

形容詞句で後置修飾するようにスコープを命名しておくと、スコープチェーンしたときにも英文法的に破綻しない。
Book.in_sale.published_by("O'Reilly") ← Book (which is) in sale published by O'Reilly
```