# 文本文件的处理

## 查看文本文件

``cat``, ``more``, ``less``, ``head``, ``tail`` ...

## 修改/编辑文本文件

* 使用文本编辑器，终端下常见文本编辑器: ``vim``, ``emacs``, ``nano``

```bash
nano /etc/passwd
vim /etc/services
emacs /etc/sudoers
```

* 使用非交互式脚本处理

```bash
sed -i
```

## 统计文本信息

``wc``: Word Count

    wc /etc/fstab

## 文本处理

* ``cut``: remove sections from each line of files

```bash
$ cut -d: -f1,7 /etc/passwd
```

* ``sort``: sort lines of text files

```bash
$ sort -t: -nk3 /etc/passwd
$ sort -u /tmp/text
```

* ``uniq``: report or omit repeated lines

```
$ sort /tmp/text | uniq
                 `-- 匿名管道，和FIFO不同。后续内容会专门讲解
```

* ``grep``: print lines matching a pattern

```bash
$ grep /bin/bash /etc/passwd
$ grep -v \# /etc/fstab      # 特别注意"#"是bash中的注释字符
```

> 其他常见的文本处理命令: http://tldp.org/LDP/abs/html/textproc.html
