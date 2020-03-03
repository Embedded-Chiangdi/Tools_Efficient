# Linux Bridge 网桥
Bridge, a virtul network device in Linux, works as network device called switches.  
The major components of a netwrok switch are a set of network ports, a control plane, a forwarding plane, and a MAC learning database.
* The set of ports: forward traffic between other switches and end-hosts in the network.
* Thr control plane : run the Spanning Tree Protocol (STP)
* The forwarding plane : process input frames from the network ports and make a forward decision.
* The MAC learning database : keep track of the host locations in the LAN.
## Reference
* [Linux Bridge - how it works](https://goyalankit.com/blog/linux-bridge)
* [Anatomy of a Linux bridge](https://wiki.aalto.fi/download/attachments/70789083/linux_bridging_final.pdf)
* [Linux-網橋原理分析](https://www.itread01.com/p/158724.html)