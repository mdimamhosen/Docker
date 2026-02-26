[ ----- Source Port ----- | ----- Destination Port ----- ]
[----- Length ---------   | --------- Checksum --------- ]
[------------------------ Data --------------------------]



Note: Ephimeral ports are typically used for the source port when a client initiates a connection, while well-known ports (0-1023) are used for the destination port when connecting to a server.

Total Header: 8 bytes (Source Port: 2 bytes, Destination Port: 2 bytes, Length: 2 bytes, Checksum: 2 bytes)

Total 32 bits

- Source Port: 16 bits (2 bytes)
- Destination Port: 16 bits (2 bytes)
- Length: 16 bits (2 bytes)
- Checksum: 16 bits (2 bytes)

No need of connection establishment. Just send the data and forget about it. No guarantee of delivery, order, or duplicate protection. 


16 bits = word = 2 bytes


In video in 1 second = 26 images


________________

Quick Protocol: Another new protocol that is designed for low-latency communication, often used in real-time applications like gaming and video streaming. It provides a faster alternative to TCP while still offering some reliability features.