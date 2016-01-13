# 信号

除了管道之外，还有很多种方式可以和正在运行的进程发生通信或交互。``信号``就是其中一种。
进程可以接受不同的``信号``并做出不同的响应，也可以选择忽略该种信号，但是某些信号由内核直接处理，
进程不可忽略(如``SIGKILL``)。例如，对正在运行的服务进程，可以停止，可以重新加载配置等，
都是给正在运行的进程发送信号实现的。

给进程发送信号的命令是``kill``，看kill的man手册:

```
NAME
       kill - send a signal to a process

SYNOPSIS
       kill [options] <pid> [...]

DESCRIPTION
       The  default  signal  for  kill is TERM.  Use -l or -L to list available signals.  Particularly useful signals include HUP, INT, KILL, STOP, CONT, and 0.  Alternate signals may be specified in three
       ways: -9, -SIGKILL or -KILL.  Negative PID values may be used to choose whole process groups; see the PGID column in ps command output.  A PID of -1 is special; it indicates all processes except the
       kill process itself and init.
```

用``kill -l``可以显示出kill可以发送的信号列表，通常默认是``15``，即``SIGTERM``。

以下三种写法都是对的:

```
kill -15 PID
kill -SIGTERM PID
kill -TERM PID
```

常见的信号列表(节选自``man 7 signal``):

 Signal | Value | Action |  Comment
 ------ | ----- | ------ | --------------------------------------------------------------
 SIGHUP |   1   | Term   | Hangup detected on controlling terminal or death of controlling process
 SIGINT |   2   | Term   | Interrupt from keyboard
 SIGKILL|   9   | Term   | Kill signal
 SIGPIPE|   13  | Term   | Broken pipe: write to pipe with no readers
 SIGTERM|   15  | Term   | Termination signal
 SIGUSR1|30,10,16| Term  | User-defined signal 1
 SIGUSR2|31,12,17| Term  | User-defined signal 2
 SIGTSTP|18,20,24| Stop  | Stop typed at terminal

The signals **SIGKILL** and **SIGSTOP** cannot be caught, blocked, or ignored.
