# 后台运行

临时将进程放后台执行可以在命令末尾加上``&``，此时执行的命令将不占用终端，可以继续在当前终端执行别的命令。

如:

```
ping www.baidu.com &
[1] 29901
```

中括号里面的数字代表当前session中job ID，后面的数字代表这个后台job的PID。

使用``jobs``命令可以列出后台job信息，使用``fg``将后台job调度至前台运行。

对已经前台运行的进程可以按下``CTRL-Z``快捷键，或发送``SIGTSTP``信号，将前台进程挂起在后台暂停。
使用``bg``将后台挂起的进程放后台继续执行。

> 更多关于``jobs``命令及相关运用，参考《鸟哥的Linux私房菜》[相关章节](http://linux.vbird.org/linux_basic/0440processcontrol.php#background)

## nohup

当一个shell退出时，系统会对这个shell下所有子进程发送``SIGHUP``信号，进程通常对这个信号的响应为``退出``。

为了让进程不受``SIGHUP``信号的影响长期后台执行，可以告诉进程忽略``SIGHUP``信号，这个命令就是``nohup``。

``nohup``用法也很简单，通常配合``&``一并使用。

    nohub ping www.baidu.com &

此时如果退出终端时(正常或异常断开)，ping命令依旧会后台执行。

> **TIPS**: bash中，也许你体会不到``nuhup``的作用，因为你用了``&``后台执行时，发现即使退出了shell，
> 进程依旧会后台执行。那是因为，bash做了一些特殊处理，默认交互式Shell已经忽略了``SIGHUP``信号，``huponexit off``。
> 但是注意，对于脚本这样就不行了，子进程``SIGHUP``信号干掉了，
> 造成后面的程序不会执行(已经运行的进程不受影响)。这个现象在网上有详细的解答。
> 参考StackOverFlow的[这个问答](http://stackoverflow.com/questions/15595374/whats-the-difference-between-nohup-and-ampersand)，对这个现象做了详细的解释。

如果一个进程已经退出，那么通常它的子进程都会收到``SIGHUP``信号而退出，如果没有退出(例如忽略``SIGHUP``,
或者已经变成僵尸进程``Zombie``)，那么将会被PID为``1``的进程接管，变成这些进程的父进程。

> **TIPS**: 通常干掉僵尸进程的方法就是kill它的父进程

> 关于僵尸进程与孤儿进程的详细介绍，参见[这篇文章](http://www.cnblogs.com/Anker/p/3271773.html)

## 其他后台执行的方法

如果一个程序经常需要后台执行，那么考虑做成后台服务是最合适的了。此内容超出本概要内容，不多讲解。

此外，还有一些简单的方式可以让程序在后台运行，参考IBM的文章:
[Linux 技巧：让进程在后台可靠运行的几种方法](https://www.ibm.com/developerworks/cn/linux/l-cn-nohup/)
