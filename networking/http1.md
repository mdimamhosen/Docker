HTTP = Hyper Text Transfer Protocol - HTTP/1.0 - 1996


1. User wants to send data to the server
2. data -> http request -> 
3. http protocol -> tcp -> ip -> connection
4. send data over the tcp connection /get request
5. server process the request and send a response
6. res -> connection closed


Drawbacks of HTTP/1.0
1. Connection is closed after each request
2. No connection re-use
3. No pipelining
4. No keep-alive
5. 3 way handshake
6. 4 way teardown

Example:
If you open a website with 10 images, the browser sends 10 requests. Each request opens a new connection, sends the data, gets the response, and closes the connection. This makes the website load very slowly.

Easy English:
HTTP/1.0 is like talking to someone, but you hang up the phone after every sentence. If you want to say 10 things, you call 10 times. This wastes time and is not good for big websites.