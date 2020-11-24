# LaunchDaemons
System wide and per-user daemon/agent manager  
MacOSXにおいてLinuxでいうところのinit.dとかcrondとかの代わりをしてくれるミドルウェア  
http://www.maruko2.com/mw/LaunchDaemons_(launchctl,_launchd.plist)_%E3%81%AE%E4%BD%BF%E3%81%84%E6%96%B9  
http://komaken.me/blog/2016/02/29/macosxlaunchd%E3%81%A8%E3%82%8A%E3%81%82%E3%81%88%E3%81%9A%E4%BD%BF%E3%81%A3%E3%81%A6%E3%81%BF%E3%82%8B%E3%81%BE%E3%81%A8%E3%82%81/

こいつでmac起動時に実行したいスクリプトとか登録できる  
https://qiita.com/hikouki/items/473d8ce0b1f562a94de6

シンタックスエラーチェック
```
plutil -lint hoge.plist
```
