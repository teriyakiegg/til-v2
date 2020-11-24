# Dynamic memory allocation
raw pointer : if you use new to create instance, you have to use delete manually.  
smart pointer : it has a destructor. When the pointer is out of scope, the destructor is called and check if the refference count is 0. If 0, the instance which the pointer points is going to be deleted.
  
From C++11, there three types of smart pointers: unique_ptr<T> shared_ptr<T> weak_ptr<T>.  
About the difference between them, read -> https://embeddedartistry.com/blog/2017/01/04/c-smart-pointers/  

『C++11スマートポインタ入門』  
https://qiita.com/hmito/items/db3b14917120b285112f
