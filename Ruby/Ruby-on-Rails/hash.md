# hash

- 存在しないキーを指定した場合はデフォルトではnilが返る

## HashWithIndifferentAccess
https://qiita.com/hamajyotan/items/085ec6c518fa1f692f24#hashwithindifferentaccess
```
ActiveSupport::HashWithIndifferentAccess.new(nil)
=> {}

引数へのhash以外の値は、存在しないキーを指定した時のnilの代わりの値としてセットされる
```

よくrailsのparamsでも使われてるという記事を見るが、
```
But with Rails 5, ActionController::Parameters will no longer inherit from HashWithIndifferentAccess.
https://www.bigbinary.com/blog/parameters-no-longer-inherit-from-hash-with-indifferent-access-in-rails-5
```
らしい

### どっちも使えるから逆に迷う件
ここでも質問してる人いるがtopicとしてあまり盛り上がってない  
https://stackoverflow.com/questions/41004956/strings-vs-symbols-when-using-hashwithindifferentaccess

#### rails6.1型でコードを読んでみる
例えば既にハッシュがセットされているオブジェクトに[]でsymbolかstringのkey指定でアクセスする際
```
def [](key)
  super(convert_key(key))
end
```
https://github.com/rails/rails/blob/6-1-stable/activesupport/lib/active_support/hash_with_indifferent_access.rb#L164-L166

```
if Symbol.method_defined?(:name)
  def convert_key(key)
    key.kind_of?(Symbol) ? key.name : key
  end
else
  def convert_key(key)
    key.kind_of?(Symbol) ? key.to_s : key
  end
end
```
https://github.com/rails/rails/blob/6-1-stable/activesupport/lib/active_support/hash_with_indifferent_access.rb#L371-L379

ということなので、結局シンボルが来たらstringに変換してるだけっぽい  
特別な理由が無ければ、ハッシュのセットも取得も変換の必要のないstringを使えば良い気がしている