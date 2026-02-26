TCP -> Transmission Control Protocol 

Segments data - breaks data into smaller pieces for transmission.

Client and Server establish a connection (handshake) before data transfer.

Client ------------------------------------------------- Server
            SYN  ------------------------>
                            <------------------------  SYN+ACK
            ACK  ------------------------>
    
    Data Transfer begins after handshake is complete.

Four ways to terminate a TCP connection:

Client ------------------------------------------------- Server
            FIN  ------------------------>
                            <------------------------  ACK
                            <------------------------  FIN
            ACK  ------------------------>

    Data Transfer ends after termination is complete.



So, Transport Layer Protocols (like TCP) are responsible for:
- Establishing connections
- Segmenting data
- Ensuring reliable data transfer
- Terminating connections
- Flow control 
- Error detection and correction
So in one word, TCP is all about making sure data gets from one place to another reliably and in order!  


----------------------------------32 bits ------------------------------------               
Client -----------------------------------------------------------------Server
[ ---------Source Port---------------][-------------Destination Port --------]    |
[  -----------------------------Sequence Number------------------------------]    |
[  ------------------------Acknowledgment Number-----------------------------]    |______ Header
[ Data Offset 4 Bits | Reserved 6 Bits | Flags 6 Bits |Window Size   16 Bits ]    |
[        Checksum                     ][          Urgent Pointer             ]    |
[                           Options (if any)  + Padding                      ]    |
[                               Data                                         ]    + Data       
------------------------------------------------------------------------------
                             Total Segment
20 bytes (Header) + Data (variable size)
Source Port: The port number of the sender (client). 16 bits - 2^16 = 65536 possible ports.
Destination Port: The port number of the receiver (server). 16 bits - 2^16 = 65536 possible ports.
Sequence Number: A unique number assigned to each byte of data sent. It helps in reassembling the data in the correct order at the receiver's end.

Port types:
- Well-known ports: 0 to 1023 (e.g., HTTP - 80, HTTPS - 443, FTP - 21)
        HTTP (HyperText Transfer Protocol) - Port 80
        HTTPS (HyperText Transfer Protocol Secure) - Port 443
        SSH (Secure Shell) - Port 22 
        FTP (File Transfer Protocol) - Port 21
        Telnet - Port 23
        SMTP (Simple Mail Transfer Protocol) - Port 25
        DNS (Domain Name System) - Port 53

- Registered ports: 1024 to 49151 (e.g., MySQL - 3306, PostgreSQL - 5432)
- Dynamic/Private ports: 49152 to 65535 (used for temporary purposes)

IANA (Internet Assigned Numbers Authority) is responsible for managing the allocation of port numbers and ensuring that they are used appropriately. They maintain a registry of well-known and registered ports to prevent conflicts and ensure smooth communication between different applications and services on the internet.

Ephemeral Ports: These are temporary ports assigned by a computer's operating system when a program requests any available user port from the OS. They are typically used for the duration of a communication session and are released once the session ends. Ephemeral ports usually fall within the dynamic/private port range (49152 to 65535).


[
Sequence Number: A unique number assigned to each byte of data sent. It helps in reassembling the data in the correct order at the receiver's end. For example, if you send "Hello" as 5 bytes, the sequence numbers might be 1 for 'H', 2 for 'e', 3 for 'l', 4 for 'l', and 5 for 'o'. If the receiver gets the bytes out of order, it can use the sequence numbers to rearrange them correctly.

Acknowledgment Number: A number sent by the receiver to the sender to indicate that it has received a segment of data. It is typically the sequence number of the next expected byte. For example, if the sender sends bytes with sequence numbers 1 to 5, and the receiver successfully receives them, it might send an acknowledgment number of 6 to indicate that it is expecting the next byte to have a sequence number of 6.
]


Data Offset:  Total number of 32-bit words in the TCP header. It indicates where the data begins. Since the minimum TCP header size is 20 bytes (5 words), the data offset will be at least 5. If there are options included in the header, the data offset will be greater than 5, indicating that the header is larger than the minimum size. The maximum data offset is 15, which corresponds to a maximum header size of 60 bytes (15 words). 

Reserved: 6 bits reserved for future use. They are typically set to zero and should be ignored by the receiver. 

Flags: 6 bits - 2^6 = 64 possible combinations of flags. Each flag represents a specific control function in the TCP protocol. Some common flags include:
        1. SYN 
        2. ACK
        3. FIN - Indicates that the sender has finished sending data and wants to terminate the connection.
        4. RST (Reset)
        5. PSH (Push)
        6. URG (Urgent)


Window Size: The number of bytes the sender is willing to receive before sending an acknowledgment. It is used for flow control to prevent overwhelming the receiver with too much data at once. 15 bits - 2^15 = 32768 bytes (32 KB) maximum window size.

Checksum: A value calculated by the sender based on the contents of the TCP segment. It is used by the receiver to verify the integrity of the received data. If the calculated checksum at the receiver's end does not match the checksum sent by the sender, it indicates that there was an error in transmission, and the segment may be discarded or a request for retransmission may be made.

Urgent Pointer: A value that indicates the end of urgent data in the segment. It is used when the URG flag is set to indicate that there is urgent data that needs to be processed immediately. The urgent pointer points to the sequence number of the last byte of urgent data in the segment.

Options: 
                timestamp,
                maximum segment size (MSS),
                window scaling,
                selective acknowledgment (SACK),
                and others.




The minimum TCP Header size is 5 (20 bytes) and the maximum is 15 (60 bytes). 