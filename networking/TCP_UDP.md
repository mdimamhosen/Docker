L7 - Application Layer
L4 - Transport Layer 
        - TCP (Transmission Control Protocol) -> When data integrity and order are crucial. Like I send "Hello" and you receive "Hello" exactly as sent. 
        - UDP (User Datagram Protocol) -> When speed is more important than reliability. Like I send "Hello" and you might receive "Helo" or nothing at all. Or like a live video stream where occasional data loss is acceptable.
            These two protocols operate at this layer. If TCP then the data is broken into segments, if UDP then into datagrams.  

         ARPANET came up with TCP in the 1970s to ensure reliable communication over unreliable networks. UDP was introduced later for applications needing faster, connectionless communication.

L3 - Network Layer 
L2 - Data Link Layer
L1 - Physical Layer