# Bash特性——补全与展开

## 补全

Bash补全的按键是``<TAB>``，可以实现``命令``与``路径``的补全。

> **NOTE**: 参数的补全并非Bash自带功能，而是由``/etc/bash_completion.d/``

> 下对应的脚本实现的。

基本用法:

* 命令补全

```bash
$ bat<TAB>    # 唯一补全结果会立刻补全
$ batch

$ ba<TAB><TAB>    # 非唯一补全结果需要按两下<TAB>，同时显示结果是可用补全列表
badblocks  base64     basename   bash       bashbug    batch
```

* 路径补全

```bash
# 和上面的效果一样，唯一补全会立刻补全，非唯一需要按两下<TAB>，显示补全列表
$ ls /t<TAB>
$ ls /tmp/

$ ls /etc/b<TAB><TAB>
bash.bashrc             bash_completion         bash_completion.d/      bindresvport.blacklist  blkid.conf              blkid.tab
```

当可用补全列表太多超过一个屏幕时，Bash会像这样显示:

```bash
$ ls  /usr/lib/python2.7/
Display all 442 possibilities? (y or n)
```

此时按``y``确认显示补全列表时，末尾看起来像是这样:

```bash
... etc ...
cmd.pyc                  dummy_thread.pyc         imputil.pyc              ntpath.py                pydoc.pyc                sre_compile.py           threading.pyc            xmlrpclib.pyc
codecs.py                email/                   inspect.py               ntpath.pyc               _pyio.py                 sre_compile.pyc          timeit.py                zipfile.py
codecs.pyc               encodings/               inspect.pyc              nturl2path.py            _pyio.pyc                sre_constants.py         timeit.pyc               zipfile.pyc
--More--
```

最后一行显示``--More--``，代表还有剩余的补全结果。

此时按回车键``ENTER``可以继续向下显示一行，按空格键``SPACE``可以显示一页，直到全部结果显示完整。

## 展开式

Bash的``{}``表达式内的部分也会像``通配符``一样，被Bash自解释。
``{}``展开效果非常类似于数学公式中的多项式积。

自己试试看，下面的结果是什么?

```bash
$ echo {a-z}
$ echo {a,z}
$ echo {a.z}
$ echo {a..z}
$ echo {0-9}
$ echo {0,9}
$ echo {0..9}
$ echo {a,b}{c,d}
$ echo \{a,b}{c,d}
$ echo "{a,b}{c,d}"
```

**总结**: 和通配符一样，展开式也会先被Bash自解释之后，将解释过后的结果作为参数传递给命令。
通配符和展开式可以结合使用。

想想看，下面的结果代表什么？

    /usr/{ucb/{ex,edit},lib/{ex?.?*,how_ex}}
