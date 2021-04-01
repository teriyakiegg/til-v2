# model includes
includesでガバッと取ってこれる模様  
https://qiita.com/hirotakasasaki/items/e0be0b3fd7b0eb350327

tail -f log/development.log 見てると分かるが、  
確かに油断するとN+1発生するので、  
railsのAPIサーバーでjsonのserializeにhas_many, belongs_to関わってる時は、  
SQL取ってくるcontroller, model, policyとかでincludes入れるように気をつけるべし

includesに複数指定していて、更にuser: {comments: :category}こういうのしたい時は配列の最後の要素に配置しないとエラーになった