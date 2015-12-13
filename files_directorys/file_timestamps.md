# 文件的时间戳

## 查看时间戳

用``stat``命令可以查看文件的时间戳

```bash
$ stat /tmp/file
File: ‘file’
Size: 0         	Blocks: 0          IO Block: 4096   regular empty file
Device: fd01h/64769d	Inode: 2228469     Links: 1
Access: (0644/-rw-r--r--)  Uid: (    0/    root)   Gid: (    0/    root)
Access: 2015-12-13 17:21:52.117050496 +0800
Modify: 2015-12-13 17:21:52.117050496 +0800
Change: 2015-12-13 17:21:52.117050496 +0800
Birth: -
```

文件共有3个时间戳，``Access time``(atime), ``Modify time``(mtime), ``Change time``(ctime)。

``Birth time``(创建时间)在Linux中已经废弃，目前一般都是``-``。

这里重点比对一下``Modify``和``Change``:

* ``Modify``: 表示文件内容被修改的时间
* ``Change``: 表示文件被修改的时间(包括内容和元数据)

## 修改时间戳

``touch``命令即可修改元数据中的时间戳:

```bash
$ touch file     # 将Access, Modify, Change均修改为当前时间
$ touch -a file  # 试试看?
$ touch -m file  # 试试看?
```

想想看，为什么没有针对``Change``的修改选项？
