# memorystore for redis
https://cloud.google.com/memorystore/docs/redis/connecting-redis-instance

- Cloud SQL Proxyみたいなのでの接続は無理っぽい
- 基本的には以下の模様。あとはGKE。
```
Redis インスタンスには、その Redis インスタンスと同じプロジェクト、リージョン、ネットワーク内に配置されている任意の Compute Engine VM インスタンスから接続できます。
```