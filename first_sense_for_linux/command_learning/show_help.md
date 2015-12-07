# 查看命令帮助

## 内建(built-in)命令与外部命令

Shell自带的命令程序即为内建(built-in)命令，使用``help``即可列出所有内建命令

除此之外，由其他外部程序或函数提供的命令即为外部命令。

使用``type COMMAND``可以查看命令类型

```bash
$ type cat
cat is /bin/cat

$ type cd
cd is a shell builtin

$ func() {
echo hello world
}

type func
func is a function
func ()
{
   echo hello world
}
```

## 内建命令帮助

使用``help COMMAND``的形式即可，如``help cd``

## 外部命令帮助

大多数外部命令都有带有帮助参数，通常为``-h``|``--help``。

```bash
$ cat --help
Usage: cat [OPTION]... [FILE]...
Concatenate FILE(s), or standard input, to standard output.

  -A, --show-all           equivalent to -vET
  -b, --number-nonblank    number nonempty output lines, overrides -n
  -e                       equivalent to -vE
  -E, --show-ends          display $ at end of each line
  -n, --number             number all output lines
  -s, --squeeze-blank      suppress repeated empty output lines
  -t                       equivalent to -vT
  -T, --show-tabs          display TAB characters as ^I
  -u                       (ignored)
  -v, --show-nonprinting   use ^ and M- notation, except for LFD and TAB
      --help     display this help and exit
      --version  output version information and exit

With no FILE, or when FILE is -, read standard input.

Examples:
  cat f - g  Output f's contents, then standard input, then g's contents.
  cat        Copy standard input to standard output.

Report cat bugs to bug-coreutils@gnu.org
GNU coreutils home page: <http://www.gnu.org/software/coreutils/>
General help using GNU software: <http://www.gnu.org/gethelp/>
Report cat translation bugs to <http://translationproject.org/team/>
For complete documentation, run: info coreutils 'cat invocation'
```

### 帮助手册

帮助参数打印的帮助信息通常较为简略，有时需要更详细的帮助说明。此时可以借助翻阅帮助手册。

打开帮助手册的命令为``man``，使用``man PAGE``的基本形式即可查阅文档。

    man find

man手册有“章节”的概念，不同“章节”区分不同的帮助类型。以下表格简单罗列了章节信息。

section|description
-------|-----------
  **1**| **User Commands**
    2  | System Calls
    3  | C Library Functions
    4  | Devices and Special Files
  **5**| **File Formats and Conventions**
    6  | Games et. Al.
    7  | Miscellanea
  **8**| **System Administration tools and Deamons**

对应的帮助文档存放于``/usr/share/man/man[sectionID]/*.gz``

使用``whatis PAGE``即可查看要查询的PAGE有哪些对应章节

> **NOTE**: 查询文件帮助时不要跟绝对路径。如: ``man apt.conf``

比``man``更详细的帮助手册 —— ``info``
