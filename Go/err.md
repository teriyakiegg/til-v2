# err
```
func failOnError(err error) {
    if err != nil {
        log.Fatal("Error:", err)
    }
}
```
こういうの生み出さないで、実直に都度エラー処理書くのが慣習っぽい

- errは_とかで基本消し飛ばさないで拾っておくのが良さげ

- parse系は出力を(err)だけじゃなくて("convert hoge value=%v error: %v", value, err) とかにしといた方がログを追う時良さげ

フォーマット指定子↓  
https://blog.y-yuki.net/entry/2017/05/02/000000  

- 基本は%vで問題無し
- 構造体は型とフィールド名が出る%#v使うのが良さげ(配列やスライスも型出るから良さげ)
- 型出すのは%T

他の型詳細↓  
https://qiita.com/Sekky0905/items/c9cbda2498a685517ad0

- trueかfalse(%t)、文字列(%s)、数値諸々(%d, %f)など、型を明示したいときはそれぞれの指定子を使えば良さげ

- エラーの作成
```
fmt.Errorf は fmt.Sprintf のようにフォーマットできる
errors.New 文字列のみでエラーを作成する
```
https://golang.hateblo.jp/entry/golang-errors-package-custom-error
