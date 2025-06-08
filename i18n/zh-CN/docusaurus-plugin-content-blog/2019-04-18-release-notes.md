---
author: Celina AI-Speaker
authorURL: https://github.com/sviete
authorFBID: 1186570423
title: Wersja systemu 0.91.4  Wikipedia, kamery i łatwe dodawnie urządzeń
---

## 2019年4月18日发布的系统版本0.91.4

### 维基百科信息查询

**家庭助手**在回答"谁是...","查找关于...的信息"这类问题时，会调用"Google知识图谱"数据库。使用这类知识库的目的是筛选最相关的内容并给出简明回答。Google知识图谱的主要信息来源是维基百科。本次更新新增了搜索并朗读整篇维基百科文章的功能。

在**信息搜索**版块新增语音指令：[维基百科语音指令](/docs/ais_app_assistent_commands#wyszukiwanie-informacji)
初始阶段我们支持一条语音指令："维基百科+搜索关键词"，关键词可以是任意名称。

![用户界面配置](/img/en/frontend/wikipedia_1.png)

<!--truncate-->

### 摄像头视频流

通过[Home Assistant的实时流组件](https://www.home-assistant.io/components/generic/#live-stream)，我们现在可以查看IP摄像头的实时画面。这开启了诸多可能性：

- 当有人按门铃时，自动将门口摄像头的画面推送到Chromecast电视
- 在儿童房安装摄像头，将网关设备用作电子婴儿监视器
- 运动检测和图像物体分析，用于描述画面内容并触发相应动作——例如语音播报"邮递员先生您好，请把信件放入信箱 :)"

我们计划深入探讨这个主题，不久将逐步详细介绍系统中摄像头的应用方案。

![摄像头](/img/en/frontend/stream_cams.jpeg)

### 简易设备添加

为简化设备接入流程，我们新增了分步引导的添加新设备向导。

![设备添加向导](/img/en/frontend/add_device.png)