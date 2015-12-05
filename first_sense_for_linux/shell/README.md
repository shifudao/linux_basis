# Shell

## 什么是shell

shell 是一个命令语言解释器（command-language interpreter）。
拥有自己内建的 shell 命令集。此外，shell也能被系统中其他有效的Linux
实用程序和应用程序（utilities and application programs）所调用。

不论何时你键入一个命令，它都被Linux shell所解释。一些命令，比如打印当前工作目录命令（pwd），
是包含在Linux bash内部的（就象DOS的内部命令）。其他命令，比如拷贝命令（cp）和移动命令（rm），
是存在于文件系统中某个目录下的单独的程序。而对用户来说，你不知道（或者可能不关心）
一个命令是建立在shell内部还是一个单独的程序。

![](http://image.360doc.com/DownloadImg/17255/381829_1.gif)

可以说在Linux体系中，Shell的地位崇高。

## Shell的分类

目前流行的shell有ash、bash、ksh、csh、zsh，如下介绍：

* **bash**：bash shell 是 Bourne shell 的一个免费版本，它是最早的 Unix shell，也是很多linux版本默认的shell。
* **csh**：C shell 使用的是“类C”语法，借鉴了 Bourne shell 的许多特点，它由以William Joy为代表的共计47位作者编成，共有52个内部命令。该shell其实是指向/bin/tcsh这样的一个shell，也就是说，csh其实就是tcsh。
* **ksh**：Korn shell 的语法与 Bourne shell 相同，同时具备了 C shell 的易用特点。由Eric Gisin编写，共有42条内部命令。该shell最大的优点是几乎和商业发行版的ksh完全兼容，这样就可以在不用花钱购买商业版本的情况下尝试商业版本的性能了。
* **zsh**：Z shell 是 Korn shell 的一个增强版本，是Linux最大的shell之一，由Paul Falstad完成，共有84个内部命令。如果只是一般的用途，是没有必要安装这样的shell
* **ash**：ash shell是由Kenneth Almquist编写的，Linux中占用系统资源最少的一个小shell，它只包含24个内部命令，因而使用起来很不方便。
* **tcsh**：TC shell 是 C shell 的一个增强版本，与 C shell 完全兼容。

# Shell的执行方式

Shell有两种执行命令的方式：

* **交互式（Interactive）**：解释执行用户的命令，用户输入一条命令，Shell就解释执行一条。
* **批处理（Batch）**：用户事先写一个Shell脚本(Script)，其中有很多条命令，让Shell一次把这些命令执行完，而不必一条一条地敲命令。
