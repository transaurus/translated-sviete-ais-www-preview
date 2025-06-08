---
author: Jola AI-Speaker
authorURL: https://github.com/sviete
authorImageURL: https://avatars3.githubusercontent.com/u/43966761?s=460&v=4
title: Wersja systemu 0.104.5 Słucham Cię
---

# 0.104.5 聆听您的声音 :)

![](/img/en/blog/202002/ai-speaker.png)

"聆听您的声音"是我们项目的核心理念。这不仅是一句口号，因为我们始终致力于倾听客户的需求与反馈。

本版本我们开始支持"唤醒词"功能，并推出更强大的媒体播放器控制能力，这些功能已集成至智能家居助手。

<!--truncate-->

## 关键词唤醒检测

我们率先在Android应用中推出（后续将扩展至全平台应用）**关键词唤醒检测功能**——这是触发语音指令录制的核心机制。

![](/img/en/blog/202002/porcupine.png)

经过测试，我们最终采用高精度轻量级的唤醒引擎[Porcupine](https://picovoice.ai/)，其优势在于：

- 采用经真实场景训练的深度神经网络
- 仅需20KB内存即可高效运行
- 跨平台支持：基于ANSI C实现，支持树莓派/BeagleBone/Android/iOS/watchOS/Linux(x86_64)/Mac/Windows/WebAssembly
- 可扩展性：能同时检测多个唤醒词且不增加CPU/内存负担
- 部分开源：免费提供多平台预训练唤醒词库

这是我们针对Android设备的唤醒词检测测试应用：

https://github.com/sviete/AIS-hotword

![](/img/en/blog/202002/ais_hot_word.png)

> 该功能已内置至Google Play版本应用中
> 麦克风启用需用户主动授权，并通过状态栏通知明确提示。**100%离线运行——无需网络连接，我们聆听但不窃听！**

![](/img/en/blog/202002/ais_hot_word_1.png)

首批提供多个Apache 2.0许可的预训练唤醒词选项，并支持灵敏度自定义设置。

用户可依据个人需求调整唤醒词检测灵敏度。

该功能与播放器及房间平面图（floor plan）相结合，可轻松构建家庭控制面板——只需在平板电脑上安装我们的免费应用即可 :)

[AI-Speaker](https://play.google.com/store/apps/details?id=pl.sviete.dom&hl=en)

我们的最终目标是使用与品牌关联的自定义唤醒词。据我们所知，这将是波兰首个此类项目，需要投入时间和资源。目前暂未公布具体时间表。

更多实现细节请参阅文档 [触摸控制面板](/docs/ais_app_android_dom_tablet)

![媒体重定向](/img/en/frontend/apk_hot_word_options.png)

## 播放器

我们新增了更高级的播放器控制功能。除设备内置的媒体播放器（已预配置媒体流服务）外，现在还可实现：

- 将媒体重定向至其他播放器：

![媒体重定向](/img/en/frontend/player_redirect.png)

- 播放器分组：

![播放器分组](/img/en/frontend/player_grup.png)

- 向扬声器组发送待朗读文本（仅限支持TTS的扬声器）

![向扬声器组发送文本](/img/en/frontend/player_tts.png)

详细实现请参阅文档 [播放器](/docs/ais_app_player)

现在搭载Android系统的手机/平板/TvBox也可作为播放器使用，并能接收语音通知。只需安装我们的免费应用即可。通过该应用还能便捷地远程控制网关的媒体播放（通过另一台手机设备）。

[AI-Speaker](https://play.google.com/store/apps/details?id=pl.sviete.dom&hl=en)

![通过手机控制网关媒体](/img/en/frontend/mob_notification_media.png)

具体实现详见文档《通过手机控制网关媒体》

## WearOS智能手表应用新版

我们改进了与网关的通信机制，现在不仅网关会播报动作执行的语音/文本反馈，发送指令的客户端也会同步接收通知。
简要流程如下：

![](/img/en/blog/202002/watch_1.jpg)
![](/img/en/blog/202002/watch_2.jpg)

## Zigbee2MQTT

更便捷的设备重命名功能——只需点击地图上的设备节点，当前名称将自动填入改名表单。

<iframe width="560" height="315"  src="https://www.youtube.com/embed/jYW2V8zgcDI" frameBorder="0" allowFullScreen></iframe>

## 为卡片生成CSS样式（平面图）

我们最终计划实现"拖放式"操作，让用户能自由布置平面图上的设备并进行控制。您可以在论坛查看功能原型：https://ai-speaker.discourse.group/t/rzut-podlogi-floor-plan/155

![平面图](/img/en/blog/202002/floor_plan.png)

## Home Assistant

最新稳定版[Home Assistant](https://www.home-assistant.io/blog/2020/01/15/release-104)

我们非常欣赏其改进的实体处理功能，以及直接从用户界面删除不可用条目的能力。

![助手](/img/en/blog/202002/ha_entity_del.png)

---

欢迎升级并[参与论坛讨论](https://ai-speaker.discourse.group/)
AI-Speaker 2020年2月
---