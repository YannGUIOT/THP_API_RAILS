
$ sudo service postgresql start

$ rails s

# TESTS :

REGISTER : $ curl -XPOST -H "Content-Type: application/json" -d '{ "user": { "email": "test2@example.com", "password": "0123456789" } }' http://localhost:3000/users
response : {"message":"Signed up successfully.","user":{"id":[id],"email":"test@example.com","created_at":[timestamp],"updated_at":[timestamp]}

LOGIN : $ curl -XPOST -i -H "Content-Type: application/json" -d '{ "user": { "email": "test2@example.com", "password": "0123456789" } }' http://localhost:3000/users/sign_in
response : HTTP/1.1 200 OK
X-Frame-Options: SAMEORIGIN
X-XSS-Protection: 0
X-Content-Type-Options: nosniff
X-Download-Options: noopen
X-Permitted-Cross-Domain-Policies: none
Referrer-Policy: strict-origin-when-cross-origin
Content-Type: application/json; charset=utf-8
Vary: Accept, Origin
Authorization: Bearer eyJhbGciOiJIUzI1NiJ9.eyJzdWIiOiIyMDQiLCJzY3AiOiJ1c2VyIiwiYXVkIjpudWxsLCJpYXQiOjE2NDYyMTk4MTEsImV4cCI6MTY0NjIyMzQxMSwianRpIjoiZWMxNDk3NWItOTNkYS00YTE1LTg1YTQtZmQ0ODllOTI2MTIwIn0.ZxRTdqSQ-Ahh4To9qdheeMewFHmbZtvWa_gSYx5mD38
Set-Cookie: _interslice_session=vOm61TiX5r758FI7DXxo07gRo%2F1lB08%2BrjKnf5N2q5oIOA4P3CI943u%2FbLSS3lJCyu%2FrFmLF8%2FliLCxhQTZN4DqNGgGgjZh6koGGyCxdFwshloUmSByg0D8vRA21kEQcCguvQ8BwJ1alzn6N9fAjXussdx63iL87TSUGhuWgSv3Ze4BkD1WsRG%2FFlH%2BJ%2Ba4mraPkGZCiQmfBlRLDjZ7n4mmWaE1ASsAhXmhf%2BeC79ag%2BQgE3ZOHkTzRUmnQft4BGeVC51ITCfvW47Cbi8elBQsfs2IzROxe9qtDOklzDcA%3D%3D--U%2FLRbl1%2FWXHqxKhR--lcsdl17IGM7jOT14NN8qZg%3D%3D; path=/; HttpOnly; SameSite=Lax
ETag: W/"3f408df0bede3cd5797e2190eefd79d9"
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: f1e51158-e4c6-42f2-bb94-535869cdccb5
X-Runtime: 0.256978
Server-Timing: start_processing.action_controller;dur=0.2275390625, sql.active_record;dur=1.86376953125, instantiation.active_record;dur=0.0888671875, process_action.action_controller;dur=234.275390625
Transfer-Encoding: chunked

{"message":"You are logged in.","user":{"id":204,"email":"test@example.com","created_at":"2022-03-01T19:50:54.482Z","updated_at":"2022-03-01T19:50:54.482Z"}}


LOGIN WITH TOKEN : $ curl -XGET -H "Authorization: Bearer PUT_HERE_YOUR_TOKEN " -H "Content-Type: application/json" http://localhost:3000/member-data
response : {"message":"If you see this, you're in!","user":{"id":204,"email":"test@example.com","created_at":"2022-03-01T19:50:54.482Z","updated_at":"2022-03-01T19:50:54.482Z"}}

LOGOUT WITH TOKEN : $ curl -XDELETE -H "Authorization: Bearer PUT_HERE_YOUR_TOKEN " -H "Content-Type: application/json" http://localhost:3000/users/sign_out
response : {"message":"You are logged out."}
