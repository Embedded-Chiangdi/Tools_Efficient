# Note for GDB
## some examples of GDB Debug
* GDB Debug core dump and analyze:[example](/Note_GDB/gdb_core/gdb_core.md)  
***
## Tutorial
***
## GDB Tutorial Part I 
Spend a few hours to learn one so you can avoid dozens of hours of frustration in the future.
### Prerequisites to GDB
Before we start , make sure that when we compiled the program with the option `-g`.ie
```
$gcc -g hello.c -o hello
```
Compiles hello.c with the debugging option (-g). We still get an a.out(here we name it as hello), but it contains debugging information that lets you use variables and function names inside GDB, rather than raw memory locations (not fun).
### How to start  GDB
If we want to debug a programm.First we must launch the debugger. Here are what they looks like when I run it:  
```
$gdb <program>
gdb hello jack tom
$gdb -p <pid>
```
For start the debugger with our program in ged , type`r`or `run` in gdb to start execution.if you want to pass argumens to programm, you can do as follow.
```
run arg1 arg2...
``` 
exit the debbugger with `quit` command.
##  some basic commands for debugging
#### Steping
Stepping lets you trace the path of your program, and zero in on the code that is crashing or returning invalid input.
```
list
step
next
finish
continue
```
The diff between `next` and `step` is that `next` won't dive into functions, but `step `will jump into the function and execute the first statement, then pause.
#### Breakpoints and Watchingpoints
Breakpoints are one of the keys to debugging. They pause (break) a program when it reaches a certain location. You can examine and change variables, then resume execution. Set a watchpoint, which pauses the program when a condition changes.This is helpful when seeing why certain inputs fail, or testing inputs.
```
break <where>
break 45
break myfunction
watch x == 3
delete/enable/disable <watchpoint/breakpoint>
delete breakpoint N
clear
//delete all breakpoints
```
#### Variables
Typically, you will view/set variables when the program is paused.
```
print
print x
display
display x
undisplay
display x
```
`display` Constantly display value of variable x, which is shown after every step or pause. Useful if you are constantly checking for a certain value. Use undisplay to remove the constant display.  
Another useful command to display memory contents is `x` command.
syntax as follow:
```cpp
x [address expression]
x 
x / [format] [address expression]
x / [length][format] [address experssion]
//debug programm
int main()
{
    char testArray[] = "0123456789ABCDEF";
    return 0;
}
//debug
x testArray
x/c testArray
```
Formati options as follows:
- o - octal
- x - hexadecimal
- d - decimal
- u - unsigned decimal
- t - binary
- f - floating point
- a - address
- c - char
- s - string
- i - instruction
length is how many words do u wanna show. the word is define as follow option:
- b - byte
- h - halfword (16-bit value)
- w - word (32-bit value)
- g - giant word (64-bit value)

## GDB Tutorial Part II
Spend a few hours to learn one so you can avoid dozens of hours of frustration in the future.
### Manipulating the Program
Changing variables at run-time is an important ways of debugging.Try giving functions invalid inputs or running other test cases to find the root of problems. Typically, you will view/set variables when the program is paused.
```
//syntax of set
set var <variable_name>=<value>
//ie of set
set x = 3
set x = y
//syntax of return
return <experssion>
```
The `return` command force the current function to return immediately,passing the given value. 
### Infomations
`info` command displays all register ,the argument to the function of the current stack frame,infomation of break/watch points,local variables and so on. when debugged program. This command helps u a lot to inspect the status of program,
```
info args
info breakpoints
info display
info locals
info threads
info sharedlibrary
info signals
```
### Handling Signals
Signals are messages thrown after certain events, such as a timer or error. GDB may pause when it encounters a signal; you may wish to ignore them instead.
```
handle [signalname] [options]
handle SIGUSR1 nostop
handle SIGUSR1 noprint
handle SIGUSR1 ignore
```
Tell GDB to ignore a certain signal  (SIGUSR1) when it occurs . There are varying levels of ignore.  
Options are :
```
(no)print
//(don't)print message when signals occurs
(no)stop
//(don't)stop the program when signals ocurs
(no)pass
//(don't)pass the signal to the program
ignore
```


## GDB Tutorial Part III
Spend a few hours to learn one so you can avoid dozens of hours of frustration in the future.
### Attaching GDB to a Process
When the program is running as a process, we can use `attach` command to debug programs.
1. Find the pid of program at first.
```shell
$ps -ef | grep program
```
2. Attach GDB to this process.
```shell
gdb attach pid
//or 
gdb -p pid
```
when we have finished debugging the program which we attach for. We should use `detach` command to release from it.
### Threads
It's common that programs use threads to achieve parallel execution. GDB has the ability to debug individual threads, and to manipulate and examine them independently.
```
info threads
```
display a list of threads with theri `id` and `gid`numbers,indicating the current thread.
```
thread id
```
set the thread with the specified `id` as the current thread.
```
thread apply [id] | [all] args
```
the `thread apply`command allows you to apply a command to one or more threads.   
some ie as follows.
```
(gdb)info thread
(gdb)thread 1
(gdb)thread apply 4 5 backtrace
(gdb)thread apply all backtrace
```
### Stack 
when we use gdb to debug our programm.program has stoped , the first thing we should check it stoped and how it got there.Each time your program performs a function call, information about the call is generated. That information includes the location of the call in your program, the arguments of the call, and the local variables of the function being called. The information is saved in a block of data called a stack frame. The stack frames are allocated in a region of memory called the call stack.
```
backtrace
bt
bt n
//print outermost n frames
where
//show call stack
backtrace full
//show call back,also print the local variables in each frame.
frame n
//select the stack frame to opreate on.
up n
down n
```



[RMS's gdb Debugger Tutorial](http://www.unknownroad.com/rtfm/gdbtut/gdbtoc.html)  
[DEBUGGING A RUNNING APPLICATION](https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux/7/html/developer_guide/debugging-running-application)  
[Debuging with GDB](https://betterexplained.com/articles/debugging-with-gdb/)  
[Guide to Faster, Less Frustrating Debugging](http://heather.cs.ucdavis.edu/~matloff/UnixAndC/CLanguage/Debug.html)
[pthread debugging](https://www.cs.swarthmore.edu/~newhall/unixhelp/gdb_pthreads.php)