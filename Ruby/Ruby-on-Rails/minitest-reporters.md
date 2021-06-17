# minitest reporters
- REDやGREENの表示が見やすくなるのでいれとくべし
```
test/test_helper.rb

require "minitest/reporters"
Minitest::Reporters.use!
```