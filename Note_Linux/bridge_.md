# Linux Bridge 网桥
Bridge, a virtul network device in Linux, works as network device called switches.  
The major components of a netwrok switch are a set of network ports, a control plane, a forwarding plane, and a MAC learning database.
* The set of ports: forward traffic between other switches and end-hosts in the network.
* Thr control plane : run the Spanning Tree Protocol (STP)
* The forwarding plane : process input frames from the network ports and make a forward decision.
* The MAC learning database : keep track of the host locations in the LAN.

## 
A network bridge is a Link Layer device which forwards traffic between networks based on MAC addresses and is therefore also referred to as a Layer 2 device.It makes forwarding decisions based on tables of MAC addresses which it builds by learning what hosts are connected to each network. A software bridge can be used within a Linux host in order to emulate a hardware bridge, for example in virtualization applications for sharing a NIC with one or more virtual NICs.
#### Creating a btidge
manage a  network bridge using the ip tool from iproute2 package.
```s
#create a new bridge and change its state to up 
ip link add name $bridge_name type bridge
ip link set $bridge_name up
#add an interfcae into the bridge, its state must up
ip link set eth0 up
ip link set eth0 master $bridge_name
#show the existing bridges and associated interfaces
bridge link
#remove an interface from a bridge 
ip link set eth0 nomaster
#delete a bridge issue 
ip link delete $bridge_name type  bridge
#assign an ip address 
ip addr add dev bridge_name 172.16.17.1
```
***
manage a network bridge using the legacy brctl tool.
```s
#create a new bridge:
brctl addbr btidge_name
#dele a bridge
brctl delbr bridge_name
#add a device to a bridge fow exaple eth0
brctl addif bridge_name eth0
#show current bridges and what interfaces they are connected to:
brctl show

ip link set dev bridge_name up

```
Attaching an IP address to a bridge device is only necessary if you want to orignate, or receive IP traffic on that interface. If you are merely using your two NICs as a repeater (of sorts) then you shouldn't need an IP address.

## Reference
* [Linux Bridge - how it works](https://goyalankit.com/blog/linux-bridge)
* [Anatomy of a Linux bridge](https://wiki.aalto.fi/download/attachments/70789083/linux_bridging_final.pdf)
* [Linux-網橋原理分析](https://www.itread01.com/p/158724.html)
* [Introduction to Linux interfaces for virtual networking](https://developers.redhat.com/blog/2018/10/22/introduction-to-linux-interfaces-for-virtual-networking/)

1. [networking:bridge [Wiki]](https://wiki.linuxfoundation.org/networking/bridge)
2. [microHOWTO: Bridge traffic between two or more Ethernet interfaces on Linux](http://www.microhowto.info/howto/bridge_traffic_between_two_or_more_ethernet_interfaces_on_linux.html)
3. [Why do we need an IP address for a bridge?](https://askubuntu.com/questions/407828/why-do-we-need-an-ip-address-for-a-bridge)