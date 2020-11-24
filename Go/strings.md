# strings
文字列の中に1000.0てな感じで小数点以降の値がある場合、strconv.Atoi()でパースエラーになってしまう  
そんな時はstrings.Split()使えるよ、というやつ  
https://stackoverflow.com/questions/19278379/why-is-this-golang-code-to-convert-a-string-to-an-integer-failing
