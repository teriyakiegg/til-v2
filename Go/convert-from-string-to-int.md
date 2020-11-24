# convert from string to int
https://golang.org/pkg/strconv/

import "strconv"してstrconv.Atoi(対象のstring)

strconv.Itoa(対象のint)でintからstring

- ParseBool
- ParseFloat
- ParseInt
- ParseUint

とかもある。

他の型からstringへはfmt.Sprint(対象の型)とかでもいけるっぽい
