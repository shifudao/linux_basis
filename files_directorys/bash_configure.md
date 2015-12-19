# bash配置文件

Bash相关的配置文件:

* ``/etc/profile``: The systemwide initialization file, executed for login shells
* ``/etc/bash.bashrc``: The systemwide per-interactive-shell startup file
* ``/etc/bash.bash.logout``: The systemwide login shell cleanup file, executed when a login shell exits
* ``~/.bash_profile``: The personal initialization file, executed for login shells
* ``~/.bashrc``: The individual per-interactive-shell startup file
* ``~/.bash_logout``: The individual login shell cleanup file, executed when a login shell exits
* ``~/.inputrc``: Individual readline initialization file

> 关于这些配置文件加载详细说明，参见GNU Bash文档: [Bash-Startup-Files](https://www.gnu.org/software/bash/manual/html_node/Bash-Startup-Files.html)

> 关于Bash启动时加载的配置文件顺序，参见: https://shreevatsa.wordpress.com/2008/03/30/zshbash-startup-files-loading-order-bashrc-zshrc-etc/

几个常用的变量:

* ``SEHLL``: 显示当前的Shell
* ``PATH``: 不加绝对路径时,查找命令的路径
* ``USER``: 显示当前用户
* ``PWD``: ``pwd``命令显示的东西
* ``HISTFILESIZE``: ``history``记录多少条历史命令
* ``PS1-4``: 交互登录式Shell的命令提示符
