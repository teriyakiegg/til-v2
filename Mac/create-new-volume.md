# create new volume
『macOSで他人に見られたくないデータを本気で暗号化する方法まとめ』  
https://qiita.com/igz0/items/06e29c46e6ef8389f5e4#4-%E6%9A%97%E5%8F%B7%E5%8C%96%E3%81%95%E3%82%8C%E3%81%9F%E3%83%9C%E3%83%AA%E3%83%A5%E3%83%BC%E3%83%A0%E3%82%92%E4%BD%9C%E6%88%90%E3%81%99%E3%82%8B

```
mount
$ diskutil apfs unlockVolume VolumeName

mount with passphrase
$ diskutil apfs unlockVolume VolumeName -passphrase PassPhrase

unmount
$ diskutil unmount VolumeName
```
https://derflounder.wordpress.com/2017/11/04/unlock-or-decrypt-an-encrypted-apfs-boot-drive-from-the-command-line/