# map iterator value_type
mapのイテレーターを参照剥がしして得られる型は　　

std::pair<const Key, T>  
参照で受けるときに型のconstとか付け忘れるとコピーになってしまう。  
autoで受けとくのが無難　　

https://qiita.com/_EnumHack/items/f462042ec99a31881a81
