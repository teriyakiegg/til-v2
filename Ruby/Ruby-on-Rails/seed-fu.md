# seed-fu
『railsで初期データを入れる(seed-fuの使い方)』  
https://qiita.com/ko2ic/items/be96e450a33d631e0059

```
$ mkdir db/fixtures
$ mkdir db/fixtures/development
$ mkdir db/fixtures/production
```
ここに環境ごとにseedファイルをぼんぼこ作って`$ bundle exec rake db:seed_fu`で初期データ投入できる
