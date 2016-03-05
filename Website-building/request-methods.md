# HTTP Request Methods
*Origin Link: <https://www.w3.org/Protocols/rfc2616/rfc2616-sec9.html>*

### OPTIONS

The OPTIONS method represents a request for information about the communication options available on the request/response chain identified by the Request-URI.

> **From *WIKIPEDIA*:** The OPTIONS method returns the HTTP methods that the server supports for the specified URL. This can be used to check the functionality of a web server by requesting '*' instead of a specific resource.

### GET

The GET method means retrieve whatever information (in the form of an entity) is identified by the Request-URI. 

**Note:**

* The semantics of the GET method change to a "conditional GET" if the request message includes an If-Modified-Since, If-Unmodified-Since, If-Match, If-None-Match, or If-Range header field. 
* The semantics of the GET method change to a "partial GET" if the request message includes a Range header field. 

### HEAD

he HEAD method is identical to GET except that the server MUST NOT return a message-body in the response.

### POST

The POST method is used to request that the origin server accept the entity enclosed in the request as a new subordinate of the resource identified by the Request-URI in the Request-Line. 

### PUT

The PUT method requests that the enclosed entity be stored under the supplied Request-URI. 

### DELETE

The DELETE method requests that the origin server delete the resource identified by the Request-URI.

### TRACE

TRACE allows the client to see what is being received at the other end of the request chain and use that data for testing or diagnostic information. 

### CONNECT

This specification reserves the method name CONNECT for use with a proxy that can dynamically switch to being a tunnel.

### PATCH(RFC 5789)

The PATCH method applies partial modifications to a resource.

