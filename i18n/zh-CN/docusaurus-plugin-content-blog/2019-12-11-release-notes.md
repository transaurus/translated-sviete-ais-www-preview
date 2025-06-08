---
author: Jola AI-Speaker
authorURL: https://github.com/sviete
authorImageURL: https://avatars3.githubusercontent.com/u/43966761?s=460&v=4
title: Wersja systemu 0.102 Galeria i QR kody
---

## 2019年12月11日发布的系统版本0.102.4

![](/img/en/blog/201912/galeria2.png)

<!--truncate-->

## 图库功能

为简化房间照片添加流程，我们在应用中新增了图库组件。您只需将照片发送至设备，即可在应用卡片上展示。具体操作详见[用户界面配置指南](/docs/ais_app_ui_config#添加自定义卡片)。

![](/img/en/blog/201912/galeria.png)

本版本起，您可直接通过应用便捷添加照片，并将其作为设备卡片展示。下个版本将说明如何配置自动化：当触发事件（如门铃响）时，自动通过摄像头拍摄照片/录制短视频，并在电视端展示或发送通知。

## 向导功能与网关ID扫码

最新版移动应用新增了配置向导功能，可逐步引导完成移动端设置。

同时支持通过摄像头扫描网关二维码ID。

若在网关连接参数中填写网关ID（而非URL地址），应用将自动判断可行的连接方式（本地或隧道连接）。具体原理参见AIS dom应用文档说明。

该扫码功能已同步集成至[集成商面板](https://powiedz.co/ords/f?p=DOM1)，简化账户添加流程。

![助手](/img/en/blog/qr_code_web.png)

## 浏览器端新增对话窗口

网页版应用中，现可通过任意界面右上角聊天图标唤起浏览器端语音助手对话窗口。

因支持语音输入和文字输入两种指令方式，原麦克风图标已替换为聊天对话图标：

![](/img/en/blog/201912/new_conversation.png)

## 定制您的专属界面！

我们已开放首页(default_view)的编辑权限——毕竟每个家庭都独一无二:)
自0.102版本起，我们持续维护并更新**音频**与**设备单元**两大视图模块

* **音频**视图中提供播放器及免费音频内容合集
* **单元**视图中自动填充符合特定条件的设备卡片，通过这种方式演示如何创建自定义卡片。您可参考该视图的卡片配置方案，将其复制到自己的视图中使用

操作指南中我们详解了[如何启用配置模式](/docs/ais_app_ui_config)

![智能助手](/img/en/blog/201912/lovelace_custom.png)

我们正在将最后两个预设视图**音频**和**单元**迁移至应用菜单——最终所有视图都将开放编辑权限

## Home Assistant

最新稳定版[Home Assistant 0.102.3](https://www.home-assistant.io/blog/2019/11/20/release-102/)

新增可通过应用访问的场景编辑器，支持将设备当前状态保存为场景，并通过语音指令激活[自动化触发](/docs/ais_app_assistent_commands#uruchamianie-automatyzacji)

```text
'Uruchom {nazwa automatyzacji}'
lub
'Automatyzacja {nazwa automatyzacji}'
```

启用应用内场景编辑功能需参照[Home Assistant文档](https://www.home-assistant.io/docs/scene/editor/)操作。版本号>0.102的网关设备将默认开启场景编辑器

![智能助手](/img/en/blog/201912/scene_editor.png)

## Discourse论坛

应用户需求，我们将新增文章评论功能，若用户积极参与讨论互助，可能逐步发展成论坛社区。具体细节即将公布

![Discourse](/img/en/blog/201912/Discourse.png)

----

欢迎立即升级！
AI-Speaker 2019年12月