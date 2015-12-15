# 修改权限

## mode修改

使用命令``chmod``即可搞定。

``chmod``用法也很简单，可以使用+-字符的形式，也可以使用八进制数字形式。

字符形式表示:

u=user, g=group, o=other, a=all，``+``代表增加权限，``-``代表减去权限，``=``代表覆盖权限。

可以用``,``分割多个模式。

例如:

给属主增加``w``权限:

    chmod u+w file

给属组去掉``x``权限:

    chmod g-w file

给ugo都增加``r``权限: ``ugo+r``或``a+r``

增加SUID权限: u+s

用八进制表示:

    chmod 755 file

``-R``参数可以递归:

    chmod -R o-r /path/to/dir

## chattr / lsattr

``chattr``用于给文件设置特殊属性，``lsattr``用于列出这些特殊属性。

chattr有两个比较常见的特殊属性:

* a: A file with the `a' attribute set can only be open in append mode for writing.  Only the superuser or a process possessing the CAP_LINUX_IMMUTABLE capability can set or clear this attribute.
* i: A file with the `i' attribute cannot be modified: it cannot be deleted or renamed, no link can be created to this file and no data can be written to the file.  Only the superuser or a  process  possessing the CAP_LINUX_IMMUTABLE capability can set or clear this attribute.


    chattr +i file      # 增加i属性
    chattr -i file      # 去掉i属性

## 变更属主，属组

使用``chown``变更属主，``chgrp``变更属组。

```bash
# chown [-R] user:group file 
```
