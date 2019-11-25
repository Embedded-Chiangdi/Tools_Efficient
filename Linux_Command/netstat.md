## Netstat
![netstat](https://hsploit.com/wp-content/uploads/2019/02/Netstat-.png)
Netstat-is a powerful linux command which show the network's status of our system such as network connections, routing tables,interface statistics, masquerade connections, and multicase memberships. Here we are going to show how `netstat` works within examples.
### Usage of netstat
#### network connections
```bash
# list all ports 
netstat -a | more
# list all tcp ports' connections
netstat -at
# list all udp ports' connections
netstat -au
# list all unix socket connections
netstat -ax
```
#### listening state
```bash
# list only listening ports 
netstat -l
# list only listening tcp ports
netstat -lt
# list only listening udp ports
netstat -lu
```
#### interface statics
```bash
netstat -s
```
#### usful command as follow
```bash
# show service name with pid
netstat -tp
# show port number used by pid
netstat -anlp | grep $PID
# show which process using a particular port
netstat -anly | grep $portnumber
# show kernel routing information
netstat -r
# show the list of networks interfaces
netstat -i
# 
```
#### examples
```bash
netstat -atep | grep ssh
netstat -atnep | grep 443
```
### Frequently used options
| Option | Description |
|---|---|
|-i|Display table of network interfaces|
|-a|Show both listening and non-listening sockets|
|-e|Display additional information|
|-l|Show only listening sockets.|
|-t|Display TCP connections only|
|-n|Show numerical addresses instead of trying to determine symbolic host, port or user names.|
|-s|Display summary statistics for each protocol.|
### Reference Reading
* [netstat(8) - Linux man page](https://linux.die.net/man/8/netstat)
* [Netstat with examples](https://linuxtechlab.com/learn-use-netstat-with-examples/)
* [netstat Command Usage on Linux](https://geekflare.com/netstat/)
* [Netstat command in Linux](https://www.geeksforgeeks.org/netstat-command-linux/)
* [UNIX / Linux: 10 Netstat Command Examples](https://www.thegeekstuff.com/2010/03/netstat-command-examples)
* [NETSTAT Command: Learn to use netstat with examples](https://linuxtechlab.com/learn-use-netstat-with-examples/)
* [Learning Linux Commands: netstat](https://linuxconfig.org/learning-linux-commands-netstat)
***