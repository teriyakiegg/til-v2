# two factor authentication effect
https://blog.hatappi.me/entry/2018/01/28/130550

```
Githubでセキュリティ面などから二段階認証を設定する。
ただこの二段階認証を設定した状態でpush先のリモートとしてhttpsプロトコルを利用すると問題が生じる。

問題としてはpush時にusernameとパスワードを求められてログイン時に使用しているusernameとパスワードを正しく入力してもエラーになってしまう。

ぐぐったりするとsshに切り替えていこうみたいな感じで書いてあってそれは分かるけど僕がやりたいのはそうじゃない

答えはGithub公式に書いてある
トークンを発行してpasswordを聞かれた時に入れると良いみたい!!
Creating a personal access token for the command line - User Documentation

これでhttpsをリモートに設定していてもpushができるようになる
ちなみにMacだとキーチェーンに保存されるので毎回いれなくて済むので楽!
```

- とりあえずsshでやるべし。
- 自分のプライベートなアカウントでssh key設定しておらず、毎回httpsで通信していたことが発覚して驚愕
- 毎回パスワード求められなかったのはkeychainに保存されてたからっぽい。OMG