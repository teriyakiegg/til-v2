# docker-compose
これが分かりやすい  
https://coinbaby8.com/docker-beginner.html  
各コマンド詳細はこれが分かりやすい  
https://qiita.com/wasanx25/items/d47caf37b79e855af95f

これは良し  
alias fig='docker-compose'

## よく使いそうなやつ
- exec コンテナ入る `fig exec container-name /bin/bash`
- logs コンテナのログ見る -fつけると実行中ターミナルでずっとログ監視
- ps コンテナの一覧表示
- restart コンテナ再起動
- run コンテナ指定してそこでコマンド実行 (dockerコマンドの場合はコンテナ名を指定するがdocker-composeではdocker-compose.ymlに記載してるサービス名を指定する)
- up image構築、コンテナ構築、コンテナ起動を一気にやってくれるやつ　-dでデーモン化
- stop
- start
- top 各コンテナのプロセス見れる
- -fオプション `fig -f ~/hoge/hoge/docker-compose.yml up -d` とかで別ディレクトリのやつもコマンド実行できる

## キャッシュに注意
https://qiita.com/tegnike/items/bcdcee0320e11a928d46

一回imageが構築されるとキャッシュされる。  
Dockerfileを変更してもキャッシュがあると変更が反映されないので--no-cacheオプションの指定が必要なの注意

## up
`docker-compose.yml` にて、services: -> 名前: -> command: にコマンド記載すると、コンテナ起動時に実行される
