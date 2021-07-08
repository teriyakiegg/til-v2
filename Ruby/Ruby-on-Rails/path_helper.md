# path helper
```
リソースフルなルーティングを作成すると、アプリケーションのコントローラで多くのヘルパーが利用できるようになります。resources :photosというルーティングを例に取ってみましょう。

photos_pathは/photosを返します
new_photo_pathは/photos/newを返します
edit_photo_path(:id)は/photos/:id/editを返します (edit_photo_path(10)であれば/photos/10/editが返されます)
photo_path(:id)は/photos/:idを返します。 (photo_path(10)であれば/photos/10が返されます)
これらの_pathヘルパーには、それぞれに対応する_urlヘルパー (photos_urlなど) があります。_urlヘルパーは、_pathの前に現在のホスト名、ポート番号、パスのプレフィックスが追加されている点が異なります。
```
hoge_pathのhoge部分を知りたいときは rails routes で見れる
https://railsguides.jp/routing.html#%E3%83%91%E3%82%B9%E3%81%A8url%E7%94%A8%E3%83%98%E3%83%AB%E3%83%91%E3%83%BC