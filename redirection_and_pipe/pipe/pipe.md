# 匿名管道

使用``pipe(man 2 pipe)``函数(``C``函数)或``|``即可创建匿名管道，由于使用频率实在太高，通常``管道``不特别说明，
都指的是``匿名管道``，甚至``|``符号本身也常称为``管道符``。

管道的用法很简单，用管道符``|``将多个命令连接即可:

    COMMAND1 | COMMAND2 [| COMMANDn]...

举几个范例:
```bash
# 只显示当前目录下前10个文件
$ ls | head

# 将标准输出不但输出到文件，也打印到终端
$ ls | tee files_list

# 获取当前主机的非环回ip
$ ifconfig | grep 'inet addr' | cut -d: -f2 | cut -d' ' -f1 | grep -v 127.0.0.1

# 找出shell为/bin/bash的用户，并将结果保存至user_list文件
$ grep /bin/bash /etc/passwd | cut -d: -f1 > user_list

# 统计当前目录下所有文件/文件夹的容量，并列出前10个容量最大的文件/文件夹
$ du -s * | sort -nr | head
```

匿名管道有几个特点:

* 管道连接的几个命令是并行执行的，而不是串行
* 管道中有任意一个命令退出时，整个管道连接的所有命令将全部退出
* 管道的退出码是最后一条命令的退出码

## find的好基友——xargs

``xargs``算是和find搭档最多的命令了。

```
NAME
       xargs - build and execute command lines from standard input

SYNOPSIS
       xargs [-0prtx] [-E eof-str] [-e[eof-str]] [--eof[=eof-str]] [--null] [-d delimiter] [--delimiter delimiter] [-I replace-str] [-i[replace-str]] [--replace[=replace-str]] [-l[max-
       lines]]  [-L  max-lines]  [--max-lines[=max-lines]]  [-n  max-args]  [--max-args=max-args]  [-s  max-chars]  [--max-chars=max-chars]   [-P   max-procs]   [--max-procs=max-procs]
       [--interactive] [--verbose] [--exit] [--no-run-if-empty] [--arg-file=file] [--show-limits] [--version] [--help] [command [initial-arguments]]
```

``xargs``主要解决了这样的问题——如果给命令传递的参数过多，超出了bash的限制，将重新构建参数(主要是切割参数循环执行)

find和xargs常常以这样的方式结合使用:

    find [表达式] -print0 | xargs -0 [COMMAND [ARGS]]

``xargs``常用参数:

* ``-0``: 与``find -print0``搭配使用绝佳,指定``\0``为参数分隔符
* ``-L n``: 指定最大接受行数为``n``，超过``n``行的参数将被切割
* ``-n n``: 指定每行参数的最大数量为``n``
* ``-I replace-str``: 指定参数占位符为``replace-str``,如: ``xargs -I '{}' mv '{}' /tmp/``
