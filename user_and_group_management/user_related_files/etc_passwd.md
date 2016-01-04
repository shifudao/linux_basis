# **/etc/passwd**

**重要文件，几乎相关认证考试必考！**

每个用户对应一个``UID``，该文件将存储用户的``UID``,``GID``,``Shell``等配置信息。

使用``man 5 passwd``查看该文件的配置语法。

```
NAME
       passwd - the password file

DESCRIPTION
       /etc/passwd contains one line for each user account, with seven fields delimited by colons (“:”). These fields are:

       ·   login name

       ·   optional encrypted password

       ·   numerical user ID

       ·   numerical group ID

       ·   user name or comment field

       ·   user home directory

       ·   optional user command interpreter
```

根据man手册的帮助说明，试描述下面的``passwd``行内容代表什么意思：

```
mail:x:8:8:mail:/var/mail:/usr/sbin/nologin
sinoiot:x:1000:1000:sinoiot,,,:/home/sinoiot:/bin/bash
```

> **TIPS**:
> * ``UID``是唯一标识一个用户的(主键)，并非用户名(特别注意!)，猜一下，如果将一个普通用户的UID改为``0``，将会发生什么？
> * ``UID``数字较小的部分(RedHat 500以内，Debian/Ubuntu 1000以内，通常定义在``/etc/login.defs``文件中的``MIN_UID``变量)通常代表系统账户，往往不能登录系统，但比普通用户拥有更多权限，一般仅供某些服务使用。
> * ``/etc/passwd``文件通常不建议手工修改，基本上每个字段都有对应的命令去修改，建议使用对应的命令修改。
