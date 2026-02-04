# OSI - Open System Interconnection Model

By International Organization for Standardization (ISO) 1984

Open System Interconnection Means Multiple Systems Can Communicate. Here systems refer to computers or devices from different manufacturers.
Then why MODEL? A model is a conceptual framework or philosophy that helps to understand complex systems. The OSI model is a conceptual framework that standardizes the functions of a telecommunication or computing system into seven distinct layers.

7 Layers of OSI Model -

1. Physical Layer -> L1
2. Data Link Layer -> L2
3. Network Layer -> L3
4. Transport Layer -> L4
5. Session Layer -> L5
6. Presentation Layer -> L6
7. Application Layer -> L7

Please do not tell secrate passwords to anyone.


System -> 
    1. Hello World - Application Layer
    2. Text Encoding - Presentation Layer (JSON, XML,YAML, HTML)

    3. Session Management - Session Layer (Cookies, Sessions) - 
    Keep the connection alive, re-establish the connection, terminate the connection

    4. Transport Layer - Segment - Devide the data into smaller chunks -
        [sender_port] [data] [receiver_port] 

    5. Packet - Network Layer (IP Addressing, Routing) - Logical Addressing  - 
        [source_ip] [data_from_transport_layer] [destination_ip]

    6. Frame - Data Link Layer (MAC Addressing, Error Detection) - Physical Addressing -
        [source_mac] [data_from_network_layer] [destination_mac]

    7. Bits - Physical Layer (Cables, Hubs, Repeaters) - Transmit raw bits over a physical medium -
        010101010101010101010101010101010101010101010101010 