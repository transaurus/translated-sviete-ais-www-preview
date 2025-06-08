---
title: "Ustawienia systemu"
sidebar_label: Ustawienia systemu
---

## Android系统设置

要进入Android系统设置，只需从`屏幕控制菜单`中选择Android选项：

![Android设置](/img/en/bramka/settings_1.png)

![设置](/img/en/bramka/settings_2.png)

## "家庭助理"应用控制台

要进入Android系统设置，只需从`屏幕控制菜单`中选择控制台选项：
控制台提供Linux环境，包含基础最小系统及Python解释器、Node.js和Clang

![设置](/img/en/bramka/settings_6.png)

额外软件包可通过APT包管理器从我们的Ais Linux软件仓库获取。

![设置](/img/en/bramka/settings_3.png)

网关进程由PM2进程管理器控制。
PM2负责管理"家庭助理"系统中的服务状态，系统启动时由PM2拉起进程并持续监控其运行状态。

要查看"家庭助理"系统服务日志，请在网关控制台执行命令：

```bash
$ pm2 logs
```

默认用户仅对/data/data/com.termux/files目录具有权限（该目录存放Linux系统软件包），以及对data/data/com.termux/files/home/AIS子目录具有权限（该目录存放"家庭助理"系统配置）。

:::caution[注意]
开发者版本网关还提供**root**用户权限，可访问整个系统。
:::