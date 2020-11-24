# resource request limit
## KubernetesのResource RequestsとResource Limitsについて
https://qiita.com/sheepland/items/eb0e4c65aaae70ec4e2f

## メモリ制限を指定しない場合
```
コンテナのメモリー使用量に上限がない状態となります。コンテナは実行中のノードで利用可能なすべてのメモリーを使用でき、
その後OOM Killerが呼び出される可能性があります。さらに、OOM killの場合、リソース制限のないコンテナは強制終了される可能性が高くなります。
```
https://kubernetes.io/ja/docs/tasks/configure-pod-container/assign-memory-resource/

## vertical pod autoscaler
resource request設定しなくても、勝手にうまくやってくれるやつ  
https://ccvanishing.hateblo.jp/entry/2018/10/02/203205