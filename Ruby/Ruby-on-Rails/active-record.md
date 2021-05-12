# active record
## findとfind_byとwhereの違い
https://qiita.com/YNYS2020/items/9e0131d110fdf61b42e8

- whereして取得件数が0でもnilが返ってくるのではなく、ActiveRecord::Relationのオブジェクトが返ってくる
 -なのでそのオブジェクトにさらにwhereとかしてもundefined methodとかにはならない
 - findは取得件数0だと例外エラー、find_byはnilが返る