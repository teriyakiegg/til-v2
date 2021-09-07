# validation
https://qiita.com/h1kita/items/772b81a1cc066e67930e

## validate uniqueness of two columns (together)
https://stackoverflow.com/questions/34424154/rails-validate-uniqueness-of-two-columns-together

## valid?
modelに対してvalid?でvaridationチェックできる  
https://qiita.com/h1kita/items/772b81a1cc066e67930e

## 独自のvalidation
https://qiita.com/SoarTec-lab/items/43a5aa7b65f61c26e0e6
```
class User < ActiveRecord::Base
  validate :name_valid?

  private

  def name_valid?
    if バリデーション条件
      errors.add(:name)
    end
  end
end
```

## errors.add詳細
https://qiita.com/yujiG/items/3e34e2e0e7b4120b0584

## エラー文変更
https://railsguides.jp/active_record_validations.html#message