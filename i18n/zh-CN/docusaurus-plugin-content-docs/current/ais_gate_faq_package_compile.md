---
title: "Własny pakiet do systemu Linux"
sidebar_label: Własny pakiet do systemu Linux
---

## 设备上的Linux运行环境

我们为设备提供了终端模拟器和一套可在控制台运行的程序（专为设备处理器架构编译的二进制文件，并考虑了环境前缀）。
我们的系统与Android共享Linux内核。这使得我们能够同时在一台设备上享受Android的多媒体功能、文本shell接口以及带有额外二进制文件的APT软件仓库。
这是一个完整的Linux环境，但与传统发行版有一个主要区别——我们的环境带有前缀。
带前缀的环境（prefixed environment）意味着目录结构与经典发行版略有不同——例如Ubuntu使用/bin，而AIS-linux使用$PREFIX/bin，其中$PREFIX在我们的案例中指向/data/data/com.termux/files/usr。

![](/img/en/bramka/faq_linux_package_compilation_1.png)

## 软件包编译

前缀会影响软件包的安装和编译过程。在创建我们的发行版时，我们参考了Termux——我们是其分支。
软件包编译过程与Termux相同（参见https://wiki.termux.com/wiki/Main_Page），我们在Docker容器中完成编译（https://github.com/sviete/AIS-linux-packages），然后将软件包放入仓库https://github.com/sviete/DOM-APT-REPO

### 将编译好的软件包添加到AIS-linux仓库

如果您希望您的二进制文件能被纳入我们的AIS-linux仓库（以便通过apt包管理器安装），推荐的方式是向Termux提交pull request

https://github.com/termux/termux-packages

通过这种方式，您的组件将经过数百名开发者和数千名用户的审查测试，最终会随着Termux的最新软件包版本正式进入家庭助理系统。