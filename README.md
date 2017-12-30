# Ghost 的 api 的整理

前缀一般为 `/ghost/api/v0.1/`

请求分为两种，一种是公开的，一种是私有的，公开的接口可以直接访问，但是私有的接口需要添加一些表示登陆的凭着，登陆请求头如下

##### 登陆头部校验

|字段|说明|例子|
|-|-|-|
|authorization|登陆校验请求头，使用`Bearer <token>`的组合，token是使用登陆请求之后的返回值accesstoken|`Bearer AUll3lBzmZK89bJqtJuQEA17K1LEgKnVNVJlFcuyE238A57z5Qsy4eL6wTSerrVUkqKsSOv2fSc4BGrcCdR8aLT35m4yC23tTxrkzM55BV73MWKp3KGNzD46BSSmsd7Kt1i9dNg1IJcuBZhDl8sj4qdS13COpSF5EImhR9kgSeqJneeVMZhQvBDgdTPnZVwaJtl3ADXvEBaxlVPnErgIZRdQepsE8sY7F6YdNcm6ZqWsnOGXelYOoWal5yeifNn`|

### 登陆请求

请求路径: `/authentication/token`</br>
请求类型: post</br>
头部:

|字段|说明|🌰|
|-|-|-|
|Content-Type|请求体的类型|`application/json`|
|origin|请求来源，同源策略，不同源ghost会返回错误|https://blog.maihaoche.com|

请求体(body):

|字段|说明|例子|
|-|-|-|
|grant_type|鉴权类型，登陆一般为`password`|password|
|username|用户登录名|guoshencheng1@gmail.com|
|password|用户登陆的密码|123456|
|client_id|数据库中存储的，可以从数据库中查看|xxxxx|
|client_secret|数据库中存储的，可以从数据库中查看|xxxxx|

### 发送重置密码邮件

请求路径: `/authentication/passwordreset`</br>
请求类型: post</br>

请求体(body):

请求体被放置在`passwordreset`中，passwordreset是一个数组，但是数组中只有一个元素，元素的字段如下

|字段|说明|例子|
|-|-|-|
|email|需要重置密码的邮箱|guoshencheng1@gmail.com|


### 重置密码

请求路径: `/authentication/passwordreset`</br>
请求类型: put</br>

请求体(body):

请求体被放置在`passwordreset`中，passwordreset是一个数组，但是数组中只有一个元素，元素的字段如下

|字段|说明|例子|
|-|-|-|
|token|从邮箱点击链接之后会带上一个token，需要在修改密码的时候带上这个token|xxxxxxxxxxxxxxxx|
|newPassword|新的密码|123456|
|ne2Password|新的密码的第二次输入值|123456|


### 接受邀请

请求路径: `/authentication/invitation`</br>
请求类型: post</br>

请求体(body):

请求体被放置在`invitation`中，invitation是一个数组，但是数组中只有一个元素，元素的字段如下

|字段|说明|例子|
|-|-|-|
|token|从邮箱点击链接之后会带上一个token，在接受邀请的时候需要带上|xxxxxxxxxxxxxxxx|
|password|密码|123456|
|email|邮箱|guoshencheng1@gmail.com|
|name|用户名|guoshencheng|

### 查看邀请状态

请求路径: `/authentication/invitation`</br>
请求类型: get</br>

query:

|字段|说明|例子|
|-|-|-|
|email|邮箱|guoshencheng1@gmail.com|

### 查看是否激活了用户体系

请求路径: `/authentication/setup`</br>
请求类型: get</br>

返回例子：

```
{
  "setup": [
    {
      "status": true
    }
  ]
}
```


### 查看是否激活了用户体系

请求路径: `/authentication/configuration`</br>
请求类型: get</br>
头部：请查看私有权限api头部规

返回例子：

get `/configuration` private

get `/configuration/:key` private

get `/posts` public
post `/posts` private
get `/posts/:id` public
get `/posts/slug/:slug` public
put `/posts/:id` private
delete `/posts/:id` private

get `/settings` private
get `/settings/:key` private
put `/settings` private

get `/users` public
get `/users/:id` public
get `/users/slug/:slug` public
get `/users/email/:email` public
put `/users/password` private
put `/users/owner` private
put `/users/:id` private
post `/users` private

get `/tags` public
get `/tags/:id` public
get `/tags/slug/:slug` public
post `/tags` private
put `/tags/:id` private
delete `/tags/:id` private

get `/roles/` private

get `/clients/slug/:slug` public

get `/slugs/:type/:name` public

get `/themes` private
put `/themes/:name` private

get `/notifications` private
post `/notifications` private
delete `/notifications/:id` private

get `/db` private
post `/db` private
delete `/db` private

post `/mail` private
post `/mail/test` private

post `/uploads` private

post `/authentication/setup` private
put `/authentication/setup` private
