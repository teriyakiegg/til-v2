# debian10 postgres install
https://k-koh.hatenablog.com/entry/2019/12/24/212636
```
$ psql --version
-bash: psql: command not found

$ sudo apt install postgresql

$ psql --version
psql (PostgreSQL) 11.12 (Debian 11.12-0+deb10u1)
```
- インストールするとデフォルトのポート5432で起動する
```
$ sudo su - postgres
$ createuser --pwprompt --interactive hoge
Enter password for new role:
Enter it again:
Shall the new role be a superuser? (y/n)

$ psql -U hoge -d postgres -h localhost
```