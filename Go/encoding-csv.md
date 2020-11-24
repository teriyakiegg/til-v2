# encoding csv
https://golang.org/pkg/encoding/csv/  

『golangでcsvファイルを読み込みたい時』  
https://qiita.com/nanakrk965/items/7bb77d3ab0dda23d56d4

1行毎読み込んだときのrecordはstring型の配列

書き込むときの最後にwriter.Flush()書かなかったら、  
2020というレコードが謎に出力されてえらい目にあった
