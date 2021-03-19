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

https://datumstudio.jp/blog/sql%E3%81%A7%E7%B8%A6%E6%8C%81%E3%81%A1%E3%81%A8%E6%A8%AA%E6%8C%81%E3%81%A1%E3%82%92%E5%A4%89%E5%BD%A2%E3%81%99%E3%82%8B

縦持ちの表を横持ちにする時、完全に便利だった

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

日付+他の要素でグルーピングしたい時は、  
シンプルにGROUP BY date, 他の要素 で書けば良い。  
ORDER BYに必要な要素もシンプルにGROUP BYに追加すれば良い

GROUP BYには条件式も使える。  
CASE文とかも使えるので割と柔軟


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

## ROW_NUMBER
行に連番を振りたい時に使える
```
ROW_NUMBER() OVER ()AS id
```

## user_id_1, user_id_2で重複するパターンを除きたい時
https://codingsight.com/multiple-ways-to-remove-duplicates-from-sql-tables/

ここにある自身のテーブルを参照する方法を利用して、  
```
WHERE hoge.id IN
    (SELECT t1.id
     FROM hoge t1,
          hoge t2
     WHERE t1.id < t2.id
       AND t1.user_id_1 = t2.user_id_2
       AND t1.user_id_2 = t2.user_id_1) 
```
みたいな感じで除ける

## サブクエリ使う時
WITH 名前 AS (SELECT ...) という感じで先に宣言して後のSQLでテーブルとして参照できるので、  
WITH使うのも良し。  
BigQueryでNo default dataset is set in the requestとなった時に救われた。

WITHはMySQLだと8.0から導入された模様なので注意。

## ISNULL
SELECT文で判定したい時、ISNULL カラム名 とかにすればnullなら1、nullで無ければ0になる  
逆をしたい時はISNOTNULLは無いので、
```
SELECT (CASE WHEN カラム名 IS NOT NULL
             THEN 1 ELSE 0 END) AS is_hoge
```
とかで頑張る

## CROSS JOIN
https://itsakura.com/sql-cross-join

## FROM テーブル名 エイリアス
てな感じで気楽にエイリアス付けられる。長いやつには便利

## ORDER BY 2 DESC
この2はテーブルの2番目のカラムでorderするよという意味

## WHERE TRUE
```
条件を変更するときに最初の1行で AND をいちいち追加・削除せずに済む
```
カッコ良い。