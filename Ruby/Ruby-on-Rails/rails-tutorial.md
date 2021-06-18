# rails tutorial
- railsについて体系的に学んで来なかったので、試しにrails tutorialやってみる
- versionは6.0
- https://railstutorial.jp/chapters/beginning?version=6.0

## 第1章
- 言われるがままにCloud9使ってみる。久々にAWS Console開いた
>Rubyの世界では、インデントに2つのスペースを使うのがほぼ常識になっている
- らしい
- 0→1の瞬間はとりあえずrails new hoge。rails serverで楽ちんローカル起動
- ルーティングとコントローラー設定
- Git使ったことない初学者はGit周りで挫折しそうな印象
- git checkout -fのfフラグは知らなかった
- GitHubは2段階認証設定してるので、personal access token作ってhttpsでCloud9からpushした
- Rails 6以降ではrails newコマンドでGitリポジトリ作成されるからgit init必要ない模様

## 第2章
- $ git push && git push heroku master これスマート
- $ rails generate scaffold Hoge カラム で大体必要なのゴリっと自動生成される
  - Scaffold機能でコードを自動生成すると、Webのあらゆる部分からモデルデータにアクセスしてやりとりできるようになる
- 欠点: データの検証が行われていない,ユーザー認証が行われていない,テストが書かれていない,レイアウトやスタイルが整っていない
- $ heroku run rails db:migrate 忘れず
- 1章、2章で作ったプロジェクトはCloud9からもGitHubからもHerokuからも消しておく

## 第3章
- $ rails generate controller StaticPages home help でactionも指定してコントローラー作れる
```
完全なコマンド	短縮形
$ rails server	$ rails s
$ rails console	$ rails c
$ rails generate	$ rails g
$ rails destroy	$ rails d
$ rails test	$ rails t
$ bundle install	$ bundle
```
- gミスった時はdで戻せる
- db:migrateミスったらdb:rollbackは知ってたが、db:migrate VERSION=0で最初の状態に、0を変えれば指定のバージョンまで戻れる、のは知らなかった
- herokuにmasterブランチ以外のブランチpushしても本番反映されないのうっかりしがち
- テスト駆動開発、好き

## 第4章
- Ctrl-Pが上矢印キーと同じ挙動をするの初めて知った
- putsはputの三人称単数現在形ではなく「put string」の略、というの初めて知った
- printと違ってputsは最後に改行入る
- 「!!」（「バンバン（bang bang）」と読みます）
- 配列の最初の要素のインデックスが0から始まることをゼロインデックスと呼ぶらしい。
- 破壊的メソッドにするにはメソッドの末尾に「!」を追加
- Rubyでは異なる型が配列の中で共存できる
- ブロックは波かっこかdo endで囲う
- Rubyにおける慣習として、ハッシュの最初と最後は空白を追加する模様
- メソッド呼び出しの丸カッコは省略可能。
- 最後の引数がハッシュの場合、波カッコは省略可能。
- s = String.new("foobar")とs = "foobar"は同等
- a = Array.new([1, 3, 2])とa = [1, 3, 2]は同等
- ハッシュは特殊でHash.new はハッシュのデフォルト 値を引数に取ります。これは、キーが存在しない場合のデフォルト値
- superclassメソッドを使うとクラス階層が分かる
- Railsでは、インスタンス変数をコントローラ内で宣言するだけでビューで使えるようになる

## 第5章

## 第6章

## 第7章

## 第8章

## 第9章

## 第10章

## 第11章

## 第12章

## 第13章

## 第14章
