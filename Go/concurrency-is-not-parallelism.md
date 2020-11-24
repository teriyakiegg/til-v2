# concurrency is not parallelism
並行処理と並列処理の違い。
```
“Concurrency is about dealing with lots of things at once. Parallelism is about doing lots of things at once.” — Rob Pike
```
並列は同じ瞬間に別のことが実行されている。  
並行は同じ瞬間に別のことは実行されていない。実行されているのは一つだが、その一つがうまい具合にあれやったりこれやったりしてる。    
Goは並行であるconcurrentを採用している
https://medium.com/@k.wahome/concurrency-is-not-parallelism-a5451d1cde8d
