# Pointer and reference

```
int a = 10;
int* pA = &a;
int& rA = a;

cout << "a == " << a << "\n"; // a == 10
cout << "&a == " << &a << "\n"; // &a == 0x7ffe7fe3b82c
cout << "pA == " << pA << "\n"; // pA == 0x7ffe7fe3b82c
cout << "*pA == " << *pA << "\n"; // *pA == 10
cout << "rA == " << rA << "\n"; // rA == 10
cout << "&rA == " << &rA << "\n"; // &rA == 0x7ffe7fe3b82c
```
