# measure program execution time
```
start := time.Now();
// 処理
end := time.Now();
fmt.Printf("%f秒\n",(end.Sub(start)).Seconds())
```
『golangでかかった処理時間を計算するには？』  
https://kwmt27.net/index.php/2012/07/06/golang%E3%81%A7%E3%81%8B%E3%81%8B%E3%81%A3%E3%81%9F%E5%87%A6%E7%90%86%E6%99%82%E9%96%93%E3%82%92%E8%A8%88%E7%AE%97%E3%81%99%E3%82%8B%E3%81%AB%E3%81%AF/

ちなみにsleepはこんな感じ  
time.Sleep(time.Second * 10) // 10秒
