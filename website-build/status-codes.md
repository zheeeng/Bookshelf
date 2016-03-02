## Status Code Definitions.
*Origin Link: <https://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html>, <http://www.w3schools.com/tags/ref_httpmessages.asp>*

Following part lists commonly used status codes. All codes info check at *<https://en.wikipedia.org/wiki/List_of_HTTP_status_codes>*

### Informational 1xx

| Code  | Message                   | Description 
|:-----:|:-------------------------:|:------------
| 100   | Continue                  | Client should proceed to send remain part of request. 
| 101   | Switching Protocols       | The server is willing comply to switch protocols.

### Success 2xx

| Code  | Message                       | Description 
|:-----:|:-----------------------------:|:------------
| 200   | OK                            | The request is OK. 
| 201   | Created                       | The request has been fulfilled, and a new resource is created.
| 202   | Accepted                      | The request has been accepted for processing, but the processing has not been completed.
| 203   | Non-Authoritative Information | The request has been successfully processed, but is returning information that may be from another source.
| 204   | No Content                    | The request has been successfully processe, but is not returning any content.
| 205   | Reset Content                 | The request has been successfully processed, but is not returning any content, and requires that the requester reset the document view.
| 206   | Partial Content               | The server is delivering only part of the resource due to a range header sent by the client.

* 201: The newly created resource can be referenced by the URI(s) returned in the entity of the response, with the most specific URI for the resource given by a Location header field. If the action cannot be carried out immediately, the server should respond with 202 (Accepted) response instead.
* 203: Avaliable since HTTP/1.1
* 205:This response is primarily intended to allow input for actions to take place via user input, followed by a clearing of the form in which the input is given so that the user can easily initiate another input action. 
 
### Redirection 3xx

The action required may be carried out by the user agent without interaction with the user if and only if the method used in the second request is GET or HEAD. A client should detect infinite redirection loops, since such loops generate network traffic for each redirection.

**Note:** Content developers should be aware that there might be clients that implement maxium five redirections limitation.

| Code  | Message               | Description 
|:-----:|:---------------------:|:------------
| 300   | Multiple Choices      | The user can select URL from a link list and then go to that location.
| 301   | Moved Permanently     | The requested page has moved to a new URL.
| 302   | Found                 | The requested page has moved temporarily to a new URL.
| 303   | See Other             | The requested page can be found under a different URL.
| 304   | Not Modified          | Indicates the requested page has not been modified since last requested.
| 305   | Use Proxy             | The requested resource must be accessed through the proxy.
| 307   | Temporary Redirect    | The requested page has moved temporarily to a new URL.

* 300: Maximum five addresses. Unless it was a HEAD request, the response should include an entity containing a list of resource characteristics and location(s) from which the user or user agent can choose the one most appropriate. 
* 301/302/307: Unless the request method was HEAD, the entity of the response should contain a short hypertext note with a hyperlink to the new URI(s). If the status code is received in response to a request other than GET or HEAD, the user agent must not automatically redirect the request unless it can be confirmed by the user. **Note:** When automatically redirecting a POST request after a 301 status code, some existing HTTP/1.0 user agents will erroneously change it into a GET request.
* 304: The response must include: 1) Date. 2) ETag. 3)Expire.
* 305: The response must only be generated by origin servers.

### Client Error 4xx

| Code  | Message                           | Description 
|:-----:|:---------------------------------:|:------------
| 400   | Bad Request                       | The request could not be understood due to malformed syntax.
| 401   | Unauthorized                      | The request requires user authentication.
| 402   | Payment Required                  | Reserved for future use.
| 403   | Forbidden                         | The server is refusing to fulfill it.
| 404   | Not Found                         | The server has not found anything matching.
| 405   | Method Not Allowed                | The method specified in the Request-Line is not allowed.
| 406   | Not Acceptable                    | No content characteristics acceptable entities according to request header.
| 407   | Proxy Authentication Required     | The client must first authenticate itself with the proxy.
| 408   | Request Timeout                   | The server timed out waiting for the request.
| 409   | Conflict                          | The request could not be completed due to a conflict with the current state of the resource.
| 410   | Gone                              | The requested resource is no longer available and no forwarding address is known.
| 411   | Length Required                   | The server refuses to accept the request without a defined Content- Length.
| 412   | Precondition Failed               | The precondition given in the request evaluated to false by the server.
| 413   | Request Entity Too Large          | The server is refusing to process a request because the request entity is larger than the server is willing or able to process.
| 414   | Request-URI Too Long              | The server is refusing to service the request because the Request-URI is longer than the server is willing to interpret.
| 415   | Unsupported Media Type            | The server is refusing to service the request because the media type of the request is not supported by the requested resource.
| 416   | Requested Range Not Satisfiable   | The client has asked for a portion of the file, but the server cannot supply that portion.
| 417   | Expectation Failed                | The server cannot meet the requirements of the Expect request-header field.

* 403: If the server does not wish to make any information to explain why request is refused, could use status code 404 instead.
* 406: Unless it was a HEAD request, the response should include an entity containing a list of available entity characteristics and location(s). The entity format is specified by the media type given in the Content-Type header field.
* 407: The client may repeat request with a suitable Proxy-Authorization header field.
* 409: This code is only allowed in situations where it is expected that the user might be able to resolve the conflict and resubmit the request. The response body should include enough information for the user to recognize the source of the conflict. 
* 410: If the server does not know, or has no facility to determine, whether or not the condition is permanent, the status code 404 (Not Found) should be used instead. 
* 413: If the condition is temporary, the server should include a Retry-After header field to indicate that it is temporary and after what time the client may try again.
* 414: Occurs when a client has improperly converted a POST request to a GET request with long query information; the client has descended into a URI "black hole" of redirection; or when the server is under attack by a client attempting to exploit security holes present in some servers using fixed-length buffers for reading or manipulating the Request-URI.

### Server Error 5xx

| Code  | Message                       | Description 
|:-----:|:-----------------------------:|:------------
| 500   | Internal Server Error         | A generic error message, given when no more specific message is suitable.
| 501   | Not Implemented               | The server either does not recognize the request method, or it lacks the ability to fulfill the request.
| 502   | Bad Gateway                   | The server was acting as a gateway or proxy and received an invalid response from the upstream server.
| 503   | Service Unavailable           | The server is currently unavailable (overloaded or down).
| 504   | Gateway Timeout               | The server was acting as a gateway or proxy and did not receive a timely response from the upstream server.
| 505   | HTTP Version Not Supported    | The server does not support the HTTP protocol version used in the request

* 503: Service unavaliable is a temporary condition which will be alleviated after some delay. If known, the length of the delay may be indicated in a Retry-After header. If no Retry-After is given, the client should handle the response as it would for a 500 response. **Note:** This status code does not imply that a server must use it when becoming overloaded. Some servers may wish to simply refuse the connection.
* 505: The response should contain an entity describing why that version is not supported and what other protocols are supported by that server.
