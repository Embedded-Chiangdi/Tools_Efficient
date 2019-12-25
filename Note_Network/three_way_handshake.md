# TCP - Three way handshake
TCP stands for Transmission Control Protocol.  
Three way handshake stands for a way of how how TCP connection is established.
***
## Introduction
TCP provide reliable communication with something called **Positive Acknowledgement with Re-transmission(PAR)**. The Protocol Data Unit(PDU) of the transport layer is called segment. Before a reliable TCP connection to get established, three segements(SYNs and ACKs) should be exchanged between client and server which is called three way handshake.
***
## Techopedia explains
![Photo](https://i0.wp.com/networkustad.com/wp-content/uploads/2019/08/Three-way-handshake.png?resize=768%2C604&ssl=1)

***
1. `SYN` Client(Host) sends a segment with `SYN` which informs server there is a client to start a connection. 
2. `SYN+ACK` Server responds to the client with `SYN + ACK`.
3. `ACK` Client(Host) response server and they both establish a reliable connection. A full-duplex communication is established.

***
## Reference 
* [TCP 3-Way Handshake Process](https://www.geeksforgeeks.org/tcp-3-way-handshake-process/)
* [TCP 3-way Handshake -SYN, SYN-ACK, ACK](https://networkustad.com/tag/importance-of-tcp-three-way-handshake/)
* [TCP 3-Way Handshake (SYN,SYN-ACK,ACK)](https://www.inetdaemon.com/tutorials/internet/tcp/3-way_handshake.shtml)
* [TCP 3-Way Handshake (SYN, SYN-ACK,ACK)](https://www.guru99.com/tcp-3-way-handshake.html)
***