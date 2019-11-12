# Gdb and Core Dump notes
There are a few steps for us to use gdb and core dump.
1. Get a core dump
As usually , kernel won't creat core dump file. use `ulimit -c `command to check our environment.  
it show `0` means the switch is off. 
```
ulimit -c unlimited
``` 
turn on this switch.
2. Configure where core dump to store
`kernel.core_pattern` is a kernel parameter or a "sysctl setting" that decide where core dump file to save.  
```
sysctl -w kernel.core_pattern=/tmp/core_dump/core-%e.%p.%h.%t
```
Using above command will write core dumps to `/tmp/core_dump/core-<a bunch of stuff identifying the process>`. By default on Centos 7 ,core_pattern is set to 
```kernel.core_pattern = |/usr/libexec/abrt-hook-ccpp %s %c %p %u %g %t e %P %I %h
```
3. debug with core dump file

# Reference
* [How to get a core dump for a segfault on Linux](https://jvns.ca/blog/2018/04/28/debugging-a-segfault-on-linux/)
* 
* 
