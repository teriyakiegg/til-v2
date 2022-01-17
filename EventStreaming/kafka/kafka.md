# kafka
## 概要動画
https://youtu.be/FJZeaY3n5CY

- Producer(データ生成側)
- Broker(複数台配置するkafkaのサーバー)
- Consumer(データ活用側)

- Topic(データの種類)
- Partition(分散に用いる区画)
- Replica
  - Leader Replica(ProducerとConsumerとやり取りする)
  - Follower Replica(複数のBrokerに配置され、Leader Replicaからレプリケーションされる。またLeaderが死んだら自身がLeaderになる)

## 概要動画続き
https://youtu.be/38LUK4hl3so

### オートスケール
今は存在してないっぽい。  
単にサーバーを追加するだけでなく、各BrokerへのReplicaの割り当て設定をしないといけない

### kadkaの速さの特徴と安全性
受け取ったデータを毎度ディスクに書き込まず、メモリに置いた時点で受信したとする(受信側へackする)ことで、ディスクへの書き込みが無い分速度を出している  
ただそれだけだとackした後該当brokerが故障したらデータロストするので、  
Leader Replicaで受信、Followerへレプリケーション(これもメモリに置くだけ)が完了した時点でackする、という順序にしてるおかげで、  
Leaderが死んでもFollowerの方にデータ残ってるよね、データロストしないよね、になっている  
Followerが少ないとデータロストの可能性が高まるので、一定数以上のFollowerがいないと受信ができないようになってるらしい  
ディスクへの書き込みは一定量溜まったら(or一定時間経過)行われる

# キューとの違い
キューはconsumeした時点でconsume元からデータを削除するのに対し、  
kafkaではconsumeしてもconsume元のデータは削除されない。  
そのため、他のシステムが同じトピックを参照したり、過去にさかのぼってデータを処理、リトライなどが可能  
その分、どこまでconsumeしたかを記録する必要があり、offsetなどの概念が出てくる
