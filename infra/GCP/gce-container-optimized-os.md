# gce container optimized os
https://cloud.google.com/container-optimized-os/docs/how-to/firewall

```
デフォルトでは、Container-Optimized OS のホスト ファイアウォールを使用すると SSH サービスのみを介した発信接続と受信接続が許可されます。Container-Optimized OS を実行している VM インスタンスで sudo iptables -L を実行することで、正確なホスト ファイアウォール構成を確認できます。
```

container optimized osでインスタンス作った場合、  
http通信を許可する、とかをインスタンス作成時にチェックしてても上記の理由で80ポートに接続は出来ない。

```
Docker のデフォルトのネットワーク名前空間でコンテナを実行する
ネットワーク経由でアクセス可能になる必要がある Container-Optimized OS にコンテナをデプロイする一方で Docker の --net=host オプションを使用しない場合は、-p オプションを使用してコンテナを実行します。このオプションを使用すると、Docker はネットワーク上でアプリケーションを公開するためのホスト ファイアウォールを自動的に構成します。Docker の実行オプションの詳細については、Docker の実行リファレンスをご覧ください。

次の例では、ポート 80 でネットワーク上の nginx コンテナにアクセスできます。


docker run --rm -d -p 80:80 --name=nginx nginx
```

