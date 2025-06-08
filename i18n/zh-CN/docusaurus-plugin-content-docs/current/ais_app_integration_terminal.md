---
title: "Terminal web"
sidebar_label: Terminal web
---

## 简介

我们在网关上提供基于Web应用程序的命令行工具，无需通过SSH连接网关即可便捷访问网关终端。

![WEB控制台](/img/en/bramka/web_console.png)

-----------------------------------------------------

## 技术信息

### WebSSH进程

网关进程由[PM2进程管理器](http://pm2.keymetrics.io/)控制。PM2负责在系统启动时运行网关终端的Web应用程序（启动webssh进程），并确保其持续运行。

查看webssh进程状态需在控制台输入：

```
pm2 show webssh
```

![webssh](/img/en/bramka/pm2_webssh.png)

### 程序代码

网关提供的Web控制台功能通过[ttyd](https://github.com/tsl0922/ttyd)实现。

### 仅限本地访问

该终端允许访问**root**账户并拥有系统完全控制权限，因此仅限局域网访问：

![MQTT代理](/img/en/bramka/terminal_local_only.png)