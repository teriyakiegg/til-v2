# install

## brewで
`$ brew install java11` 例えば11を入れる時  
インストール後↓  
`echo 'export PATH="/usr/local/opt/openjdk@11/bin:$PATH"' >> ~/.zshrc`  
`sudo ln -sfn /usr/local/opt/openjdk@11/libexec/openjdk.jdk /Library/Java/JavaVirtualMachines/openjdk-11.jdk`
これはIDEとかでJDKを参照する際に必要な認識  
[Homebrewでjavaをインストールする方法](https://qiita.com/ponsuke0531/items/9be8dee67a91c6c78d4f#java11%E3%82%92%E3%82%A4%E3%83%B3%E3%82%B9%E3%83%88%E3%83%BC%E3%83%AB%E3%81%99%E3%82%8B)