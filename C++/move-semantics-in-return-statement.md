# move semantics in return statement
>in a return statement copy elision can only occur, if the expression is the name of a local variable. If you write std::move(var), then it is not the name of a variable anymore. Therefore the compiler cannot elide the move, if it should conform to the standard.
 
https://stackoverflow.com/questions/19267408/why-does-stdmove-prevent-rvo
