---
title: "OwnTracks"
sidebar_label: OwnTracks
---

## 简介

OwnTracks是一款免费开源的iOS和Android应用，可将位置信息直接推送至Home Assistant系统。您可以通过系统配置中的集成功能进行设置，下文将逐步演示具体操作流程。

![存在检测配置](/img/en/bramka/presence_detection_0.png)

## 集成配置

:::tip[提示]
Home Assistant将通过HTTPS接收来自OwnTracks的位置信息。若需在外部网络环境下接收数据，请先[启用网关的互联网访问功能](/docs/ais_bramka_remote_www_index)。
:::

配置OwnTracks需进入系统配置的集成面板，点击右下角橙色"+"按钮打开可用集成列表，选择**AIS存在检测**集成项。

![存在检测配置](/img/en/bramka/presence_detection_1.png)

### 位置上报URL

选择该集成后，您将获得用于移动设备配置的URL（可复制并通过如下方式发送至手机）。

![存在检测配置](/img/en/bramka/presence_detection_2.png)

### Android系统配置

<a href="https://play.google.com/store/apps/details?id=org.owntracks.android" target="_blank">安装Android版OwnTracks应用</a>

在OwnTracks应用中打开侧边栏，点击"偏好设置"→"连接"，修改以下参数：

- 模式：**私有HTTP**

![存在检测配置](/img/en/bramka/presence_detection_3.png)

- 主机：**集成配置时提供的URL地址**

![存在检测配置](/img/en/bramka/presence_detection_4.png)

身份验证：

- 用户名：**您的用户名**
- 设备ID：**您的设备名称**

![存在检测配置](/img/en/bramka/presence_detection_5.png)

### iOS系统配置

<a href="https://itunes.apple.com/us/app/owntracks/id692424691?mt=8" target="_blank">安装iOS版OwnTracks应用</a>

在OwnTracks应用中，点击左上角的(i)图标，然后点击设置。修改以下配置：

- 模式：**HTTP**
- URL：**配置集成时提供的URL地址**
- 启用身份验证
- 用户ID：**您的姓名**

### 系统中的设备标识符

您的设备将自动在家庭助理中被添加为 **device_tracker.您的用户名_您的设备名称**。

![存在检测配置](/img/en/bramka/presence_detection_6.png)

应用内地图将显示移动设备上报的实时位置信息。

![地图上的存在状态显示](/img/en/bramka/presence_detection_7.png)