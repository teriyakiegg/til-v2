# presence
## Rails: present?より便利なActiveSupportのpresenceメソッド（翻訳）
https://techracho.bpsinc.jp/hachi8833/2021_02_26/62326

```
#presenceメソッドは、オブジェクトが存在すればそのオブジェクトを返し、存在しなければnilを返したい場合にとても便利なショートカットです。
```

これが欲しかった。感動。

```
if user.name.blank?
  name = "What's your name?"
else
  name = user.name
end

↑これがこう↓

name = user.name.presence || "What's your name?"
```