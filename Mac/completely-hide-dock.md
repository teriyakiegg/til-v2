# completely hide dock
『Mac の邪魔な Dock を消す方法』  
https://loumo.jp/archives/9540

```
defaults write com.apple.dock autohide-time-modifier -int 10; killall Dock
```
元に戻す
```
defaults write com.apple.dock autohide-time-modifier -int 1; killall Dock
```