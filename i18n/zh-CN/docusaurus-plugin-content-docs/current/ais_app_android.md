---
title: "AIS Android"
sidebar_label: AIS Android
---

## AIS Android 安卓集成

AIS Android集成支持与运行安卓系统的网关及其他安卓设备（如电视、手机、平板、智能手表、车载播放器、电视盒子等）进行通信。

:::caution[注意]
**与其他安卓设备的集成**

该集成通过[Android ADB TCP/IP](https://developer.android.com/studio/command-line/adb)接口进行通信。并非所有安卓设备都像网关那样能轻松启用ADB接口，也并非所有设备都能完整支持ADB通信协议。
:::

当前该集成主要用于控制网关上的Spotify播放器：

![Spotify](/img/en/frontend/spotify_adb.png)