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


