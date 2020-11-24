# CPU num
コア数は多ければ多いほど、その分並列処理が可能。  
激重処理が並列処理に対応していれば、コア数多い分早く終わる。  
コア数はPCのスペック見れば書いてある。
Dual Coreだったら物理コアは2個。(QuadとかHexaの数値は意味通り)  
物理と論理コアがあり、物理が2でも論理が4ならコア4つあるように振舞うことができるらしい。
```
Intelのハイパースレッド(HT)技術は、１つのコアで仮想的なCPUコアを増やしてくれる技術
```

shellコマンドでの確認記事↓  
https://yu8mada.com/2018/09/22/how-to-check-the-numbers-of-the-physical-and-logical-cores-of-a-mac-using-shell-commands/



https://infornography.blue/mac/mac-cpu-per-core-usage/

ちなみに、2.5 GHzとか書いてあるのはクロック数で、単純なクロック数だけでの比較なら、数値が高いほど処理が速い。その分消費電力は高い  
Activity MonitorのDock IconでShow CPU Usage見れる。論理コア含めた各コアの使用率がパッと見れる

### 参考
今使ってるmacbook pro
```
CPU: 2.5GHz Dual-Core Intel Core i7
Memory: 16GB
Storage: 500GB
```
前使ってたmacbook air
```
CPU: 1.3GHz Dual-Core Intel Core i5
Memory: 4GB
Storage: 128GB
```
