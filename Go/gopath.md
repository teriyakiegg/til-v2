# gopath
https://katuo-ai.com/go-root-path

前までは$GOPATH/src配下に依存するパッケージもインストールされてたが  
今では$GOPATH/pkg/mod配下にインストールされるようになった模様  
https://techblog.kayac.com/migration-gopath-to-go-modules


goのレポジトリをcloneする時はghqではなくgo get  
```
You can also use " go get -u " to update packages and their dependencies.
```
