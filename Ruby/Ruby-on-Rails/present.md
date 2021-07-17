# present
## 存在の有無を確認する場合はblank?/present?を積極的に使う
https://qiita.com/jnchito/items/dedb3b889ab226933ccf#%E5%AD%98%E5%9C%A8%E3%81%AE%E6%9C%89%E7%84%A1%E3%82%92%E7%A2%BA%E8%AA%8D%E3%81%99%E3%82%8B%E5%A0%B4%E5%90%88%E3%81%AFblankpresent%E3%82%92%E7%A9%8D%E6%A5%B5%E7%9A%84%E3%81%AB%E4%BD%BF%E3%81%86
```
Rubyの標準APIではnil?やempty?のように「無い」を表すメソッドしかないので、「もしあるなら」をコードで表現するとぎこちなくなります。

Railsであれば、present?を使って「もしあれば」を明示的に書くことができます。
```

```
if user
  # userがいれば、何かを実行する
  # =>「もしuserがいれば」ではなく「もしuserなら」と読めてしまう
end

unless users.empty?
  # usersが空ではないなら、何かを実行する
  # => empty?の逆がないので、否定形で条件を書かざるを得ない
end
```

```
if user.present?
  # userがいれば、何かを実行する
  # =>「もしuserがいれば」と明示的に読める
end

if users.present?
  # usersに1つ以上の要素があれば、何かを実行する
  # => 肯定形で条件が書ける
end
```

## とは言え脳死でpresent使わない
https://moneyforward.com/engineers_blog/2019/03/15/ruby-code-4/

文章として読めるメリットは感じるが、  
無駄は省くべしで記述量少なくなるメリットも同等に感じる。  
present?を使う必要がある、例えば空の文字列(空オブジェクト)をtrueにしたくない場合とかのみ使えば良さそうに思う