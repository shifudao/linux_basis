# Bash

## Bash简介

bash，全称为Bourne-Again Shell。它是一个为GNU项目编写的Unix shell。
bash是绝大多数Linux发行版默认的Shell，Google的shell脚本规范甚至就指明必须使用bash。

**我们后面的内容，如无特殊说明，均以``Bash``作为Shell。**

## Bash的命令提示符

默认情况下，Bash的命令提示符像是这样:

```bash
sinoiot@linuxteaching:~$
  |             |     |
当前登录用户名  主机名  当前目录
```

或是这样:

```bash
root@linuxteaching:~#
```

其中，``$``代表当前用户身份为普通用户，``#``代表当前用户身份为超级用户。

> 看到这样的提示符之后，就可以开始Surfing Linux

## 元字符

bash中存在一些``元字符``，使用时特别注意处理这些元字符。后续内容会逐步提到解释元字符的用途。

常见的元字符如下:

空白符(空格,tab等)，``\``,``$``，``&``，``|``，\`(着重号或反引号) ，引号(单引号和双引号)，
括号(包括小括号，中括号和大括号)，
