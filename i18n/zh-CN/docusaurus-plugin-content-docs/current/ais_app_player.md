---
title: "Odtwarzacze"
sidebar_label: Odtwarzacze
---

## 内置媒体播放器

设备内置了媒体播放器及媒体资源库。

![AIS Radio](/img/en/frontend/ais_exo_player.png)

媒体内容可通过网关连接的扬声器播放，和/或通过HDMI连接的电视/显示器播放。用户可通过网页浏览器或移动应用远程控制连接电视的网关活动界面，实现流媒体服务或监控摄像头画面的播放。

![AIS Video](/img/en/frontend/video_doorbell2.png)

## AIS附加播放器

家庭助理系统中可添加的AIS附加播放设备包括：

1. 其他搭载家庭助理系统的网关/扬声器
2. 安装免费应用AIS dom的安卓设备

:::info[说明]
安卓设备安装AIS dom应用后，需满足以下条件才能作为附加播放器添加到AIS网关：
1. 需与网关处于同一局域网
2. 在应用设置中启用控制面板特殊功能（如下图所示）
:::

![AIS Radio](/img/en/frontend/panel_special_functions.png)

### 添加播放器至网关

在集成配置中选择**AI Speaker**集成

![AIS Radio](/img/en/frontend/ais_exo_player_add_new.png)

随后填写配置表单并提交

:::info[提示]
播放器局域网IP地址可在AIS dom应用设置中查看：
:::

![AIS Radio](/img/en/frontend/device_ip_in_local_network.png)

![AIS Radio](/img/en/frontend/ais_exo_player_add_new2.png)

配置完成后，家庭助理系统将新增播放器

![AIS Radio](/img/en/frontend/ais_exo_player_add_new3.png)

每个附加播放器均可添加到界面——在视图卡片中布局并自定义显示样式。

![AIS Radio](/img/en/frontend/ais_exo_player_add_new4.png)

## AIS播放器附加功能

### 文本转语音播报

AIS播放器支持文本转语音功能：

![AIS Audio](/img/en/frontend/app_audio_player_tts.png)

### 远程控制

我们可以通过"控制面板"的通知屏幕远程控制网关上的媒体播放器，更多信息请参阅文档《控制面板 - 音频播放器》。

![AIS Radio](/img/en/frontend/ais_exo_mobile.png)

## API接口

与其他集成组件一样，该播放器也开放了服务接口，支持通过[自动化脚本](/docs/ais_bramka_automation)实现播放控制，例如将电台设为闹钟、在指定时间播放特定节目等功能。

![AIS Radio](/img/en/frontend/app_audio_player_api.png)