# TCP - Four Way handshake
Four way handshake stands for a way how TCP close connection between Client and Sever.
## Introduction
Four way handshake provides a secure authentication strategy for data delivered through network architectures.
## Techopedia explains
![4four handshake](https://media.geeksforgeeks.org/wp-content/uploads/CN.png)
1. `Fin from Client` When client application decides to close the connection. Client send a TCP segment `FIN` bit to server and enter `FIN_WAIT_1` state. During client in `FIN_WAIT_1` state, the client waits for a TCP segment from the server with an acknowledgment(ACK).
2. `ACK from Server` When Server received `FIN` bit segment from client. Server immediately send an acknowledgement segment to the client.
3. `Client Waiting` When client receives an Acknowledgement, the client enters the `FIN_WAIT_2` state. While client in the `FIN_WAIT_2` state, the client waits for another segment from the server with `FIN`. 
4. `FIN from server` Server sends a segment with `FIN` to the client.
5. `ACK from client` when client receives an `FIN` from server, client acknowledges to server in a `TIME_WAIT` state. The `TIME_WAIT` lets client resend the final acknowlledgment in case the `ACK`is lost. After `TIME_WAIT` , this connection formally closes and all resources on the client side are released.

## Reference
*** 
* [CTS 134: Understanding the 4-Way Handshake](https://www.cleartosend.net/understanding-4-way-handshake/)
* [TCP Connection Termination](https://www.geeksforgeeks.org/tcp-connection-termination/)