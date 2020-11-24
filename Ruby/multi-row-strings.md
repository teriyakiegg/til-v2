# multi row strings
```
識別子には任意の文字列を指定できるが、「EOS」などがよく使われているらしい。(EOS=End of String)
こんな感じ。

str = <<-EOS
hello, world!
hello, ruby!
hello, rails!
EOS

p str #=>"hello, world!\nhello, ruby!\nhello, rails!\n"
```
らしい  
https://qiita.com/nomuyoshi/items/819942f06cc4c7fd8a26