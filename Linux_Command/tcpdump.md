![tcpdump](https://www.poftut.com/wp-content/uploads/2017/01/img_586f8deb3d860.png)
## tcpdump
In this tutorial, we are going to discuss Usages of tcpdump command along with some practical examples. Before you start use `tcpdump`, ensure your system has installed `tcpdump` already.
### Introduction
tcpdump, dump traffic on a network, is a packet sniffer for everyday use. Tcpdump use libcap library which is the core library used for packet sniffing. It also give us a option to save captured packets in a file for future analysis. It saves the file in a pcap format, that can be viewed by tcpdump command or use `wireshark`.
### Usage with examples
#### Capture Packets
On a standard Linux system there is a lot of interfaces. I means not just network interface also USB interfaces exists. Tcpdump can listen USB protocol from USB interfaces and other special Kernel devices. Tcpdump numbers interfaces as optionally usage. First to select interface list interfaces tcpdump can sniff and capture.
```
[jiangdi@example ~]# tcpdump -D
1.eth0
2.br0
```
Than we select the interface we wanna sniffer to. To use one of listed interfaces name or index can be used
```
tcpdump -i 2
//or 
tcpdump -i br0
```
to get the nework packets from all network interfaces, run the following command.
```
tcpdump -i any
```
Then, tcpdump prints out all collected pacekts if you don't run with `-w` option, which causes it to save packet file for later analysis.
```
tcpdump -i br0 -w br0_packet.cap
```
Besides, tcodump withour `-c` option continue capturing packets until it is interrupted bt a SIGINT signal(generated, for example, by typing your interrupt character, typically control-C) or a SIGTERM signal (typically generated with the kill(1) command); if run with the -c flag, it will capture packets until it is interrupted by a SIGINT or SIGTERM signal or the specified number of packets have been processed.
```
tcpdump -i br0 -c 5000 -w br0_packet.cap
```
In order to get much more detailed infomation of packet we should add such options `-vvv`.
```
tcpdump -i br0 -c 5000 -w br0_packet.cap -vvv
```
#### Filtering Packets
##### Protocol
To filter packets based on protocol, specifying the protocol in the command line.
```
tcpdump tcp
tcpdump icmp
tcpdump ssh
tcpdump ip6
```
##### IP
```
tcpdump host 1.1.1.1
```
Get all the packets based on the IP address, whether source or destination or both.
```
tcpdump src 1.1.1.1
tcpdump dst 1.1.1.1
```
To get packets based on source or destination of an IP address.
##### PORT
```
tcpdump port 22
tcpdump portrange 21-23
tcpdump src port 22
```
##### MAC
```
tcpdump ether 6c:11:61:a1:11:41
tcpdump ether src 1c:11:18:1e:1b:54
```
##### Combine Filters
Throughout these examples you can use standard logic to combine different filters.
> `and` or `&&`  
> `or`  or `||`  
> `not` or `!`  

```
tcpdump src 192.168.1.100 or dst 192.168.1.50 && port 22
tcpdump port 443 or 80
```
#### Analyze Packets
tcpdump use `-r` option  read a saved packet file.
```
tcpdump -r br0_packet.cap
```
Then you can analyze it for your intens.
### More detailed informations of tcpdump
More detailed info can be get from tcpdump man page as follow:
```bash
man tcpdump
```
### Reference
* [tcpdump(8) - Linux man page](https://linux.die.net/man/8/tcpdump)
* [Learn how to use tcpdump command with examples](https://linuxtechlab.com/learn-use-tcpdump-command-examples/)
* [Tcpdump Tutorial With Examples](https://www.poftut.com/tcpdump-tutorial-with-examples/)
* [12 Tcpdump Commands – A Network Sniffer Tool](https://www.tecmint.com/12-tcpdump-commands-a-network-sniffer-tool/)
* [An introduction to using tcpdump at the Linux command line](https://opensource.com/article/18/10/introduction-tcpdump)
* [Tcpdump Examples](https://hackertarget.com/tcpdump-examples/b)
* [A tcpdump Tutorial with Examples — 50 Ways to Isolate Traffic](https://danielmiessler.com/study/tcpdump/)
***