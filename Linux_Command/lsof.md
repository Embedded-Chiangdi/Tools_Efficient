## lsof
lsof - list open file
### Description
As everything in Linux can be considered a file, this means that lsof can gather information on the majority of activity on your Linode, including network interfaces and network connections. `lsof` by default will output a list of all open files and the processes that opened them.
### Format Explain
```bash
lsof | less
COMMAND     PID   USER   FD      TYPE     DEVICE SIZE/OFF       NODE NAME
init          1   root  cwd       DIR        8,2     4096          2 /
init          1   root  rtd       DIR        8,2     4096          2 /
init          1   root  txt       REG        8,2   149284     129327 /sbin/init
init          1   root  mem       REG        8,2    59172        255 /lib/libnss_files-2.12.so
init          1   root  mem       REG        8,2  1909464        208 /lib/libc-2.12.so
init          1   root  mem       REG        8,2   120672       3964 /lib/libgcc_s-4.4.7-20120601.so.1
init          1   root  mem       REG        8,2    40268        216 /lib/librt-2.12.so
init          1   root  mem       REG        8,2   131848        223 /lib/libpthread-2.12.so
init          1   root  mem       REG        8,2   284780       1206 /lib/libdbus-1.so.3.4.0
init          1   root  mem       REG        8,2    38768        499 /lib/libnih-dbus.so.1.0.0
init          1   root  mem       REG        8,2   100500         34 /lib/libnih.so.1.0.0
init          1   root  mem       REG        8,2   145768        438 /lib/ld-2.12.so
init          1   root    0u      CHR        1,3      0t0       1258 /dev/null
init          1   root    1u      CHR        1,3      0t0       1258 /dev/null
init          1   root    2u      CHR        1,3      0t0       1258 /dev/null
init          1   root    3r     FIFO        0,8      0t0       3799 pipe
init          1   root    4w     FIFO        0,8      0t0       3799 pipe
init          1   root    5r     0000        0,9        0       1255 anon_inode
init          1   root    6r     0000        0,9        0       1255 anon_inode
init          1   root    7u     unix 0xf4dd4fc0      0t0       6537 socket
kthreadd      2   root  cwd       DIR        8,2     4096          2 /
kthreadd      2   root  rtd       DIR        8,2     4096          2 /
kthreadd      2   root  txt   unknown                                /proc/2/exe
ksoftirqd     3   root  cwd       DIR        8,2     4096          2 /
ksoftirqd     3   root  rtd       DIR        8,2     4096          2 /
ksoftirqd     3   root  txt   unknown                                /proc/3/exe
kworker/0     4   root  cwd       DIR        8,2     4096          2 /
kworker/0     4   root  rtd       DIR        8,2     4096          2 /
kworker/0     4   root  txt   unknown                                /proc/4/exe
migration     6   root  cwd       DIR        8,2     4096          2 /
migration     6   root  rtd       DIR        8,2     4096          2 /
migration     6   root  txt   unknown                                /proc/6/exe
migration     7   root  cwd       DIR        8,2     4096          2 /
migration     7   root  rtd       DIR        8,2     4096          2 /
migration     7   root  txt   unknown                                /proc/7/exe
```
![](https://www.linuxtechi.com/wp-content/uploads/2019/04/Process-parameter-lsof-command.jpg)
### Usage with Examples
```bash
#list of open files
lsof [file_name]
#list all open file
lsof
#list files opened by specified processes
lsof -u nginx
#list files opened by specified to a process
lsof -p [PID]
lsof -p 1100
#list files opened by internet (ipv4 or ipv6)
lsof -i 4
lsof -i 6
lsof -i@192.168.1.3
lsof -i udp
lsof -i TCP:80
lsof -i TCP:1-1048

#list IDs of processes that have opened a specified file
lsof -t [file_name]
#example as follow
lsof -t /var/log/messages
783
ps -ef | grep 783
root       783     1  0 03:33 ?        00:00:01 /sbin/rsyslogd -i /var/run/syslogd.pid -c 5
root     16097 26765  0 17:40 pts/0    00:00:00 grep 783
#list all open files under a specific directory
ksif +D [dir_name]
```
### Reference Reading
* [lsof(8) - Linux man page](https://linux.die.net/man/8/lsof)
* [How to List Open Files with lsof](https://www.linode.com/docs/networking/diagnostics/lsof/)
* [lsof](https://medium.com/@copyconstruct/lsof-f2b224eee7b5)
* [10 lsof Command Examples in Linux](https://www.tecmint.com/10-lsof-command-examples-in-linux/)
* [How to Use the Linux lsof Command](https://www.howtogeek.com/426031/how-to-use-the-linux-lsof-command/)
* [Linux lsof Command Tutorial for Beginners (10 Examples)](https://www.howtoforge.com/linux-lsof-command/)
* [18 Quick ‘lsof’ command examples for Linux Geeks](https://www.linuxtechi.com/lsof-command-examples-linux-geeks/)