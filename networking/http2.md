HTTP/1.1 - 1999


Drawbacks of HTTP/1.1

1. Still only one request at a time. If you want to load 10 images, the browser sends 10 requests, but they wait for each other. This is called "head-of-line blocking".
2. Slow for loading many files together (like images, CSS, JS).
3. No real multiplexing (cannot send many requests at the same time on one connection).
4. Can keep the connection alive, but still not very fast for modern websites.
5. Example: If you open a website with 5 images, the browser sends 5 requests, but they are handled one after another, not all at once.

HTTP/2 - 2015

HTTP/2 is much faster and smarter.
1. Can send many requests at the same time on one connection (multiplexing).
2. Uses binary format, not text, so it's quicker for computers.
3. Compresses headers to save data.
4. Example: If you open a website with 5 images, the browser sends 5 requests, and they are handled together, so the page loads faster.

Drawbacks of HTTP/2.0

1. Not all old browsers and servers support HTTP/2.0.
2. Multiplexing can still have "head-of-line blocking" at the TCP level. If one packet is lost, all requests wait.
3. Harder to debug because it uses binary format instead of text.
4. Needs HTTPS (encryption) for most browsers, so setup is more complex.
5. Example: If your network is bad and a packet is lost, all requests on that connection pause until the packet is fixed.