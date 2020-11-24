# mysql
『Docker で MySQL 起動時にデータの初期化を行う』  
https://qiita.com/moaikids/items/f7c0db2c98425094ef10

docker-compose.ymlにて、 `/docker-entrypoint-initdb.d` ここに起動時に実行したいsqlファイルのあるディレクトリをvolumeとしてあれしておくと、いける

## mysqlへのログインアカウント設定
『DockerのMySQLイメージ起動時に渡す環境変数』  
https://qiita.com/nanakenashi/items/180941699dc7ba9d0922

## コンテナやイメージを削除してもDBのレコードが残ったまま
docker-compose.ymlにて、  
データの保持をコンテナではなくホストで持つようにマウント設定していたらそうなる  
消したかったらホストの方のデータを削除すれば良し  
例) この場合はホストのdocker/mysql/dataを消す
```
mysql:
  volumes:
    - ./docker/mysql/data:/var/lib/mysql
```
