# javascript_include_tag
## Rails 必要なJavaScriptのみを読み込む
https://keruuweb.com/rails-%E5%BF%85%E8%A6%81%E3%81%AAjavascript%E3%81%AE%E3%81%BF%E3%82%92%E8%AA%AD%E3%81%BF%E8%BE%BC%E3%82%80/
```
Railsは、初期状態でapp/assets/javascriptsディレクトリ以下の全てのJavaScriptを自動で読み込みます。
```
*require_treeディレクティブを使用している場合
```
個別のJavaScriptファイルを読み込むには、ビューファイルにてjavascript_include_tagを使います。
```