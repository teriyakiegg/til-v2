# redash
OSSのデータ可視化ツール。MySQLやBigQueryからも参照できる  
https://seleck.cc/614

さっと調べた感じ、Redashと比較してMetabaseというやつも良さそうな雰囲気。試してみたい

[MetabaseがRedashの苦労を吹き飛ばすくらい熱い - Qiita](https://qiita.com/Ponzmild/items/adc6b8248e1e54e5e1f4)

# Redash活用事例

[re:dashは何が良くて、何が足りないのか - Qiita](https://qiita.com/toyama0919/items/c6c600d8bfd4dcdd69e1)

メリデメがチャチャっと書いてある。

上記の記事を引用するとやることは基本以下になりそう

- SQLを書く
- グラフを作る
- ダッシュボードに組み込む
- スケジュールを組む

他に、アラート機能やQuery Snippetsも活用は出来そう  
地味にFormat機能もある。あとwhereを変更するためのparameter追加も  
Dashboardは複数のQueryの結果を組み合わせて表示できる模様。ナイス  
DashboardではテキストBOXもMarkdownで挿入できるから注意書きとか書ける。  
クエリが増えて見にくくなってきたらタグをつけて見やすく管理できる。

# 試した感じ
SQLの結果が1レコードで、カラム複数みたいなテーブルだとVisualizationうまく活用できなさそう。学び。  
純粋に一つのQueryではGROUP BYして「カウント」、「種類」の2カラムのテーブル出すようにするのが良さげ  
(ただ、上の1レコードから要素毎にGROUP BYできれば活用できそう)

# Slack連携
https://data.gunosy.io/entry/slack-redash-kpi-notify

Slackのプレビュー表示では、一つのグラフしか表示できないので、  
表示するものを何にするかはよく吟味したい。ちなみにDashboardはプレビュー表示されなさそう  
とりあえず、ChannelにRedash追加してRedashのURL貼ればプレビュー表示される

この活用事例が参考になった  
### 【Slack×Re:dash】リアルタイムKPI通知をコード0行で実現する
https://data.gunosy.io/entry/slack-redash-kpi-notify

Slackのremind機能でプレビュー表示も簡単にできる  
```
/remind #channel 何 いつ
```