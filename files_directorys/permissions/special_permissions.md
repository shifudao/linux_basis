# 特殊权限

特殊权限平时较为罕见。一般可能会遇到的特殊权限有以下几类。

## 特殊权限位

除普通权限八进制表示之外，还有一个特殊权限位，也用八进制表示。

  特殊权限名          |       作用
------------------- | ------------------------------------------------
SUID (set user id)  | 针对可执行文件有效，执行时将拥有文件属主的权限(危险权限)
SGID (set group ID) | 如果对可执行文件赋权，执行时将拥有文件属组的权限。如果对目录赋权，则在目录下创建的文件和目录都继承属组权限，并且子目录继承SGID属性。
Sticky bit          | 对可执行文件赋权，则执行完毕之后依旧在内存驻留(但如今几乎没人用这个功能了)。对目录赋权，则只有属主才有权限删除。

* SUID = 4 (100)
* SGID = 2 (010)
* Sticky = 1 (001)

看看典型的特殊权限位的范例:

```bash
$ ls -ld /bin/su /usr/bin/mlocate /var/cache/man /tmp /var/tmp
-rwsr-xr-x  1 root root    36936 Jul 16 03:29 /bin/su
drwxrwxrwt  5 root root     4096 Dec 15 21:46 /tmp
-rwxr-sr-x  1 root mlocate 39520 Jun 20  2013 /usr/bin/mlocate
drwxr-sr-x 28 man  root     4096 Dec 15 21:37 /var/cache/man
drwxrwxrwt  2 root root     4096 Dec 15 20:45 /var/tmp
```

在普通三位八进制数字mode前面追加一个八进制数字即可表示特殊权限位，如:

* ``4755`` = ``rwsr-xr-x``
* ``1777`` = ``rwxrwxrwt``

## chattr设置的特殊权限

chattr可以设置特殊权限，不会被``ls -l``参数列出，可以设置一些mode权限无法实现的权限，如：

* 设定文件不能被删除、改名、设定链接关系
* 只可追加，不可删除
* ... etc ...

``chattr``将在下一小节讲解

## 其他软件控制的权限

其他也有些权限控制的软件，如``SELINUX``和``ACL``。

被SELINUX控制权限的文件会在权限字符串后面加上``.``，如``rwxr-xr-x.``

被ACL控制权限的文件会在权限字符串后面加上``+``，如``rwxrwxrwx+``

还有其他类似的软件。这部分不属于本概要的内容，不做讲解。有兴趣的可以自己找资料了解。

> 关于``ACL``，在我出入行的时候第一份工作中用到过，当时写过一篇文章总结:

> http://wenzhang.baidu.com/page/view?key=b9953e356a9d5efa-1426563912
