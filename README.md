# RestAPI-Structure-Guideline
Guideline for creating REST API endpoints.



* URL structure should include api version number, eg. /v1/
* All GET methods should support limit and offset query string parameters, and have default values in case of absence. Sorting
* POST - new item, PUT - update, DELETE - remove, GET.
* In case query string params contain ?_method=DELETE, use method DELETE.

# API Authentication
- AuthKey Token as a request header.

POST /auth/signup  - new admin user
GET /auth/verifyemail/:verifcode  - activate account

POST /auth/signin  - login user (all types)
  response
  HEADERS: Set-Cookie: 'AuthKey=asdkljqldalskdjasd'
  {status: 'ok', AuthKey: 'asdkljqldalskdjasd'}

GET /auth/signout - logout user
  HEADERS: x-AuthKey: 'asdkljqldalskdjasd'

POST /auth/passrecovery - send pass recovery email
GET /auth/passrecovery/:chPassReqVerifCode - show form ({status: true, verifCode})
POST /auth/restpass (verifCode, new password) - rest pass

/users/current - GET (current logged in user info)


API endpoints
/v1/users - POST

/v1/users/2222 - PUT, DELETE, GET

## All API GET endpoints should implement COUNT, number of items.
/v1/users/count

# API resources - nouns, actions - verbs

GET /v1/dogs/13123

POST /v1/dogs/register

## ALL API GET endpoints should handle these params
?page=nnnn


## Response Codes

HTTP: 200, { status: “ok”, data: [] }

HTTP: 200, { status: “error”, message: “Error message“, error_code: 231 }

Return fields filter
	response_fields=[ short | long | public ]
