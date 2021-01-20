# metabase
SQL無しでもデータの可視化できるのでは、のやつ

## セットアップ
https://www.metabase.com/start/oss/

Docker Imageとjarがある。

Dockerまず試してみる

docker run -d -p 3000:3000 --name metabase metabase/metabase

```
Docker Image
Metabase provides an official Docker image via Dockerhub that can be used for deployments on any system that is running Docker. Here’s a one-liner that will start a container running Metabase.
```

```
Launching Metabase on a new container
Here’s a quick one-liner to get you off the ground (please note, we recommend further configuration for production deployments below):

docker run -d -p 3000:3000 --name metabase metabase/metabase
This will launch a Metabase server on port 3000 by default. You can use docker logs -f metabase to follow the rest of the initialization progress. Once the Metabase startup completes you can access the app at localhost:3000

Since Docker containers have their own ports and we just map them to the system ports as needed it’s easy to move Metabase onto a different system port if you wish. For example running Metabase on port 12345:

docker run -d -p 12345:3000 --name metabase metabase/metabase
```

localhost:12345 でセットアップ画面アクセス出来る。  
MySQL、BigQueryとかメジャーなデータセットは扱える

## GCEでMetabaseを構築する
https://jonathan-holloway.medium.com/deploying-metabase-on-google-cloud-platform-gcp-95a8010f9a93  
基本はこれ通りに従って作業で、ファイアウォールをやればIP直打ちでアクセス出来るようになる

こっから必要に応じて、静的IPの適用、ドメイン設定、https設定する感じの流れのはず

## portについて
docker runする場合、-p 3000:3000を12345:3000とすることで、ホスト側のportを変えることが可能。  
3000:12345のように、コンテナ内の3000を変える場合は、  
-e MB_JETTY_PORT=12345 のように、環境変数を渡してあげれば変更可能