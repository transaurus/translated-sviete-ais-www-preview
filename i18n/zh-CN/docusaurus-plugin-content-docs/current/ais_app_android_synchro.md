---
title: "AIS synchro"
sidebar_label: AIS synchro
---

AIS synchro 是一款用于在本地磁盘与云存储之间同步文件和目录的应用程序。

<img src="/img/en/frontend/ais_synchro_apk_screen.png" width="360" align="right" />

该应用内置了命令行工具 **Rclone** 的二进制程序。
我们曾通过该应用为智能家居助手添加远程磁盘功能，直至我们将此功能迁移至网页应用，并将 rclone 二进制程序移至我们的 [apt软件包仓库](http://powiedz.co/apt/)。该应用程序可在 [Google Play](https://play.google.com/store/apps/details?id=pl.sviete.dom.rcloneexplorer) 获取。

未来我们计划扩展本地磁盘与云存储的同步功能，实现系统设置的自动备份。[Rclone](https://rclone.org/) 二进制程序为我们提供了支持数十种云存储的API接口。

源代码发布于我们的 [公开代码仓库](https://github.com/sviete/AIS-synchro)

已签名的测试版发布在我们的 [系统组件服务站点](https://powiedz.co/ota/)