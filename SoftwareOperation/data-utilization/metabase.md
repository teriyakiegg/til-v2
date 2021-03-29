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
ただ、これだとhttps化とかが面倒

## portについて
docker runする場合、-p 3000:3000を12345:3000とすることで、ホスト側のportを変えることが可能。  
3000:12345のように、コンテナ内の3000を変える場合は、  
-e MB_JETTY_PORT=12345 のように、環境変数を渡してあげれば変更可能

## 構築についてまとめ
基本はやっぱり公式ドキュメントに沿うのが良い。  
公式だとAWS、Heroku、Debianでの構築がドキュメントある。  
Debianでの構築はプラットフォームどこであれ使えるので助かる。  
https://www.codeflow.site/ja/article/how-to-install-java-with-apt-on-debian-10  
https://www.cloudbooklet.com/install-metabase-on-ubuntu-18-04-with-nginx-and-ssl-google-cloud/  
これとかが構築時役に立った。

## 複数データソースの結合
Redashでは可能な複数データソースの結合、Metabaseだと現状出来ない模様。ユーザーからの要望は多そうでGitHubのissueにもリクエストは上がってはいる  
https://www.metabase.com/docs/latest/faq/using-metabase/how-do-i-answer-questions-when-data-is-in-multiple-databases.html

BigQueryとCloud SQLとかだったら、  
BigQueryからCloud SQL連携できる。  
その際はBigQueryをDatabaseとして追加した際に使ったサービスアカウントの権限に「BigQuery Connection User」が必要

## BigQueryのネストされたフィールド
SQL書かないと操作できない  
データマート使えということかも

## スプレッドシートデータ連携
http://beniyama.hatenablog.jp/entry/2019/02/18/080000  
big queryとスプレッドシートが連携できるので、経由で連携は可能  

https://github.com/metabase/metabase/issues/13001

ただここのissueにもある通り、普通には繋げずなので、

BigQueryで定期的に(スケジュールされたクエリを新規作成で)Spreadsheetをクエリした結果を新たなテーブルに上書きして、  
そのテーブルをMetabaseから読み込むすればなんとか今もいける。根本対応が入るまではこれになりそう

## 閾値によるハイライト
良い機能

## データに対するグラフ自動生成
勝手に良い感じでグラフを生成してくれる。気楽でとても良い。が、今の所あんま実用的でない感

## SQL内での変数使用
SQL内なのでSQL使用必須

## SQL使用せずとも
フィルター(WHERE)、サマライズ(GROUP BY)、ジョインデータ(JOIN)、ソート、リミットがぽちぽちで出来る。これだけで強い。

## Slack連携
アラートも自動投稿も可能。  
ただし投稿するグラフは表示できないものもある。  
その場合ただの表が表示される。

metabotでグラフ表示させようとすると日本語は文字化け。metabot結構貧弱

## Timezone設定
Metabaseのreportのtimezoneは管理画面から変更できるが、  
Metabaseのシステムのtimezoneの変更は管理画面から出来ないので、  
起動時のjavaコマンドの引数に -Duser.timezone=Asia/Tokyo を追加して変更が必要。

## SQLのフォーマッティング
Redashにはあるが、Metabaseには無い。しょうがなし  
BigQuery上で出来るので、そっちでやっとくべし

## metricsとsegments
- metrics: ユーザー定義の集計
- segments: ユーザー定義のフィルター

あんま使うことなさそう。フィルターにSQL書けないし

## BigQueryとの連携
連携用のサービスアカウントには以下の権限があれば動く。(冗長な権限もあるかも)
```
BigQuery データ閲覧者
BigQuery ジョブユーザー
BigQuery メタデータ閲覧者
BigQuery リソース閲覧者
```
あとは以下の権限あれば、Cloud SQLとの連携クエリも使えるようになる
```
BigQuery Connection User
```
サービスアカウントの権限を付与するための権限は必要なので、  
自分に権限が無かったらresourcemanager.projects.setIamPolicyの権限を付与してもらう必要あり。  
「Resource Manager ＞ Project IAM 管理者」ロールでOK

## レコード限界値
表もグラフも2,000が限界。それを超えるレコードに関しては表示できない  
ダウンロードでは1,000,000が限界

## 型について
BigQueryのSQLでFORMAT_STRING()とかしてると、中身は日付形式でもstring型と認識されて、  
Metabaseで使える強力な日付型でのgroupingとかができなくなるので注意

## Collection
グラフやダッシュボードをゴリゴリ作っていくと、  
次第に一覧がカオスになってくるので、Collectionを使って整理するのが良さげ

## datetimeのdayofhourでgroup
折れ線グラフにした時、詳細を見ようとポイントにカーソルを合わせると表示がおかしいのであんま使いたくない

## datetimeのdayofhourでgroup
syntax error...  
バージョンアップデートを試してみる

## date型でダウンロード
時間も出力される...

## キャッシュ
平均のクエリ実行時間が閾値以上のクエリの結果に関してはキャッシュすることがキャッシュ設定画面から可能。  
どのくらいキャッシュを維持するか、クエリ毎のキャッシュサイズとかも設定可能

## カラムへのMultiply by a number
見せかけの表示を変えるだけで実際のグラフへは影響が無い

## データ参照元の変更
クエスチョン編集画面のeditorを表示して、Dataのところをクリックすれば楽に変えれる。  
ただし、summarizeなどの情報は消える。悲しいが仕方なし