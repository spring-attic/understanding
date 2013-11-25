# Understanding CORS

The [same-origin policy][same-origin-policy] is an important security concept implemented by web browsers to prevent Javascript code from making requests against a different origin (e.g., different domain) than the one from which it was served.
Although the same-origin policy is effective in preventing resources from different origins, it also prevents legitimate interactions between a server and clients of a known and trusted origin.

[Cross-Origin Resource Sharing (CORS)][cors] is a technique for relaxing the same-origin policy, allowing Javascript on a web page to consume a REST API served from a different origin.

## Handling Simple CORS requests

In the simplest scenario, cross-origin communications starts with a client making a GET, POST, or HEAD request against a resource on the server. In this scenario, the content type of a POST request is limited to `application/x-www-form-urlencoded`, `multipart/form-data`, or `text/plain`.
The request includes an `Origin` header that indicates the origin of the client code.

The server will consider the request's `Origin` and either allow or disallow the request.
If the request is disallowed, TODO.

However, if the server allows the request, then it will respond with the requested resource and an `Access-Control-Allow-Origin` header in the response.
This header will indicate to the client which client origins will be allowed to access the resource.

For example, suppose that client code served from foo.client.com were to send the following request for a resource at bar.server.com:

```
GET /greeting/ HTTP/1.1
User-Agent: Mozilla/5.0 (Macintosh; Intel Mac OS X 10_8_5) AppleWebKit/536.30.1 (KHTML, like Gecko) Version/6.0.5 Safari/536.30.1
Accept: application/json, text/plain, */*
Referer: http://foo.client.com/
Origin: http://foo.client.com
```

The `Origin` header tells the server that the client code originated from http://foo.client.com.
So it checks its same-origin policies and determines that it can serve the request.
The response might look like this:

```
HTTP/1.1 200 OK
Content-Type: application/json;charset=UTF-8
Date: Wed, 20 Nov 2013 19:36:00 GMT
Server: Apache-Coyote/1.1
Content-Length: 35
Connection: keep-alive
Access-Control-Allow-Origin: http://foo.client.com

[response payload]
```

The `Access-Control-Allow-Origin` indicates that "http://foo.client.com" is allowed access, but no other origins will be allowed access.

Optionally, `Access-Control-Allow-Origin` may be set to "*" to indicate that all client origins are allowed. This is considered an unsafe practice, however, except in special cases where an API is completely public and is expected to be consumed by any client.

## Pre-flight requests

If a request may have implications on user data, a simple request is insufficient. Instead, a preflight CORS request is sent in advance of the actual request to ensure that the actual request is safe to send.
Preflight requests are appropriate when the actual request is any HTTP Method other than GET, POST, or HEAD or if a POST request's content type is anything other than `application/x-www-form-urlencoded`, `multipart/form-data`, or `text/plain`. Also, if the request contains any custom headers, then a preflight request is required.

> **Note:** Some Javascript libraries, such as AngularJS and Sencha Touch, send preflight requests for any kind of request.

For example, suppose that a client served from foo.client.com performs a DELETE request against a resource at bar.server.com. The preflight request takes the form of an OPTIONS request with the following headers:

```
OPTIONS /resource/12345
User-Agent: Mozilla/5.0 (Macintosh; Intel Mac OS X 10_8_5) AppleWebKit/536.30.1 (KHTML, like Gecko) Version/6.0.5 Safari/536.30.1
Access-Control-Request-Method: DELETE
Access-Control-Request-Headers: origin, x-requested-with, accept
Origin: http://foo.client.com
```

The preflight request is essentially asking the server if it would allow the DELETE request, without actually sending the DELETE request.
If the server allows the original request, then it will respond to the preflight request like this:

```
HTTP/1.1 200 OK
Date: Wed, 20 Nov 2013 19:36:00 GMT
Server: Apache-Coyote/1.1
Content-Length: 0
Connection: keep-alive
Access-Control-Allow-Origin: http://foo.client.com
Access-Control-Allow-Methods: POST, GET, OPTIONS, DELETE
Access-Control-Max-Age: 86400
```

The response to the preflight request indicates (in the `Access-Control-Allow-Methods` header) that the client is allowed to issue a DELETE request for the given resource.
The `Access-Control-Max-Age` indicates that this preflight response is good for 86,400 seconds, or 1 day, after which a new preflight request must be issued.

In the meantime, the client will be allowed to send the original DELETE request for the resource.

[same-origin-policy]: http://www.w3.org/Security/wiki/Same_Origin_Policy
[cors]: http://www.w3.org/TR/cors/
