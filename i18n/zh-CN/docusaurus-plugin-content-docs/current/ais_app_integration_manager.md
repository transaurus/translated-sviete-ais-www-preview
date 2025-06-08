---
title: "Menedżer plików"
sidebar_label: Menedżer plików
---

## 简介

我们在网关上提供基于网页应用的文件管理器。该文件管理器包含文本编辑器及文件预览功能（支持文本、音频、视频）。通过浏览器应用，您可以在任意电脑、手机或平板上管理网关中的文件和目录。

![WEB cmd](/img/en/bramka/web_cmd.png)

:::caution[注意]
**文件管理器**应用预装在系统版本为**Leon**及后续版本的网关上。早期版本网关用户可参照[AI-Speaker论坛指南](https://ai-speaker.discourse.group/t/ais-commander/2312)自行安装该应用。
:::

-----------------------------------------------------

## 技术信息

### webcmd进程

网关进程由[PM2进程管理器](http://pm2.keymetrics.io/)控制。PM2负责在系统启动时运行网关终端网页应用（即启动webssh进程），并持续监控其运行状态。

查看webcmd进程状态需在控制台输入：

```
pm2 show webcmd
```

![webssh](/img/en/bramka/web_cmd_pm2.png)

### 代码实现

文件管理功能由[AIS-webcmd](https://github.com/sviete/AIS-webcmd)应用实现。该应用同时以npm包形式发布在仓库中：

![MQTT broker](/img/en/bramka/web_cmd_npm.png)

### 仅限本地访问

该控制台具有**root**账户权限，可执行系统所有操作。因此仅开放局域网访问权限：

![MQTT broker](/img/en/bramka/ttyd_local_only.png)