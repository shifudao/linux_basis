# 文件和目录管理

本章将讲解文件和目录的管理内容。

首先先回忆一下``FHS``标准。

> FHS标准官方文档: http://www.pathname.com/fhs/pub/fhs-2.3.html

特别注意一下有两个目录是虚拟文件系统，``/proc``，``/sys``

这两个目录下的文件都不是存储在磁盘上的，是虚拟文件系统。

* ``/proc``: Kernel and process information virtual filesystem
* ``/sys``: sysfs is a virtual file system provided by the Linux kernel that exports information about various kernel subsystems, hardware devices, and associated device drivers from the kernel's device model to user space through virtual files. In addition to providing information about various devices and kernel subsystems, exported virtual files are also used for their configuring.
