# CLI
## 認証情報
~/.aws/config に[profile hoge]を記載して、  
~/.aws/credentials に
```
[hoge]
aws_access_key_id = XXXXX
aws_secret_access_key = XXXXX
```
を用意しておくと、  
$ aws --profile hoge でhogeの認証情報を利用したawsコマンドを実行できる