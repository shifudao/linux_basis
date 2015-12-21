# 文件的搜索

文件搜索有两种: ``locate``和``find``。

## locate

``locate``是通过文件索引数据库查找的，速度快，但是不具有实时性。

手工更新文件索引数据库可以使用``updatedb``，之后就可以使用``locate filename``来查找文件。

```bash
updatedb
locate filename
```

## find

``find``功能十分强大，属于实时查找，相比``locate``会比较慢，但是拥有更多更强的特性。

```
NAME
       find - search for files in a directory hierarchy

SYNOPSIS
       find [-H] [-L] [-P] [-D debugopts] [-Olevel] [path...] [expression]
```

``find``命令高频参数:

* ``-type``: 指定查找的文件类型，如``f``,``d``,``l``等
* ``-name/-iname``: 指定要查找的文件名，支持**通配符**
* ``-perm``: 指定要查找的文件的mode
* ``-[amc]time``: 指定文件的atime,mtime,ctime
* ``-exec``: 对找出的文件执行外部命令操作

examples: http://www.tecmint.com/35-practical-examples-of-linux-find-command/

几个find的小范例:

```
find /path/to/dir -samefile /path/to/file      # 找出硬链接
find -type f -perm 0777 -print                 # 找出777权限的文件
find ! -name '*.sh' ! -type d                  # 反向匹配
find -inum number                              # inum用于匹配inode，删除怪异文件名的利器
find -size +5M                                 # 找出大于5M的文件
```
