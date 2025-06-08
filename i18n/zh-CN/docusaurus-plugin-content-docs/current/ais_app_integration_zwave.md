---
title: "Zwave"
sidebar_label: Zwave
---

## 简介

Zwavejs集成使您无需使用制造商网关即可在智能家居系统中使用Zwave设备。该解决方案基于[ZwaveJs2Mqtt](https://github.com/zwave-js/zwavejs2mqtt)项目开发，可将Zwave设备接入运行AI-Speaker系统的智能家居基础设施。

### <span class="mdi mdi-professional-hexagon"></span> PRO网关

在AIS PRO <span class="mdi mdi-professional-hexagon"></span>网关上，Zwavejs集成已默认安装并配置完成。

![Zwave](/img/en/frontend/zwave_control_panel_dark.png)

### <span class="mdi mdi-dev-to"></span> DEV网关

对于DEV网关，Zwave集成需要手动安装。完整操作指南详见AI-Speaker论坛：[在AIS网关上使用Zwave - Zwavejs2Mqtt](https://ai-speaker.discourse.group/t/zwave-na-bramce-ais-zwavejs2mqtt/1769)

![Zwave](/img/en/frontend/zwave_dev_integration.png)

## Zwave集成

本集成已通过市场主流适配器Aeotec Z-Stick测试验证，该设备采用USB CDC（通信设备类）协议进行通信。

![Zwave](/img/en/frontend/zwave_adapter.jpeg)

通过ZwaveJs2Mqtt支持的TCP socket远程连接，本集成也可兼容不支持USB CDC协议的适配器：

```
 tcp://dongle.lan:5000
```

## 支持的设备

我们支持所有Zwavejs2Mqtt兼容设备，更多信息请参阅[ZwaveJs2Mqtt项目页面](https://zwave-js.github.io/zwavejs2mqtt/#/)。

### 网络拓扑图

可刷新Zwave网络拓扑页面查看已接入网关的设备

![Zigbee集成](/img/en/frontend/zwave_mesh_diagram.png)

-----------------------------------------------------

## 技术信息

### Zwave进程

网关进程由[PM2进程管理器](http://pm2.keymetrics.io/)控制。PM2会在检测到Zwave设备（Aeotec Z-Stick适配器）后启动zwave进程，并持续监控其运行状态。

查看zigbee进程状态可通过控制台输入：

```
pm2 show zwave
```

![zwave](/img/en/frontend/pm2_zwave.png)

### 本地网络访问

Zwavejs2MQTT应用运行在本地网络**8091**端口，可直接通过浏览器访问``http://<网关IP>:8091``

![Zwavejs2MQTT](/img/en/frontend/app_zwavejs2mqtt.png)

### 配置访问

所有ZwaveJs2Mqtt的配置均可通过网页应用完成。
目前我们暂不支持将Zwave配置文件上传至AIS服务或在网关间复制配置。
可通过控制台或ZwaveJs2Mqtt应用程序备份配置文件（即``~/zwavejs2mqtt/store``目录内容）。

![Zwavejs2MQTT](/img/en/frontend/zwave_configuration.png)