# virtual override
派生クラスでは仮想関数はoverride指定子付けるようにする。その場合、virtualは冗長なので付けないでおく。  
仮想関数はコンパイル時点で呼び出す関数が判断できないため、inline指定しても意味ないことが多い。  
呼び出すべき関数を限定する呼び出し方をしている場合は、インライン化できる  

仮想関数 | Programming Place Plus　C++編【言語解説】　第２７章  
https://programming-place.net/ppp/contents/cpp/language/027.html
