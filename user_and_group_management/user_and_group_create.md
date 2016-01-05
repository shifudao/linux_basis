# 创建用户与用户组

知道了用户的配置文件之后，创建用户的过程其实就是在配置文件中添加新用户信息的过程。

## 手工创建用户

手工创建新用户(以普通用户为例)的过程如下，注意每个用户必须有个主组:

* 创建用户的主组(如果想使用系统中已存在的用户组作为新用户的主组的话，这一步可跳过):
    * 在``/etc/group``文件中按照既定格式添加新主组的信息，由于作为新用户主组，故最后一个``:``后面可空
    * 在``/etc/gshadow``文件中按照既定格式添加新主组的密码信息，密码段可使用``*``或``!``，不允许非组成员切换至该组提权。
* 在``/etc/passwd``文件中按照既定格式添加新用户名,UID,GID(主组),Shell等信息
* 在``/etc/shadow``文件中添加用户的密码信息(``mkpasswd``生成``sha-512``密码串)，**date of last password change** 字段为``0``意味着用户下次登录系统时必须修改密码。
* (可选步骤)创建用户家目录，并赋予相关权限(即使没有家目录，只要有可用shell，用户一样可以登录系统)
* (可选步骤)拷贝``/etc/skel/``目录下所有文件及文件夹(特别注意隐藏文件，可使用``cp -r /etc/skel/. /path/to/user_home/``)，并赋予相关权限

## 工具创建用户

通常使用``useradd``命令添加新用户，Ubuntu可能会包含有另一个支持交互式创建用户的工具``adduser``，这个命令实际上是一个``Perl``脚本，底层对``useradd``命令进行了一次封装。

```
useradd命令基本用法:

Usage: useradd [options] LOGIN
       useradd -D
       useradd -D [options]
```

``useradd``命令会读取一个默认配置文件作为默认行为，未指定的参数将按照配置文件中的设置规则执行，该配置文件根据系统的不同存放路径可能不一样(Ubuntu的useradd默认配置存储于``/etc/default/useradd``)，具体请参考``man useradd``

创建一个普通用户``newuser``，密码永不过期，下次登录无需修改密码，主组和用户名相同，可以用如下命令创建:

    useradd -m -s /bin/bash newuser  # 试根据man手册及--help参数帮助描述这个命令的含义
    echo newuser:mypassword | chpasswd # 修改密码可能更多人第一反应是使用passwd，但passwd不支持非交互模式，故改用chpasswd实现

## 工具创建用户组

``useradd``可以同时添加用户和主组，如果只想添加用户组，不创建相关用户，可以使用``groupadd``命令:

    groupadd mygroup
