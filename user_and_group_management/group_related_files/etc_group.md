# **/etc/group**

该文件存储用户组名，``GID``，以及用户对应关系等信息。

字段也比``/etc/passwd``少。

```
NAME
       group - user group file

DESCRIPTION
       The /etc/group file is a text file that defines the groups on the system.  There is one entry per line, with the following format:

              group_name:password:GID:user_list

       The fields are as follows:

       group_name  the name of the group.

       password    the (encrypted) group password.  If this field is empty, no password is needed.

       GID         the numeric group ID.

       user_list   a list of the usernames that are members of this group, separated by commas.
```

试描述以下``/etc/group``内容是什么含义：

```
adm:x:4:syslog,sinoiot
landscape:x:106:
sinoiot:x:1000:
admin:x:107:sinoiot
mlocate:x:108:
```
