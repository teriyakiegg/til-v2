# metabase share dashboard

## 公式ドキュメント

[Guide to sharing data](https://www.metabase.com/learn/data-diet/analytics/guide-to-sharing-data)

- 読んだ感じ、以下二つの方法が良さそう

## 公開URL発行

- publicにしてもokなダッシュボードとかであればこれが一番楽。
- URL知られると誰でも見れるので、機密情報は控えた方が良し

## 社外用のグループ作成と権限設定

- 顧客毎の機密情報でも以下の手順で共有できそう
    - Metabase上で顧客用のグループ作成
    - 該当グループが閲覧できるダッシュボードの権限設定
    - 該当グループ所属のアカウント作成
    - 顧客へアカウント情報送付、Metabaseにアクセスしてもらう(権限設定したダッシュボードのみ閲覧できる)
        - 権限次第ではグラフの表示変更などの操作も可能にできる