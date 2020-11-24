# migration

## 説明
未実行のマイグレーションファイルを実行

## 使い方
```
$ rake db:migrate [VERSION=バージョン番号 オプション]
```
## 実行の流れ
1. rake db:migrateを実行
2. schema_migrationsテーブルを調べ、存在しなければ作成
3. db/migrateディレクトリ内のすべてのマイグレーションファイルを調べる
4. データベースの現在のバージョンと異なるバージョンがあった場合、データベースに適応
5. schema_migrationsテーブルの更新

https://railsdoc.com/page/rake_db_migrate

### 豆知識
schema_migrationsテーブルはRails DBには表示されない  
schema_migrationsテーブルにはdb/migrateディレクトリ内のファイルの日付が一行ずつどどどっと挿入される
