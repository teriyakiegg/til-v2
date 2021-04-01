# pluck
任意のカラムのみ取得する時、便利。  
mapはrubyの機能だが、pluckはrailsのみ  
https://pikawaka.com/rails/pluck

## mapとpluckの一番の違い
発行されるSQLが違う。  
mapは全カラム、pluckは指定したカラムのみselectする  
https://qiita.com/TT-nasu/items/e6971efd1383d7f500dd

Active Recordに対してSQL発行するタイミングではなく、  
既に取得済みのオブジェクトから特定のフィールド取得したい時はmapで良し