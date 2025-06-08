---
title: "Bramka z systemem Linux"
sidebar_label: Bramka z systemem Linux
---

import BrowserWindow from '@site/src/components/BrowserWindow';

Linux系统中已安装Home Assistant Supervised。这种安装方式可在Linux操作系统中提供完整的Home Assistant功能，意味着可以使用所有Home Assistant组件和插件。Supervisor不仅是一个应用程序，更是管理整个系统的完整工具。

## Supervisor信息

<BrowserWindow url="http://homeassistant.local:4357">
<center>
![Supervisor](/img/en/linux/supervisor.png)
</center>
</BrowserWindow>

## 通过SSH连接控制器

我们可以通过系统控制台输入以下命令连接Linux系统：

``` bash
ssh root@<IP-BRAMKI>
```

或在网关的Home Assistant终端输入命令通过网页浏览器连接：

``` bash
ssh root@172.17.0.1
```

<BrowserWindow url="http://homeassistant.local:8123">
<center>
![SSH](/img/en/linux/ssh_web.png)
</center>
</BrowserWindow>

这样就能建立从Docker容器（Home Assistant）到Docker宿主机（网关Linux系统）的SSH连接：

<BrowserWindow url="http://homeassistant.local:8123">
<center>
![SSH](/img/en/linux/ssh_web2.png)
</center>
</BrowserWindow>

## 插件

系统预装了以下插件：

- AIS Cloudflared - 远程访问Home Assistant系统
- EMQX - MQTT代理
- File editor - 文件编辑器  
- Terminal & SSH - 系统终端

<BrowserWindow url="http://homeassistant.local:8123">
<center>
![SSH](/img/en/linux/ha_addons.png)
</center>
</BrowserWindow>

这些开箱即用的实用工具可帮助您快速开始工作。

其他插件可通过插件商店安装：

<BrowserWindow url="http://homeassistant.local:8123">
<center>
![SSH](/img/en/linux/ha_addons_store.png)
</center>
</BrowserWindow>