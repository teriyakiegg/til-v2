# Excel
データ分析とかになんだかんだ使う  

*Excel for Mac 16.40で動作確認

## 空白セルにNULL入力
1. cmd + a でセル全選択
2. ctrl + g で移動
3. 左下の「Special…」を選択後「Blanks」を選択
4. カラム名上部の文字入力欄で「NULL」を入力後、cmd + enter で空白セル全てにNULLが入力される


## 日付内のTを半角スペースに置換
yyyy/mm/ddThh:mm こんな表示が微妙な時

1. カラムを選択
2. Excel画面右上のFind&Selectから「Replace…」を選択
3. Find what: に「T」、オプションの「Match case」にチェック、Replace with: に「 」の半角スペースを入力してReplace Allで日付内のTが半角スペースに置換され、日付はyyyy/mm/dd h:mmの形式で表示される

## UTCをJSTに変換したい時
### [Excel] 協定世界時(UTC)を日本標準時(JST)に変換する計算式
https://a1-style.net/microsoft-365/iso8601-utc-convert/

## 出力されたcsvをExcelで開いて文字化けする場合
下記コマンドでBOM付きのUTF-8に変換すれば大抵解消される
```
$ nkf --overwrite --oc=UTF-8-BOM 対象ファイル
```
nfkがcommand not foundの場合、Macであればhomebrewでnfkはインストール可能

## カラムの上部の幅のとこダブルクリック
幅良い感じに広げてくれる

## 一番下の行まで式とかをfillしたい時、対象のセルの右下をダブルクリック
一番下の行までfillしてくれる。隣に埋まってるカラムがある場合だけ有効

## 式で =セル&セル
するとセル結合した結果を表示できる

## INT()
日付でINT関数適用すると、日付から時間を切り捨てることができる

## COUNTIF()
重複行とかカウントできる

# 重複行非表示
上の方からできる

# ソート
第一、第二.... と複数をキーにソートできる

# ピボットテーブル
テーブル内のいずれかのセル選択状態でInsertタブから作れる。  
カラムをレコード単位にしたりフィルターにしたりだなんだができてだいぶ便利  
ファイルの拡張子がcsvのままだと保存できないのでxlsmにして保存が必要

## コピーした内容を複数のレコードに反映したい時
1. セル”S2”を選択。
2. Ctrl＋Cでセル”S2”をコピー。
3. Ctrl＋Shift＋Endで範囲選択。
4. Enterで選択範囲にペースト。

## VLOOKUP

https://dekiru.net/article/21009/