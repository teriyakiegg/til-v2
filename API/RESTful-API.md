# RESTful API

## Non RESTful
- /CreateUser
- /UpdateUser
- /DeleteUser
- /GetUser

## RESTful (URL is connected to resource)
- /UserInfo
  - request method
    - POST: create
    - PUT: update
    - DELETE: delete
    - GET: get

## 捉え方
「URL」で表現した一意の「リソース」を、HTTPプロトコルのGETやPUT等の「メソッド」でどう操作するかを定めたもの、と捉えておけば良さげ

## RailsでRestfulのAPIでのHTTPステータスコードど応答内容について
https://qiita.com/hrtkmztn/items/f3e2e44f16435fc5edc0#destroy

## idempotent
In REST, it seems to be common to refer to whether the final state of the resource is the same.  
```
If we follow the REST principles in designing our APIs, we will have automatically idempotent REST APIs for GET, PUT, DELETE, HEAD, OPTIONS, and TRACE methods. Only POST APIs will not be idempotent.

- POST is NOT idempotent.
- GET, PUT, DELETE, HEAD, OPTIONS and TRACE are idempotent.
```
https://restfulapi.net/idempotent-rest-apis/