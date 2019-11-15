## iptables
### Basic Concept
Iptables is just a command-line interface to the packet filtering functionality in netfilter. However, to keep this article simple, we won’t make a distinction between iptables and netfilter in this article, and simply refer to the entire thing as “iptables”.The Linux kernel comes with a packet filtering framework named netfilter. It allows you to accept, drop and modify traffic leaving in and out of a system. Iptables builds upon this functionality to provide a powerful firewall, which you can configure by adding rules.
### Type of Chains
>chains allow you to filter packets at various points.
>>![](http://www.zsythink.net/wp-content/uploads/2017/02/021217_0051_1.png)

* INPUT链：处理输入数据包。 
* OUTPUT链：处理输出数据包。  
* PORWARD链：处理转发数据包。  
* PREROUTING链：用于目标地址转换（DNAT）。
* POSTOUTING链：用于源地址转换（SNAT）。
### Type of Tables and Rules
tables allow you to do very specific things with packets.
* raw：网址过滤 
>iptables is a stateful firewall, which means that packets are inspected with respect to their “state”. (For example, a packet could be part of a new connection, or it could be part of an existing connection.) The raw table allows you to work with packets before the kernel starts tracking its state. In addition, you can also exempt certain packets from the state-tracking machinery.

* mangle：数据包修改
>This table allows you to alter packet headers in various ways.

* net：地址转换，用于网关路由器。
>This table allows you to route packets to different hosts on NAT (Network Address Translation) networks by changing the source and destination addresses of packets. It is often used to allow access to services that can’t be accessed directly, because they’re on a NAT network.

* filter：包过滤，用于防火墙规则。
>It is used to make decisions about whether a packet should be allowed to reach its destination.

*** 
Rule are defined in tables to match traffic packet. what should you do after matching them under rules ? That’s what targets are for — they decide the fate of a packet.

* ACCEPT：接收数据包。
> This causes iptables to accept the packet.

* DROP：丢弃数据包。
> iptables drops the packet. To anyone trying to connect to your system, it would appear like the system didn’t even exist.

* REJECT：拒绝数据包。
> iptables “rejects” the packet. It sends a “connection reset” packet in case of TCP, or a “destination host unreachable” packet in case of UDP or ICMP.

Some ohthre targets as follow:
* REDIRECT：重定向、映射、透明代理。
* SNAT：源地址转换。
* DNAT：目标地址转换。
* MASQUERADE：IP伪装（NAT），用于ADSL。
* LOG：日志记录。
### Connections between Tables,Rules and Chains.
> 链中存在对应的规则，规则又存在对应的表中。 任何数据与对应链中的规则匹配。则执行相应的操作。

![](http://www.zsythink.net/wp-content/uploads/2017/02/021217_0051_2.png)
***
![](http://www.zsythink.net/wp-content/uploads/2017/02/021217_0051_6.png)
### Command summary
* 查询iptables规则
```
iptables -L
iptables -L INPUT
iptables -t filter -L
iptables -t nat -L
```
使用`-L`选项即可显示iptables的规则，默认显示`FILTER`表格的规则。 设定查看别的表格需表上`-t`选项及表格名。
```
iptables -nvL
iptables --line-number -nvL
```
加上`-v`可以显示表格的更多信息。加上`--line-numbers`可以显示规则的编号。
* 增加规则
```
iptables -t filter -A INPUT -s 192.168.146 -j DROP//递增
iptables -t filter -I INPUT -s 192.168.146 -j DROP//插入
iptables -t 表 -A 链名 匹配条件 -j 动作
iptables -t 表 -I 链名 匹配条件 -j 动作
```
* 删除规则
```
iptables -t filter -D INPUT -s 192.168.146 -j DROP//删除命令
iptables -t filter -D INPUT 3//删除指定行命令
```
* 修改规则
```
iptables -e filter -R INPUT 1 -s 192.168.1.146 -j REJECT
```
* 清除已有iptables规则
```
iptables -F
```
* 其他范例
```
//block SSH connections from any IP address
iptables -A INPUT -p tcp --dport ssh -j DROP
//block SSH connections from 10.10.10.10.
iptables -A INPUT -p tcp --dport ssh -s 10.10.10.10 -j DROP
//block SSH connections from 59.45.175.0.
iptables -A INPUT -p tcp -m tcp --dport 22 -s 59.45.175.0/24 -j DROP
//屏蔽单个IP的命令
iptables -I INPUT -s 123.45.6.7 -j DROP
//重定向80端口打上0x01标签的报文到10.1.0.1:2060
iptables -t nat -D PREROUTING -p tcp --dport 80 -m mark --mark 0x01 -j DNAT --to-destination 10.1.0.1:2060
```


***
### Reference Reading 参考阅读：
* [iptables详解1：iptables概念](https://www.zsythink.net/archives/1199)
* [iptables详解2：iptables规则查询](http://www.zsythink.net/archives/1493)
* [iptables详解3：iptables规则管理](http://www.zsythink.net/archives/1517)
* [iptables(8)  - Linux man page](https://linux.die.net/man/8/iptables)
* [Linux命令大全 iptables命令](https://man.linuxde.net/iptables)
* [An In-Depth Guide to iptables, the Linux Firewall](https://www.booleanworld.com/depth-guide-iptables-linux-firewall/)
* [The Beginner’s Guide to iptables, the Linux Firewall](https://www.howtogeek.com/177621/the-beginners-guide-to-iptables-the-linux-firewall/)
* [Iptables Tutorial – Securing Ubuntu VPS with Linux Firewall](https://www.hostinger.com/tutorials/iptables-tutorial)

***