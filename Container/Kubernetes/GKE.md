# GKE
## クラスタのアーキテクチャ
この公式のドキュメントはざっくり分かりやすかった  
https://cloud.google.com/kubernetes-engine/docs/concepts/cluster-architecture?_ga=2.91577298.-915982471.1598934677

## リージョンクラスタ
リージョン内で複数ゾーンを設定してマスタとノードを複製することで可用性を高めてる模様  
https://cloud.google.com/kubernetes-engine/docs/concepts/regional-clusters?hl=ja

## Node上へのPodのスケジューリング
podをどのNodeに指定するかは、スケジューラーが勝手にうまくやってくれる。  
自分で指定したいときは指定することも可能  
https://kubernetes.io/ja/docs/concepts/configuration/assign-pod-node/

割り振りの際はresource requestとかも参照する↓  
https://ccvanishing.hateblo.jp/entry/2018/10/02/203205

## GKEクラスタを kubectl で扱えるよう登録する方法
https://qiita.com/oguogura/items/c4f73dbcf0c73e25ec9a

## kubectl で Namespace を切り替える
namespace合ってないと動かぬ  
https://qiita.com/nirasan/items/9dcc7e45cf20fb72bf8a