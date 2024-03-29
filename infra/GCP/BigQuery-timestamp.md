# BigQuery timestamp

## TIMESTAMP周りの挙動

FORMAT_TIMESTAMP()関数の返り値はstring

WHERE DATE(dateの列) IN ("2020-09-04") てな感じで日付絞りできる。date型 BETWEEN "2020-09-04" AND "2020-09-06" てな感じでもできる

CAST(string AS DATE) でstringのフォーマットがちゃんとdateになってたら型変換できる
```
▼STRINGからCASTする場合
DATEが求める文字列: YYYY-MM-DD
TIMESTAMPが求める文字列: YYYY-MM-DD HH:MM:SS UTC (UTCのとこのtimezoneは省くとUTCに。+か-の表記でも良い。マイクロセカンドが6桁まであっても良い。詳しくはリンク参照)
https://cloud.google.com/bigquery/docs/reference/standard-sql/data-types#time_zones
```

CASTできなかった奴のせいでクエリが失敗するのを防ぐにはSAFE_CASTを使う。
```
このようなエラーからクエリを守るには、SAFE_CAST を使用できます。SAFE_CAST はエラーの代わりに NULL を返すという点を除き、CAST とまったく同じです。
```
https://cloud.google.com/bigquery/docs/reference/standard-sql/functions-and-operators

## REGEXP_REPLACE
```
REGEXP_REPLACE(value, regex, replacement)
正規表現 regex と一致する value のすべての部分文字列が replacement で置き換えられて、STRING が返されます。
```

ちなみに、正規表現の先頭につく`r`  
```
raw文字列
r'...'やr"..."のように引用符の前にrをつけた文字列をraw文字列といいます。
raw文字列は、\がエスケープ文字になりません。
すなわち、単独の\でバックスラッシュを表します。 たとえば、r'\n'は'\\n'と同じです。
```

valueの中で置き換えしなくて良い箇所は何も気にしなくて良い。  
置き換えたい箇所を特定する正規表現をregexで指定。  
さらに、特定された中で置き換えたい箇所を()で指定する。

例:
```
REGEXP_REPLACE(hoge, r"[\.:]\d+ ([\+\-])(\d{2}):?\d{2}$", "\\1\\2:00")
```

この場合、hogeの文字列の中で、regexにマッチする部分を「"1番目に()にマッチした何か""2番目に()にマッチした何か":00」で置き換える、と解釈できる
```
2019-05-27 23:58:52:182 +0000
```
hogeがこの文字列だとすると、置き換えるのは「:182 +0000」部分。

"1番目に()にマッチした何か"は `+` 、
"2番目に()にマッチした何か" `00` 、

置き換え後の文字列は「+00:00」になる

### 参考
『正規表現のバックスラッシュの数字(\1)とは何か』  
https://www.toumasu-program.net/entry/2019/11/08/154528  

- ?はあっても無くても良い
- 角カッコ: 角括弧([...])は角括弧の中に記述した複数の文字のいずれか一つにマッチさせる場合に使用するメタ文字です。

## cast dateでgroup by
した場合はselect文でもgroup byで使った全く同じ文を指定しないとエラーになる

## 日付別テーブルでの日付範囲指定
今までの3年分とかスキャンするの毎回億劫...が無くなる。
```
テーブル名に"_yyyymmdd"のサフィックスがついてるBigQueryの日付別テーブルで、直近の1週間だけを読み込む対象にしたい時のWHERE
WHERE _TABLE_SUFFIX >= FORMAT_DATE('%Y%m%d', DATE_SUB(CURRENT_DATE(), INTERVAL 7 DAY))
```
http://daas.la.coocan.jp/bigquery/biguqery_jisenwaza.htm

テーブル名にサフィックスではなく、日付カラムや自動で付与される_PARTITIONEDTIMEとかでパーティショニングされてるテーブルの場合、  
対象のカラムに対して以下のようにやれば読み込み対象絞れる。(対象カラムをゴニョゴニョいじると読み込み対象は全ての日付に認識されてしまうので注意)
```
WHERE timestamp BETWEEN TIMESTAMP_TRUNC(TIMESTAMP_SUB(CURRENT_TIMESTAMP(), INTERVAL 90 DAY), DAY)
  AND TIMESTAMP_TRUNC(CURRENT_TIMESTAMP(), DAY)
```
https://cloud.google.com/bigquery/docs/querying-partitioned-tables?hl=ja#querying_ingestion-time_partitioned_tables_using_pseudo_columns

## FORMAT_TIMESTAMP
- %a: The abbreviated weekday name.	ex) Wed
- %b: The abbreviated month name.	ex) Jan
https://cloud.google.com/bigquery/docs/reference/standard-sql/date_functions#supported_format_elements_for_date