# Bash组合键

``Bash``有一些快捷组合键，灵活使用这些组合键可以让命令行操作事半功倍。

常用的快捷键:

## 移动光标

* `alt+b`: 前移一个单词
* `alt+f`: 后移一个单词
* `ctrl+a`: 移到行首（a是首字母）
* `ctrl+e`: 移到行尾（end）
* `ctrl+x`: 行首到当前光标替换

## 编辑命令
* `alt+.`: 粘帖最后一次命令最后的参数（通常用于`mkdir long-long-dir`后, `cd`配合着`alt+.`）
* `ESC, .`: 同上
* `alt+d`: 删除当前光标到临近右边单词开始
* `ctrl+w`: 删除当前光标到临近左边单词结束
* `ctrl+u`: 删除光标左边所有
* `ctrl+k`: 删除光标右边所有
* ***`ctrl+l`: 清屏(相当于``clear``命令)***
* `ctrl+shift+c`: 复制（相当于鼠标左键拖拽）
* `ctrl+shift+v`: 粘贴（相当于鼠标中键）

## 其它

* `shift+PageUp`: 向上翻页
* `shift+PageDown`: 向下翻页
* ***`ctrl+r`: 进入历史查找命令记录， 输入关键字。 多次按返回下一个匹配项***
* ***`ctrl+c`: 发送``Interrupt``信号，常用于取消未输入完整的命令，或中断当前正在执行的命令***
* ***`ctrl+d`: 发送``EOF``信号，常用于登出交互式shell，或结束``STDIN``***
* `ctrl+z`: 给当前正在运行的命令发送``SIGTSTP``，将导致被后台挂起

> 全部组合键参见: http://ss64.com/bash/syntax-keyboard.html
