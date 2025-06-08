---
title: "Serwer FTP"
sidebar_label: Serwer FTP
---

## 简介

我们在网关上提供FTP服务器，通过FTP通信协议实现网关与局域网内其他计算机之间的便捷文件传输。

![FTP服务器](/img/en/bramka/ftp_server.png)

-----------------------------------------------------

## 技术信息

### FTP进程

网关进程由[PM2进程管理器](http://pm2.keymetrics.io/)控制。
PM2还负责在系统启动时运行FTP服务器，并持续监控其运行状态。

查看FTP进程状态需在控制台输入：

```
pm2 show ftp
```

![webssh](/img/en/bramka/pm2_ftp.png)

### 二进制文件

FTP服务器基于[busybox](https://busybox.net/)构建

我们将编译好的busybox二进制包存放在[bintray仓库](https://bintray.com/sviete/ais/ttyd)

![MQTT代理](/img/en/bramka/busybox_binary.png)

### 仅限本地访问

该FTP服务器仅支持匿名登录——不进行任何身份验证。因此FTP访问仅限于局域网内。