# capybara
## 不安定テストを生み出すCapybaraを調教する
https://speakerdeck.com/mstshiwasaki/bu-an-ding-tesutowosheng-michu-sucapybarawodiao-jiao-suru

## findがクエリ実行を繰り返す場合の制限時間(待ち時間)
Capybara.default_max_wait_time  
過ぎてもリトライしてくれるので画面描画待ちの際にfindは使える