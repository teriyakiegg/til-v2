# jbuilder
https://llcc.hatenablog.com/entry/2015/03/07/103121


## インスタンス変数の共有
```
jbuilderでインスタンス変数を使う場合は、インスタンス変数を共有する為にjbuilderのファイル名を「アクション名.json.jbuilder」にする必要があります。

例えば、usersコントローラのindexアクションには、以下のように@usersのインスタンス変数が定義されています。

app/controllers/users_controller.rb | indexアクションでインスタンス変数を定義-->
class UsersController < ApplicationController
  def index
    @users = User.all # このインスタンス変数をjbuilderで使う
  end
end

indexアクションで定義した@usersは、app/views/users配下にindex.json.jbuilderという名前のファイルを作成する事でこのインスタンスを共有することが出来ます。
```
https://pikawaka.com/rails/jbuilder