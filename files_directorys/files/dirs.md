# 目录的操作

## 创建目录

    mkdir dir
    mkdir -p /tmp/dir1/dir2/dir3

## 列出目录内容

    ls [-R] /path/to/dir
    tree [/path/to/dir]

## 拷贝目录

    cp -r dir1 dir2

## 删除目录

    rmdir dir
    rmdir -p /tmp/dir1/dir2/dir3
    rm -fr /path/to/delete

> Warning: **rm** 十分危险，几乎能删除任何你想删掉的文件，被``rm``删掉的文件很难找回。

> 特别提醒，尤其是``-r -f``参数连用的时候需谨慎，且用且珍惜！

## 移动/重命名目录

    mv /path/to/dir1 /path/to/dir2

灵活使用展开式可以在批量创建/删除目录时事半功倍:

    mkdir -p /tmp/dir{1..9}/stores{a..z}  # 猜猜看，这个结果是什么？
