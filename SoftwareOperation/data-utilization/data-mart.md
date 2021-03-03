# data mart
## GitHubで管理されたデータマート構築基盤の紹介
https://techblog.zozo.com/entry/datamart_on_github

Data martにBigQueryを利用する際の方法が参考になった

大体のデータをDWHのBigQueryに集約はしても、  
BI toolの方でガッツリSQL書きまくっちゃうパターンが多い。  
できればBI toolではSQLあんま書かないようにしたい気がしている。  
アドホックなやつなら良いが、定期的に使うやつに関しては、BigQueryの中でデータマートととして取り出しやすい形にするのが良さそう