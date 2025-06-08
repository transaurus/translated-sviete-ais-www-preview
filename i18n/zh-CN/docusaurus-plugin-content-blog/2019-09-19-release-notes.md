---
author: Jola AI-Speaker
authorURL: https://github.com/sviete
authorImageURL: https://avatars3.githubusercontent.com/u/43966761?s=460&v=4
title: Wersja systemu 0.98.9 Tryb nocny, start autoaktualizacji
---

## 2019年9月19日发布的系统版本0.98.9

## 夜间模式

我们在网关设置中新增了自动启用夜间模式的功能。

![AIS dom Tryb nocny](/img/en/blog/ais_dom_dark_mode.gif)

<!--truncate-->

当"启用夜间模式"后，系统将在设定的夜间模式启动时间自动执行以下操作：

- 将通知朗读音量降低至20%
- 将音频播放器音量降低至20%
- 将应用界面主题切换为夜间模式

当然，在设定的夜间模式结束时间，音量和界面外观将自动恢复至夜间静默前的状态。

## 不再覆盖用户视图和卡片

经过数月的密集界面开发，部分更新会覆盖用户自定义的界面设置。

我们很高兴地告知您，从0.98版本起，我们将不再覆盖您创建的视图。仅会更新前三个默认视图（首页、音频和设备）。其余配置完全由您掌控——现在正是您全面接管界面配置的时候！

说明文档中我们解释了[如何启用配置模式](/docs/ais_app_ui_config)。
FAQ中新增了示例，展示如何添加[自定义处理器温度图表卡片](/docs/ais_gate_faq_config_yaml)以及更进阶的[Node-RED集成教程](/docs/ais_faq_node_red)，其中演示了在网关上安装Node-RED并与家庭助手应用集成的方法（感谢Łukasz G.提供的创意）。

![AIS dom Tryb nocny](/img/en/blog/0.88_definiuj_vidoki_i_karty.png)

## 音频列表全新美化外观

我们优化了搜索列表的视觉效果，并新增了从播放列表删除曲目的功能（支持Spotify和YouTube）。

![AIS dom remove from list](/img/en/blog/remove_from_yt_list.png)

## Google Drive集成已通过Google官方验证

现在可以更便捷地添加Google云端硬盘。

![Google Drive](/img/en/blog/drive_logowanie.png)

## 通过应用程序进行屏幕设置

在网关配置中，我们新增了屏幕画面自适应功能。
若通过HDMI接口连接的显示器或电视出现画面裁剪或偏移现象，您可在此处调整图像以匹配屏幕尺寸。

![Google Drive](/img/en/blog/ustawienia_ekranu.png)

## 系统自动更新功能开发启动

夜间静默模式与用户界面保护机制的引入，是实现系统自动更新功能的第一步。自1.0版本起，我们将持续完善系统功能并实时更新软件包，同时计划新增可选式自动升级至最新系统版本的功能。

### 首个自动更新组件youtube-dl

当前版本(0.98.9)已实现对youtube-dl组件的自动更新支持。

<a href="https://github.com/ytdl-org/youtube-dl/" target="_blank">youtube-dl</a> 是一款基于Python开发的工具，支持从数百个免费网站下载音视频内容——<a href="http://ytdl-org.github.io/youtube-dl/supportedsites.html" target="_blank">查看youtube-dl支持的平台列表</a>。目前我们通过该组件实现网关对YouTube.com音乐内容的播放功能。

该组件体积虽小，但因免费网站音频内容的呈现方式频繁变更，需保持较高更新频率。鉴于其特殊性，我们将其作为自动更新机制的试点组件。自0.98版本起，网关将自动安装经我们验证的youtube-dl新版本。

## 其他重要更新

- 禁止在网关运行时"取消麦克风常驻"(悬浮于其他应用上方的麦克风图标)(感谢Tomasz B.反馈该问题)

- 夜间静默时段暂停新版本通知推送(该创意来自热心用户——衷心感谢)

- 启动时默认禁用HDMI CEC设备控制功能，避免部分显示器/电视误触发网关休眠/关机(该问题出现在最新系统镜像中，经多位用户反馈后，我们已立即提供临时解决方案，本版本将为所有设备永久修复)

- 集成最新稳定版Home Assistant <a href="https://www.home-assistant.io/blog/2019/08/28/release-98/" target="_blank">0.98</a>，包含大量新特性与改进

----

欢迎立即升级体验

2019.09.19 智能家居助手团队