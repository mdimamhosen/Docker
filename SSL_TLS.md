SSL - Secure Socket Layer

TLS - Transpost Layer Security

Used in Trasport Layer - TCP / UDP


SSL Versions    
        - 1.0 - Never Released
        - 2.0 - Broken
        - 3.0 - Broken (Toodle Attack)

    TLS Version
            - 1.0 - 1999 - Deprecated
            - 1.1 - 2006 - Deprecated
            - 1.2 - 2008 
            - 1.3 - 2018 


How TLS Works ? 
                -> First Build the connection using 3 way TCP handshake.
                -> Now Do TLS Handshake with [

                    Step 1: Client Send A Hello Request to server
                                1. TLS Version
                                2. Random number
                                3. Cypher suits {Encoding Decoding Algorithms}
                    
                    Step 2: Server sends a hellow request to client
                                1. Random Number
                                2. Choosen TLS Version
                                3. Choosen Cypher Suits
                                4. Certificate {with a public key and private key}
                    
                    Step 3: Browser Checks:
                                1. Valid or not Certificate
                                2. Expired or not
                                3. Proper domain or not like valid for google microsoft etc

                    Step 4: Client:
                                1. Genarate A Secrate - Pre-master-secrate
                                2. Ecrypt that pre-master-secrate public key 
                    
                    Step 5: Client send that to the server

                    Step 6: Server Decrypt that with private key

                                   ]

Step 7: 
Client ------------------------ Server [Both_Genarate_Same_key_2_Unique_Key]

client write key   |   client read key
server read key    |   server write key

Total 4 called session keys

Step 8:
Client -> Fin
Step 9: 
Server -> Fin


# Now start data transfer using Normal HTTP request ; How Funny !!


