# Unix tools for checking services

* [strace](#strace): it shows if a process is blocked or has any activity.
* [netstat](#netstat): it shows all the active connections to socket (including http).

## strace
strace is a diagnostic, debugging and instructional userspace utility for Linux. It is used to monitor and tamper with interactions between processes and the Linux kernel, which include system calls, signal deliveries, and changes of process state. The operation of strace is made possible by the kernel feature known as ptrace.

To check if a particular process is working, given its pid, run:

```
strace -p <pid>
```

## netstat
In computing, netstat (network statistics) is a command-line network utility that displays network connections for Transmission Control Protocol (both incoming and outgoing), routing tables, and a number of network interface (network interface controller or software-defined network interface) and network protocol statistics. 

To check if all the HTTP connections open, run:

```
netstat | grep http
```
