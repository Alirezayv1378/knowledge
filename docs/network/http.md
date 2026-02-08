# HTTP
## The Web and HTTP
### Overview of HTTP
- HTTP stands for **Hyper Text Transfer Protocol**
- It's a protocol which used in browser(client) and server to talk to each other
- Http is **stateless protocol** which means an HTTP server maintains no information about the clients.
- It firsts initiates a [[tcp_udp|TCP]] connection.
### Non-Persistent and Persistent Connections
- **none-persistent connection:** each request/response pair send over a separate TCP connection.
- **persistent connection:** all requests and their corresponding responses send over the same TCP connection.

#### HTTP with Non-Persistent Connections
- Each TCP connection closed after server sends back the respond.
- **Round-Trip time (RTT):** Time it takes for a small packet to travel from client to server and then back to the client.
- **Three-way Handshake:** The client sends a small TCP segment to the server, the server acknowledges and responds with a small TCP segment, and, finally, the client acknowledge back to the server and also sends the HTTP request messages to the server with it.
- The total response time is two RTTs plus the transmission time at the server for each request.

#### HTTP with Persistent Connections
- The TCP connection remains open and if for a certain amount of time there is no request the connection will be closed
- So the handshake only happens once not for every request.
### HTTP Message Format
#### HTTP Request Message
```
Get /somedir/page.html HTTP/1.1
Host: www.someschool.edu
Connection: close
User-agent: Mozilla/5.0
Accept-language: fr
```
- First line is **request** line and the other lines called **header** lines.
- Connection: close => Tells the server to close TCP connection after it sends back the response.
- Some times the data passed to the server without `POST` method and browser uses "GET" method and passes the data within the URL: `www.somesite.com/animalsearch?monkeys&bananas`
#### HTTP Response Message
```
HTTP/1.1 200 OK
Connection: close
Date: Tue, 09 Aug 2011 15:44:12 GMT
Last-Modified: Tue, 09 Aug 2011 15:44:11 GMT
Content-Length: 6821
Content-Type: text/html

(data data data data ...)
```
##### Examples of Response Status Codes
1. 200 OK
2. 301 Moved Permanently: has `Location` in headers that browser uses to redirect to new URL.
3. 400 Bad Request
4. 404 Not Found
5. 505 HTTP Version Not Supported

> [!practice]
> - [ ] Open browser and navigate to a website, then use dev tools to inspect HTTP requests and responses



