# invalid date in IE11
嘘みたいな話だがこれで救われる
```
Yesterday I met new Date("2018-03-29 17:25:2") under IE11 for Invalid Date. Firefox and Google Chrome are normal. I don't know if it is the same as your problem. The solution is to replace "-" with "-". Changed to "/" to become new Date("2018/03/29 17:25:2"). I have poor English and I don't know if you can read it. Sorry.
```
https://github.com/moment/moment/issues/3968