# editorconfig
『どんなエディタでもEditorConfigを使ってコードの統一性を高める』

https://qiita.com/naru0504/items/82f09881abaf3f4dc171

vscodeで使う際は`EditorConfig for VS Code`インストールした後、  
Settings -> Text Editor -> Formatting -> Format On Save にチェックつけておくと良し

## rubyでのインデントのタブサイズ変更したい
デフォルトだと4っぽいが、プロジェクト全体で2で統一されてる時、以下参照  
https://qiita.com/kenkono/items/85fd0f15bcec0ac64605

## ファイル全体をフォーマットして差分出過ぎるのを避けたい時
Format On Save ModeをFileじゃなくてModificationsにすると、  
変更した箇所だけフォーマットしてくれる模様。試し中。