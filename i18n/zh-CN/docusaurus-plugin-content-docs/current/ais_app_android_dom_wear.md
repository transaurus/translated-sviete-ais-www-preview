---
title: "AIS dom Wear OS"
sidebar_label: AIS dom Wear
---

## 简介

AIS dom Wear OS 是一款独立运行（无需依赖手机应用）的应用程序，可在搭载 Wear OS 系统的设备上运行。

![Wear OS](/img/en/blog/202009/wear_os_1.jpeg)

## 手表端安装

该应用在 [Google Play](https://play.google.com/store/apps/details?id=pl.sviete.dom) 商店免费提供（无广告、内购等），搜索名为 AIS dom 即可下载。

<center>

![Google Play](/img/en/frontend/barcode_go_to_apk_in_google_play.png)

![Google Play](/img/main/google-play-badge.png)

</center>

应用源代码可在我们 [公开的代码仓库](https://github.com/sviete/AIS-dom-wear) 获取
已签名的版本也会发布在我们的 [系统组件服务站点](https://powiedz.co/ota/)

## 与网关集成

### 网关端集成向导

在网关上启动集成向导即可开始集成流程。

![Wear OS](/img/en/frontend/wear_os_wiz_1.png)

随后按照分步引导完成简单配置：

![Wear OS](/img/en/frontend/wear_os_wiz_2.png)

![Wear OS](/img/en/frontend/wear_os_wiz_3.png)

![Wear OS](/img/en/frontend/wear_os_wiz_4.png)

![Wear OS](/img/en/frontend/wear_os_wiz_5.png)

### 在手表应用中输入PIN码

首次启用手表应用时，需输入网关添加集成时生成的一次性PIN码。

<center>

![Wear OS](/img/en/frontend/wear_os_wiz_6.png)

</center>

:::caution[注意]
PIN码仅在2分钟内有效。若错过时间窗口未在手表输入，请重新执行 **AIS Wear OS** 集成流程。
:::

在手表端输入并确认PIN码后

<center>

![Wear OS](/img/en/frontend/wear_os_wiz_7.png)

</center>

将显示已连接网关的标识信息，并自动跳转至应用主界面

<center>

![Wear OS](/img/en/frontend/wear_os_wiz_8.png)

</center>

## 应用使用

### 语音指令

首次点击麦克风图标时，将弹出麦克风权限请求

<center>

![Wear OS](/img/en/frontend/wear_os_wiz_10.png)

</center>

授予权限后，即可向AIS dom网关发送语音指令。

### 与网关同步

可启用与网关的同步功能，允许网关向手表应用发送请求。其工作机制类似于网关向手机应用发送指令的方式

<center>

![Wear OS](/img/en/frontend/wear_os_wiz_11.png)

</center>

:::info[信息]
最终我们将定期从手表向网关发送报告（心率、活动数据等），与移动应用的功能类似。
:::