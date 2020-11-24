# array to hash
色々ある。  
筆者的にはArray#zipが推しらしい。  
```
array = User.all
array.map(&:id).zip(array).to_h
```
https://tech.raksul.com/2018/02/06/ruby_array_to_hash/