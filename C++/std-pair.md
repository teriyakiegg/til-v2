# std pair
>構造体テンプレートstd::pairは、2つの型の正確に 2つの戻り値を束ねることができます。  

>C ++ 11以降では、 std::make_pair代わりにイニシャライザリストを使用できます。  

C ++ 11  
```
#include <utility>  
std::pair<int, int> foo(int a, int b) {  
    return {a+b, a-b};
} 
```

https://riptutorial.com/ja/cplusplus/example/1917/std----pair%E3%82%92%E4%BD%BF%E7%94%A8%E3%81%99%E3%82%8B
