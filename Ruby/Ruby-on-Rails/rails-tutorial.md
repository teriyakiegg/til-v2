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

## 第3章

## 第4章

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
