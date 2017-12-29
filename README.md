# Ghost 的 api 的整理

前缀一般为 `/ghost/api/v0.1/`

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

### 发送邮件重置密码

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


post `/authentication/passwordreset`  private
put `/authentication/passwordreset` private
post `/authentication/invitation` private
get `/authentication/invitation` private
post `/authentication/setup` private
get `/authentication/setup` private
put `/authentication/setup` private

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
