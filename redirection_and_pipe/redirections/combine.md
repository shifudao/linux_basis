# 结合使用

输入重定向与输出重定向可以在一起使用，实现从文件/here-document接受输入，输出到指定文件的功能。

比如将``/etc/passwd``文件转换成为``CSV``格式:

```bash
$ tr ':' ',' < /etc/passwd > passwd_csv
```

在终端直接创建一个带有部分内容的文本文件(**脚本常用**):

```bash
$ cat <<EOF > myfile
This is the first line.
And this is the last line.
EOF
```

> **NOTE**: 重定向的``>``,``<``和顺序无关，上面两个范例，你完全可以将大于号和小于号对调过来写。如: ``tr ':' ',' > passwd_csv < /etc/passwd``
