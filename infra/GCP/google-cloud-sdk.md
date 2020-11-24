# google cloud sdk
https://cloud.google.com/sdk/docs/quickstart-macos?hl=ja

```
$ gcloud init
```
を実行後、最初の質問に y と回答するとブラウザが起動しgoogleアカウントでの認証を要求されるので、承認を行うと認証完了。


ホームディレクトリをきれいにしときたかったので、google-cloud-sdkは↓の記事のように /usr/local に格納。PATHをちゃんと通せば問題無し  
http://tech-blog.tsukaby.com/archives/482


- サービスアカウントとかブラウザでの認証承認とかの認証全般の詳しい説明  
『GCP と OAuth2』  
https://medium.com/google-cloud-jp/gcp-%E3%81%A8-oauth2-91476f2b3d7f

dockerで動かしてるサーバーからGCPに繋ぐ時は、docker上でもデフォルトクレデンシャル読めるようにせんといかん

## sdkの更新
以下のように更新あるよ、というメッセージが出て、
```
Updates are available for some Cloud SDK components.  To install them,
please run:
  $ gcloud components update
```
更新しようとしたら
```
ERROR: (gcloud.components.update) Permission denied: [/usr/local/google-cloud-sdk.staging]

Ensure you have the permissions to access the file and that the file is not in use.
```
これ出て、/usr/local/ に移したせいか~、とテンション下げないで、sudo付けてコマンド実行すれば問題無し。  
https://stackoverflow.com/questions/44514177/permission-denied-error-when-installing-gcloud-components

更新後のsdkで問題出ても、
```
$ gcloud components update --version 245.0.0
```
てな感じでversion指定すればrevertみたいなこと出来る模様。強い。
