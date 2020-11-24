# GitHub Action

『10分で自分のGitHubプロフィールをカッコ良くする』  
https://qiita.com/Hassan/items/134009209f5709f892b1

feedに毎日表示されるのが鬱陶しいので日毎ではなく週毎に更新されるよう修正↓

```
-  schedule: # execute every 24 hours
-    - cron: '* */24 * * *'
+  schedule: # execute every week on Sunday
+    - cron: '0 0 * * 0'
```
https://github.com/teriyakiegg/teriyakiegg/commit/7783fdee4f827cf64dfee09a1b3ca30c49a39ec9