# Фактический прогон curl

```text
$ curl -sS -i --max-time 15 -X POST http://127.0.0.1:18008/api/v1/notes -H Content-Type: application/json -d {"title": "Go Mongo 1793436249897441000", "content": "Тест"}
HTTP/1.1 201 Created
Content-Type: application/json; charset=utf-8
Date: Sat, 31 Oct 2026 08:44:09 GMT
Content-Length: 186

{"id":"6ae5aa5960f878fda38466c3","title":"Go Mongo 1793436249897441000","content":"Тест","createdAt":"2026-10-31T11:44:09.91253+03:00","updatedAt":"2026-10-31T11:44:09.91253+03:00"}


$ curl -sS -i --max-time 15 -X POST http://127.0.0.1:18008/api/v1/notes -H Content-Type: application/json -d {"title": "Go Mongo 1793436249897441000"}
HTTP/1.1 409 Conflict
Content-Type: application/json; charset=utf-8
Date: Sat, 31 Oct 2026 08:44:09 GMT
Content-Length: 28

{"error":"duplicate_title"}


$ curl -sS -i --max-time 15 -X GET http://127.0.0.1:18008/api/v1/notes/6ae5aa5960f878fda38466c3
HTTP/1.1 200 OK
Content-Type: application/json; charset=utf-8
Date: Sat, 31 Oct 2026 08:44:09 GMT
Content-Length: 172

{"id":"6ae5aa5960f878fda38466c3","title":"Go Mongo 1793436249897441000","content":"Тест","createdAt":"2026-10-31T08:44:09.912Z","updatedAt":"2026-10-31T08:44:09.912Z"}


$ curl -sS -i --max-time 15 -X GET http://127.0.0.1:18008/api/v1/notes?q=Go&limit=1&skip=0
HTTP/1.1 200 OK
Content-Type: application/json; charset=utf-8
Date: Sat, 31 Oct 2026 08:44:09 GMT
Content-Length: 174

[{"id":"6ae5aa5960f878fda38466c3","title":"Go Mongo 1793436249897441000","content":"Тест","createdAt":"2026-10-31T08:44:09.912Z","updatedAt":"2026-10-31T08:44:09.912Z"}]


$ curl -sS -i --max-time 15 -X PATCH http://127.0.0.1:18008/api/v1/notes/6ae5aa5960f878fda38466c3 -H Content-Type: application/json -d {"content": "Обновлено"}
HTTP/1.1 200 OK
Content-Type: application/json; charset=utf-8
Date: Sat, 31 Oct 2026 08:44:09 GMT
Content-Length: 182

{"id":"6ae5aa5960f878fda38466c3","title":"Go Mongo 1793436249897441000","content":"Обновлено","createdAt":"2026-10-31T08:44:09.912Z","updatedAt":"2026-10-31T08:44:09.966Z"}


$ curl -sS -i --max-time 15 -X PATCH http://127.0.0.1:18008/api/v1/notes/6ae5aa5960f878fda38466c3 -H Content-Type: application/json -d {"title": ""}
HTTP/1.1 400 Bad Request
Content-Type: application/json; charset=utf-8
Date: Sat, 31 Oct 2026 08:44:09 GMT
Content-Length: 27

{"error":"title_required"}


$ curl -sS -i --max-time 15 -X DELETE http://127.0.0.1:18008/api/v1/notes/6ae5aa5960f878fda38466c3
HTTP/1.1 204 No Content
Date: Sat, 31 Oct 2026 08:44:09 GMT



$ curl -sS -i --max-time 15 -X GET http://127.0.0.1:18008/api/v1/notes/6ae5aa5960f878fda38466c3
HTTP/1.1 404 Not Found
Content-Type: application/json; charset=utf-8
Date: Sat, 31 Oct 2026 08:44:09 GMT
Content-Length: 22

{"error":"not_found"}


$ curl -sS -i --max-time 15 -X GET http://127.0.0.1:18008/api/v1/notes/abc
HTTP/1.1 404 Not Found
Content-Type: application/json; charset=utf-8
Date: Sat, 31 Oct 2026 08:44:10 GMT
Content-Length: 22

{"error":"not_found"}

```
