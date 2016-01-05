# /etc/gshadow

和``/etc/shadow``类似，组密码的影子文件。

如果用户组有密码时，此文件用于保存用户组密码。但比``/etc/shadow``内容少的多。

```
名称
       gshadow - 影子化了的组文件

描述
       /etc/gshadow 包含影子化了的组账户信息。

       如果没有维护好密码安全，此文件绝对不能让普通用户可读。

       此文件的每行包含逗号分隔的如下字段：

       组名
           必须是系统中已经存在的有效组。

       加密了的密码
           请参考 crypt(3) 来了解关于解析此字符串的细节信息。

           If the password field contains some string that is not a valid result of crypt(3), for instance ! or *, users will not be able to use a unix password to access the group (but group members do
           not need the password).

           此密码用于不是此组成员的用户获取此组的权限。(参考 newgrp(1) )。

           此字段可以为空，此时，只有组成员可以获取组权限。

           以叹号开始的密码字段意味着密码被锁定。该行的剩余字符表示锁定之前的密码。

           此密码取代 /etc/group 中指定的任何密码。

       管理员
           必须是一个逗号分隔的用户名列表。

           管理员可以更改组密码和成员。

           管理员也有成员一样的权限(请看下边)。

       成员
           必须是一个逗号分隔的用户名列表。

           成员可以免密码访问组。

           You should use the same list of users as in /etc/group.
```

> **TIPS**: 组密码和用户密码不一样，并非登录或添加用户到该组时需要的密码

> 一个用户可以有很多组，但必须有且只有唯一一个``主组``，除了``主组``之外的其他组称为``附加组``

> 用户可以用``newgrp``命令修改自己的主组(此命令只是临时变更主组，永久修改需要改``/etc/passwd``)

> 当用户``newgrp``到一个既不是自己的组，也不是自己的附加组时，需要组密码
