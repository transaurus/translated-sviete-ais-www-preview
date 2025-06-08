---
title: "Biblioteka Spotify"
sidebar_label: Biblioteka Spotify
---

## AIS Spotify集成

与Spotify音乐库的集成使得家庭助理系统能够浏览曲库并在Spotify服务中搜索音频内容。从曲库中选择项目会自动将其推送到网关设备上安装的Spotify播放器。

![Spotify Lib](/img/en/frontend/spotify_lib_2.png)

## Spotify免费版或Premium版

该集成同时支持Spotify免费账户和Premium账户用户。

## 控制网关上的Spotify播放器

**AIS Spotify**集成支持Spotify服务认证及音乐库浏览功能。用户可选择将指定曲目、艺人、专辑或播放列表发送至Spotify播放器。默认情况下，点击选中内容将自动发送至网关内置播放器。

可通过遥控器或家庭助理应用（需配合[AIS Android](/docs/ais_app_android)集成）控制AIS dom网关上的Spotify播放器。

## 遥控器操作

也可通过专用[网络收音机遥控器](/docs/ais_remote_index)启动Spotify搜索。用户可通过[语音指令](/docs/ais_app_assistent_commands)或虚拟键盘配合字母朗读功能进行搜索。

## 分步配置指南

### 1. 前提条件

* 拥有Spotify账户（可免费注册且无需绑定信用卡）：https://www.spotify.com/pl/

* 搭载家庭助理系统的设备

### 2. 登录Spotify应用

:::caution[注意]
需在网关安装的Spotify应用中登录账户，才能将选定内容发送至该应用播放。
:::

* 通过HDMI将设备连接至电视或显示器

* 使用遥控器启用"屏幕控制模式"[遥控器操作模式](/docs/ais_remote_modes)

* 点击图标按钮 -> 选择"Spotify"

![Przejście do Spotify](/img/en/frontend/spotify_settings.jpeg)

* 登录Spotify服务

### 3. 家庭助理Spotify授权

请在网页浏览器中完成以下步骤。

* 通过本地网络访问"家庭助理"网页端[HTTP远程访问网关](/docs/ais_bramka_remote_http)

* 打开***配置*** -> ***集成***

![Konfiguracja Spotify](/img/en/bramka/go_to_integrations.png)

* 启动***AIS Spotify服务***集成配置向导

![Spotify配置](/img/en/frontend/configure_spotify_s2.png)

* 点击"确认"

![Spotify配置](/img/en/frontend/configure_spotify_s2.1.png)

* 登录您在步骤2中使用的同一Spotify账户


* 授权AI-Speaker应用访问Spotify

![Spotify配置](/img/en/frontend/configure_spotify_s3.png)

### 4. AIS Android集成

需要通过额外集成[AIS Android](/docs/ais_app_android)来控制网关上的播放器

## 浏览Spotify音乐库

您可以浏览个人音乐库、查看曲目地址及封面图片

![Spotify音乐库](/img/en/frontend/spotify_lib_2.png)

## 控制Spotify播放器

需添加[AIS Android](/docs/ais_app_android)集成来控制Spotify播放器(Spotify应用)

![跳转至Spotify](/img/en/frontend/spotify_adb.png)