# select duplicated records on conditions
https://www.go-next.co.jp/blog/web/18252/
```
SELECT hoge_id, fuga_id, name FROM hoges
GROUP BY hoge_id, fuga_id, name
HAVING COUNT(*)>1;
```