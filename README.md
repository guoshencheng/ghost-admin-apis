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

post `/authentication/passwordreset`  private
put `/authentication/passwordreset` private
post `/authentication/invitation` private
get `/authentication/invitation` private
post `/authentication/setup` private
get `/authentication/setup` private
put `/authentication/setup` private
post `/authentication/token` private

post `/uploads` private







