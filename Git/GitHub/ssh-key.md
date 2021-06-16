# ssh key
## 公式ドキュメント
https://docs.github.com/ja/github/authenticating-to-github/connecting-to-github-with-ssh/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent

## GitHub のレポジトリをクローンする際, HTTPS で指定された URL を SSH 用の URL として扱う方法
https://yu8mada.com/2018/10/31/how-to-treat-an-url-specified-in-https-as-one-for-ssh-when-cloning-a-repository-in-github/

```
[url "git@github.com:"]
  insteadOf = https://github.com/
```
- これでhttps通信を無理矢理全てssh通信にする(リポジトリ毎に設定を見直すのは面倒なので)