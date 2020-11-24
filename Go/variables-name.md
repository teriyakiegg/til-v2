# variables name
ローカル変数名はスネークケースで書くとフォーマッターに怒られる。キャメルケースで書く  
ファイル名はスネークケース  
https://xblood.hatenablog.com/entry/2019/01/28/213223

変数名のIdはIDにしないとフォーマッターに怒られる

変数名に限らないが、Goの命名はムッチャシンプル。則ってなるべく短く簡潔な命名にする  
変数名に型名入れるのは静的型付け言語としては微妙っぽい。hogeListとかhogeMapとか。  
https://micnncim.com/post/2019/12/11/go-naming-conventions/

mapもsliceもvalueの複数形の変数名にする、で試し中。

mIDとかsIDとかまで省略するなら、mid, sidとかで全小文字の方が読みやすい説浮上
