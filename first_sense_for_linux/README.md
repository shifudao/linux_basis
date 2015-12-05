# 初识Linux

## Linux的概念

什么叫Linux？

> Linux只是一组拥有GUN/Linux内核操作系统的统称

> 严格来讲，Linux只是操作系统内核的名字。官网: [kernel.org](https://www.kernel.org/)

## Linux系统的基础架构

和大多数操作系统并无太大区别，下图简单的描述了Linux系统:

![](http://www.2cto.com/uploadfile/Collfiles/20140106/201401060837277.jpg)

内核、shell和文件系统一起形成了基本的操作系统结构，它们使得用户可以运行程序、管理文件并使用系统。文件系统和内核是彼此依赖的，可以把内核简单的理解成执行单元，文件系统是存储单元。Linux内核中，跟文件系统相关的组件如下图所示：

![](http://www.2cto.com/uploadfile/Collfiles/20140106/201401060837279.jpg)

## 什么是Linux发行版(Distrobution) ?

前面提过，Linux只是系统内核，负责和硬件打交道。同时，Linux是自由软件，允许任何个人和组织
基于GPL协议进行定制和开发。于是就涌现出很多组织或个人使用Linux为基础，在上层进行打包或定制后进行分发，
从而形成一个完整可用的“操作系统”。这个完整的操作系统称为“发行版(distrobution)”，拥有自己的版本号，
组织或个人对发行版享有命名的权利。如常见的``Fedora``，``Debian``，``Ubuntu``，``CentOS``
等等，都是“发行版”的名字。它们使用的内核都是``Linux``，固使用``Linux``做广义上Linux发行版的统称。

![](http://futurist.se/gldt/wp-content/uploads/12.10/gldt1210.png)
