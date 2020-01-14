# sysctl 
A  powerful command for Linux Kernerl Security Hardening.
## Introduction
sysctl, a Linux command , acts as an interface to dynamically change the kernel parameters. Under effect of this command, we can modify the kernel parameters without recompiling the kernel or rebooting the machine.
## Usage
### Read current kernel parameters
```sh
sysctl -a
```
### Modify kernel parameters
Kernel parameters can be modified temporarily or permanently.
#### Modify by command
Using command can change kernel parameters temporarily. These changes will reset on reboot.
```
sysctl -w net.ipv4.icmp_echo_ignore_all=1
```
#### Modify by files
We can directly modify the files in procfs(/proc/sys/ directory) to alter the kernel parameter.
```sh
echo "1" > /proc/sys/net/ipv4/icmp_echo_ignore_all
```
#### Modify by configuration
Modify /etc/sysctl.conf can modify kernel parameters. 
```sh
vi /etc/sysctl.conf
net.ipv4.icmp_echo_ignore_all = 1
``` 
After we modify sysctl configuration file, we need to execute a command `sysctl -p` to load sysctl settings from the file /etc/sysctl.conf.

## Reference
* [How to Use /etc/sysctl.conf for Linux Kernel Security Hardening](https://linoxide.com/how-tos/linux-sysctl-tuning/)
* [Ipsysctl tutorial 1.0.4](https://www.frozentux.net/ipsysctl-tutorial/chunkyhtml/variablereference.html)
* [Tuning the Cluster Interconnect - Expert Oracle RAC Performance Diagnostics and Tuning - page 466](http://what-when-how.com/Tutorial/topic-996ljkisj/Expert-Oracle-RAC-Performance-Diagnostics-and-Tuning-476.html)
***