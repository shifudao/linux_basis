# 输入重定向

输入重定向的字符是``<``和``<<``

* ``<``: 代表从其他某一文件接收输入，而不是默认的``/dev/stdin``
* ``<<``: *here-document* 形式重定向, 代表将一段标记为 *here-document* 的文本作为输入

几个典型的 ``<`` 输入重定向演示:

```bash
$ cat < file
$ tr ':' ',' < /etc/passwd
$ sort < file
```

``<<``重定向格式:

```
<<WORD
some lines here
WORD
```

``<<``后面紧跟任意一个单词(单词和``<<``之间无空格)标记document起始, 遇到任意一行以同样单词起始的行会结束(注意这个单词前面不能有任何空格)，
将夹在中间的内容作为输入内容整体作为输入内容传递给命令执行。

```bash
$ cat <<EOF
 First line
Second line
     last line
EOF
```
