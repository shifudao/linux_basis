# 别名

别名用于简化某些常用的命令及参数。

列出当前使用的别名:

    alias

定义一个别名:

    alias new_alias="command args"

如: ``alias vi=vim``, ``alias cdl="cd -"``

比如我定义的alias：

```bash
alias mysql='docker run -it --rm mysql mysql'
alias mongo='docker run -it --rm mongo mongo'
alias psql='docker run -it --rm postgres psql'
```

想要永久生效将``alias``命令写入``~/.bashrc``中即可。
