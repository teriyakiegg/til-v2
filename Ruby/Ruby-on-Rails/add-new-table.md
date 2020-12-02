# add new table

## rails generate migrationコマンドまとめ
https://qiita.com/zaru/items/cde2c46b6126867a1a64

hogeテーブル追加する時、
```
$ rails g model Hoge name:string description:text
```
下記のファイル差分生まれる。specはテスト周り。migrateはdb更新してくれるやつ
- db/migrate/YYYYMMDDHHMMSS_create_hoges.rb
- app/models/hoges.rb
- spec/factories.rb
- spec/models/hoge_spec.rb

```
サロゲートキー（id）とレコードの作成日時／更新日時のタイムスタンプは自動で作られる。
```

## 外部キーに指定してるカラムにunique属性持たせたい
例
```
t.references :user, index: { unique: true }, foreign_key: true, null: false
```
https://www.techbox.jp/entry/rails-unique-references

## NOT NULLにしたい
null: false をmigrateファイルに追加

## 反映
```
$ rake db:migrate
```
上記コマンド実行で db/schema.rb に差分生成&DBに反映

## 確認
```
$ rake db:migrate:status
```

## 諸々やり直したい時
### 開発中に rails generate や db:migrate をやり直したい時
https://qiita.com/histori/items/7b76aaaa69f2e3ab4f06

```
$ rails generate model Foo hage
「また、やっちゃった！」
$ rails destroy model Foo
「ふ～、助かった」
（モデル名以外の引数は不要）

$ rake db:migrate
「うぎゃー」
$ rake db:rollback
「ふ～」
```