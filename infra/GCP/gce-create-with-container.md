# gce create with container
インスタンス作成時、コンテナ指定でインスタンス作れる。

## コンテナの ENTRYPOINT コマンドに引数を渡す
https://cloud.google.com/compute/docs/containers/configuring-options-to-run-containers#passing_arguments_to_container_entrypoint_command

引数や環境変数も設定できる模様。

## 超要注意
https://cloud.google.com/compute/docs/containers/configuring-options-to-run-containers#publishing_container_ports
```
コンテナを伴う VM ではホスト ネットワーク モードが使用されます。
このモードでは、コンテナはホストのネットワーク スタックを共有し、ホストのインターフェースはすべてコンテナから使用可能です。
注: これは、docker run コマンドを使用する際に --network="host" フラグを渡すことと同じです。コンテナのネットワーク設定とホストモードをご覧ください。

コンテナポートには、ホスト VM ポートへの 1 対 1 のマッピングがあります。たとえば、コンテナポート 80 はホスト VM ポート 80 にマップされます。
Compute Engine ではポートの公開（-p）フラグをサポートしていないため、このフラグを指定しなくても、マッピングは機能します。
```

さらに、
https://stackoverflow.com/questions/49365500/google-cloud-deploy-as-container-from-gcr-ports-not-exposed-in-docker-contai

```
Other than what @Stefan R has told, you should also use PORT number greater than 1000 as auto deployed container images aren't run as root and hence can't access privileged ports.

https://www.staldal.nu/tech/2007/10/31/why-can-only-root-listen-to-ports-below-1024/

https://www.google.co.in/search?q=privileged+ports+linux&oq=privileged+ports+linux
```