# sql

### JOIN
JOIN(INNER JOIN)は条件に一致したレコードだけ取得。どちらかのテーブルにしか存在しない場合は結果に反映されない  

LEFT OUTER JOINは結合元で条件に一致してないレコードに関してはNULL埋めして結果に反映する。

RIGHT OUTER JOINは結合先で条件に一致してないレコードに関してはNULL埋めして結果に反映する。

https://www.ecoop.net/memo/archives/2007-11-14-1.html

### サブクエリ
https://qiita.com/aki3061/items/6df0513ccc5aa40a075a

### UNION ALL
https://sql55.com/t-sql/t-sql-union.php

### GROUP BY
集計関数とセット  
https://qiita.com/Go-Noji/items/5baeb790ade4b57126ff

GROUP BY使った場合、
```
SELECT句には，GROUP BY句で指定した列と集計関数のみを指定することができます．
```
http://www.sql-reference.com/summary/summary.html

集計関数で、ANY_VALUE()というのもある。グループのどれか任意の値を取得するというやつ。  
グループの中でどれも同じ値ならこれを使うで良い説? どの環境でも使える訳ではなさそう。BigQueryでは使える  
→あんま気にせず、MAX()とか使っとけば良さげ

GROUP BYで指定したカラム、集計関数を使うカラム以外のカラムを取得したい時↓  
「重複行削除の際、重複判定に指定したキー列項目以外の列も取得するSQL」  
https://a-habakiri.hateblo.jp/entry/2016/11/27/223143

### HAVING
GROUP BYで集計関数適用した後の値に対して条件指定したい場合はHAVINGをWHEREと同じノリで使える  
https://www.dbonline.jp/mysql/select/index10.html

## DISTINCT
単純な重複排除ならDISTINCT使える  
https://qiita.com/masniimura/items/7ac62b37f6b42c4e17bc

### ORDER BY
https://www.sejuku.net/blog/72918
```
ASC・・・昇順
DESC・・・降順
```
未指定だとデフォルトは昇順

## WHERE
NOT NULL, IS NOT NULLセットできる

## where句でエイリアス使いたい時
https://stackoverflow.com/questions/715462/sql-use-alias-in-where-statement

## DATE BETWEEN
```
WHERE DATE BETWEEN '2011/02/25' AND '2011/02/27'
```
https://stackoverflow.com/questions/5125076/sql-query-to-select-dates-between-two-dates

注意: 比較するDATEがDATETIMEだったりすると、fromからtoのtoの日付がyyyy/mm/dd 00:00:00になるので対象にならなくなってしまう。  
危なし。DATEで範囲指定するならDATEで比較するべし

## INSERT/UPDATE
あったり前だが、複数レコード一気に操作できる。