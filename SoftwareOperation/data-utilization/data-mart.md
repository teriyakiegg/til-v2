# data mart
## GitHubで管理されたデータマート構築基盤の紹介
https://techblog.zozo.com/entry/datamart_on_github

Data martにBigQueryを利用する際の方法が参考になった

大体のデータをDWHのBigQueryに集約はしても、  
BI toolの方でガッツリSQL書きまくっちゃうパターンが多い。  
できればBI toolではSQLあんま書かないようにしたい気がしている。  
アドホックなやつなら良いが、定期的に使うやつに関しては、BigQueryの中でデータマートととして取り出しやすい形にするのが良さそう

## 実体験
一回のクエリに1GB食うやつを10何個もダッシュボード置いていて、  
さらに何度も開く機会があると、  
キャッシュを設定していたとしてもじわりと料金かさむし、  
気楽にダッシュボード開く気持ちが無くなる。  
BigQueryにdata_martという、データマート用のデータセット作って、  
単発のやつはそこにクエリ結果をテーブルとして保存しておくと、  
BIツール側からも呼び出しが無茶苦茶早くなるし、料金も全く気にならなくなった。  
さらに、BIツール側でSQL書かなくて良いので本来の使い方っぽい気持ちになる。  
最新の情報が欲しいやつは、日次でスケジュールされたクエリを使って更新すれば良さそう。