---
author: Jola AI-Speaker
authorURL: https://github.com/sviete
authorImageURL: https://avatars3.githubusercontent.com/u/43966761?s=460&v=4
title: Wersja systemu 0.100.4 Google Home
---

## 2019年10月30日发布的系统版本0.100.4

## Google Home

与[Google Home的集成](/docs/ais_app_ai_integration_google_home)

我们提供**AIS Google Home**功能，实现家庭助手与Google助理开发者平台的对接。该集成基于官方[Google Assistant SDK](https://developers.google.com/assistant)开发，允许从家庭助手直接向Google助理发送指令和提问。

![AIS Google Home配置界面](/img/en/bramka/ais_google_home_1.png)

<!--truncate-->

这意味着[助手Jolka](/docs/ais_app_ai_integration)可在本地运行管理智能家居，同时您还能启用Google助理，让网关获得Google Home设备的功能 🥳

当您向Google助理提问或发送指令时，将通过Google服务返回原始音频响应。这样您就能同时与两个语音助手对话 👧 👨 🚀

## Android SDK

所有组件已迁移至SdkVersion 28。我们同步更新了部分应用界面设计，并在文档中添加了应用说明及源代码仓库链接。

![AIS dom APK界面](/img/en/frontend/ais_launcher_apk_screen.png)

## 应用界面

### 优化的夜间模式

Sebastian优化了夜间模式的配色方案
![AIS dom夜间模式配色](/img/en/blog/ais_dom_dark_mode_colors.png)

### 自定义界面定义

用户Darek贡献了自定义界面的创新实现方案，并分享了日历功能的巧妙设计。[查看文档说明](/docs/ais_app_ui_config#自定义用户界面)。我们鼓励每位用户参与文档编辑[贡献指南](/docs/ais_faq_where_is_the_code#参与贡献) 🥰

## 当...时执行...

最新稳定版Home Assistant <a href="https://www.home-assistant.io/blog/2019/10/10/release-100/" target="_blank">0.100</a>带来多项新特性，包括支持从设备端开始定义自动化流程。

![设备自动化设置](/img/en/blog/automation_from_device.png)

## Tasmota增强版

近期频繁被问及的一个问题是关于与运行Tasmota固件的设备协同工作的情况。
我们在FAQ中新增了[Tasmota兼容性](/docs/ais_faq_iot_ap_mode)章节，说明**由于网关内置MQTT代理，任何支持MQTT协议的设备都能与家庭助手无缝协作**。
同时详细阐述了实现原理，以及我们如何持续优化以提供最简化的操作流程！

附注
我们还为AIS dom设备推送了最新固件版本，控制台的美观配色只是冰山一角;) FAQ中同时介绍了[我们提供的便捷功能](/docs/ais_faq_iot_ap_mode#jakie-ułatwienia-dostarczamy)

![Reset 5](/img/en/iot/iot_device_menu_upgrade_6.png)

----

诚邀您进行系统升级！
AI-Speaker 2019年10月