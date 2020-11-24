# automator
『Macで複数アプリを一括で起動させるのにAutomatorを使えばよかった』  
https://ika-ring.net/blog/launch-multiple-apps-with-automator/

起動: Launch Application  
終了: Quit Application

## シェルスクリプト実行
Run Shell Script最高  
使いたいコマンドがcommand not foundだったらPATHを通せばok  
whichでコマンドの居場所探して下記のような感じで通す
```
export PATH=$PATH:/usr/local/bin
```

## record
自分のマウスやキーボードなどの行動を記録してくれる。マージ便利  
chromeに複数ユーザーでログインしていて、片方のウィンドウだけ開く、閉じる、を自動でしたい時にこのrecord機能が使えた。  
automator作成後はSecurity&PrivacyのAccessibilityで許可しなきゃいけないのが面倒だけど仕方無し

## chrome操作
chromeの操作がエラー出て実行できない時は↓を参考にApple Scriptにしたらエラー出ず実行できるようになった  
https://stackoverflow.com/questions/31301834/automator-not-working-with-google-chrome

### 追記:  
dockを右クリックして選択する、という行動はApple Scriptにしてもエラーが出るようになってしまった。  
これはdockを右クリックしないで別の操作でやりたいこと実現する、で回避した。  
recordでwatch me doする場合も、アクセス許可周りの挙動が怪しいので全部Apple Scriptに変換するようにした

### 追記の追記
dockをクリック自体全く安定しない。  
よく考えたらアプリケーションの起動はLaunch Application経由でやれば良かった。  
が、今度はPeopleをclickもうまくいかない。絶望

### 追記の追記の追記
この記事みたいな戦いになってるっぽい  
https://kk90info.com/%E3%80%90mac%E3%80%91%E4%BD%BF%E3%81%84%E6%96%B9%EF%BC%9F%E6%85%A3%E3%82%8C%EF%BC%9Fautomator%E3%81%AE%E3%80%8C%E8%A8%98%E9%8C%B2%E3%80%8D%E3%82%92%E4%BD%BF%E3%81%A3%E3%81%A6%E3%81%BF%E3%81%A6/

タチ悪いのはautomator起動しててrunした場合はうまくいって、spotlightから実行した場合は失敗したりする

メニューバーをキーボードから選択できるようなのでこれでリベンジ  
https://mac-ra.com/menubar-shortcut/

死

Apple Scriptにしてるのが悪い気がしてきた→だめ

Automator、魔物すぎる

### 追記の追記の追記の追記。勝利
Chromeのアカウント切り替えは、コマンド経由でユーザー指定での起動ができた。神。  
http://met4lic-akekure.hatenablog.com/entry/2017/02/08/235803
```
$ open '/Applications/Google Chrome.app' --args --profile-directory='Default'
$ open '/Applications/Google Chrome.app' --args --profile-directory='Profile 1'
```
自分の場合は最初にログインしたアカウントがDefaultで次にログインしたやつはProfile 1になってる模様だった

ChromeをQuitしてその次にこのコマンド置いててもうまくいかず。  
Pauseを2second入れてみたら動いた。今までのもPauseをチョコチョコ挟めば動いたのかもしれない疑惑

## アイコン変更
automatorで作ったアプリケーションのアイコンは変更できる。  
既存のアプリケーションのアイコンをコピペするのが一番楽。Get Infoからいける

## 追記の....
特定のアプリケーションで、cmd + h が効かなくて仕方なく最小化してたがDockがスマートじゃないことに対して、  
watch me doで自動化しようとして挫折してたが、
```
open --hide /Applications/Hoge.app
```
このコマンドで起動すると、起動+隠すが行えることを発見。これをAutomatorに組み込んでついにやりたいことが全て実現できた