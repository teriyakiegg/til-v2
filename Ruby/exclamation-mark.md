# exclamation mark
```
create!、save!　→　レコードの作成・保存に失敗　→　例外を発生させる　
create、save　→　レコードの作成・保存に失敗　→　nilを返す
```
https://qiita.com/ozin/items/5968971c9d2b3ab0a84d

上記はActiveRecordのみの話。以下詳細
```
rubyの場合
注意喚起。今からオブジェクトに対して何らかの変化を加えますよ〜とういう合図。
例：uniq! reverse!

●ActiveRecordの場合
メソッドを実行した結果の返却値がnilの場合に例外を発生させる。
例：save! update!
```
https://qiita.com/mao-0901/items/5d89534d5b7df752807c