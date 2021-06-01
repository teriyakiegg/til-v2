# gcloud account switch
https://qiita.com/sonots/items/906798c408132e26b41c

## デフォルトクレデンシャル
gcloudアカウント切り替えたらデフォルトクレデンシャルも切り替える必要ありそう  
https://medium.com/google-cloud-jp/gcp-%E3%81%A8-oauth2-91476f2b3d7f
```
$ gcloud auth application-default login
```
このコマンド叩けば~/.config/gcloud/application_default_credentials.json ここにトークンが保存され、プログラムからGCPのapi叩けるようになる