# testing
『Goのtestingパッケージの基本を理解する』  
https://qiita.com/taisa831/items/85fea8d970bcadd796b9

公式ドキュメント  
https://golang.org/pkg/testing/

## benchmark
```
The benchmark function must run the target code b.N times.
During benchmark execution, b.N is adjusted until the benchmark function lasts long enough to be timed reliably. 
The output

BenchmarkRandInt-8   	68453040	        17.8 ns/op

means that the loop ran 68453040 times at a speed of 17.8 ns per loop.
```