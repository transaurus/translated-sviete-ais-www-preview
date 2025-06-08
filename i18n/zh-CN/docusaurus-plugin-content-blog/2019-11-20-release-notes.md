---
author: Jola AI-Speaker
authorURL: https://github.com/sviete
authorImageURL: https://avatars3.githubusercontent.com/u/43966761?s=460&v=4
title: Wersja systemu 0.101.4 RF 433 i IKEA TRÅDFRI
---

## 2019年11月20日发布的系统版本0.101.4

## RF 433与AIS dom设备

![RF 433](/img/en/iot/iot_ais_dom_device_rf433_learn_step_7.png)

为实现将遥控器（用于门禁、卷帘）、开关、传感器等通过433MHz射频通信的设备与AIS dom网关连接，我们需要额外支持RF 433信号收发功能的设备。推荐使用刷写了第三方固件的Sonoff RF Bridge 433，该固件不仅支持与AIS dom网关通过MQTT协议轻松集成，还能兼容更多通信协议（原厂固件仅支持24位编码的单一协议）。

<!--truncate-->

![RF 433](/img/en/iot/iot_ais_dom_device_rf433_map.png)

操作视频演示：

<div>
<iframe width="560" height="315"  src="https://www.youtube.com/embed/NEFd_T3gqNU" frameBorder="0" allowFullScreen></iframe>
</div>

## 宜家TRÅDFRI智能灯具

自0.101版本起，我们已将宜家Trådfri网关集成作为默认内置功能——不再需要额外安装组件包。具体操作详见《宜家Trådfri集成文档》

![宜家配置界面](/img/en/bramka/integration_ikea_0.jpg)

在家庭助手应用中的呈现效果：

<video width="100%" height="100%" playsInline="" autoPlay="" muted="" loop="">
  <source src="/video/ikea.webm" type="video/webm"/>
</video>

## IFTTT应用示例

我们在集成模块新增了示例分类。首先逐步演示如何在IFTTT平台注册账号并创建首个小程序（Applet）。根据IFTTT术语，Applet是指能够联动两个及以上应用或设备，实现单一应用/设备无法独立完成的功能组合。
后续示例将展示如何通过IFTTT服务触发家庭助手中的任意操作。

![IFTTT界面](/img/en/blog/examples_ifttt.png)

## TuneIn电台服务

通过对接TuneIn API，本次更新在电台分类新增"TuneIn热门"和"TuneIn趋势"两大板块。后续版本将陆续添加TuneIn音频搜索及收藏功能。

![TuneIn启动界面](/img/en/blog/tunein_start.png)

## 文档搜索功能

Sebastian为我们的文档系统找到了绝佳的搜索解决方案。我们已通过www.algolia.com的官方认证👋

![Algolia搜索界面](/img/en/blog/algolia.png)

现在文档页面已支持全文检索

![Algolia搜索结果](/img/en/blog/algolia2.png)

## 工作日设置

我们默认配置中添加工作日/休息日传感器的灵感来自用户Darek——感谢 :)
该传感器会指示当前日期是否为工作日，并考虑国家法定节假日信息。

![工作日设置](/img/en/blog/working_days.png)

目的是简化考虑工作日因素的自动化规则添加流程。

![工作日设置](/img/en/blog/working_days1.png)

## 其他重要变更

> 通过语音通知依赖项安装状态，并默认关闭历史记录功能。

以下说明我们做出该决策的原因。

客服反馈中最常见的问题是升级后启动耗时过长。部分用户不查看日志，若设备升级后未快速启动，就会直接断电重启。我们甚至收到过一台被退回售后的设备——该设备被切换到测试版通道后启动时间过长...我们怀疑因此导致损坏（或原本就存在缺陷）。虽然比例不高，但这种情况让我们非常担忧 :( 。

我们竭尽全力确保所有设备运行良好（每台设备编程后都会测试），**因此我们严肃对待这起首例投诉，决定彻底调查该问题**。

经排查发现导致升级后启动缓慢的两个主要原因：

1. **依赖项安装**：升级后的首次启动可能需要十几分钟（具体时长取决于已添加的集成数量）

2. **数据库迁移**：首次启动时的数据迁移可能再耗费十几分钟（耗时取决于数据模型变更内容、日志记录设置及系统实体数量）

这些问题难以彻底解决并向用户解释，因为我们无法预知用户集成的设备数量，也不清楚其网络带宽状况，因此无法预估升级耗时。

实践证明，应用程序中的升级状态提示和升级进度日志检查仍显不足（尤其对视力障碍用户或仅将设备作为扬声器使用的场景）。

但我们已采取以下措施缓解这些问题：

### 依赖项安装

为解决第一个问题，我们在Home Assistant首次启动安装额外依赖包时添加了语音提示。
从本版本开始，在更新过程中您将听到以下标准语音提示：

- 更新中。正在下载...
- 更新中。正在安装...
- 更新中。正在重启...

随后（在更新后的首次启动时）：

- 正在安装依赖包：...；请稍候。
- 正在安装依赖包：...；请稍候。
- 正在安装依赖包：...；请稍候。
... 根据您已安装的集成数量，此过程会持续进行。这样您就能了解系统正在运行，无需强制断电。

### 数据库迁移

数据库的情况更为复杂。我们最大的客户为视障人士生产设备，这些用户主要通过语音交互使用设备。他们从不关心记录器生成的历史数据，也无法自行配置或禁用该功能。

部分高级用户非常重视数据记录功能，我们默认提供的日志存储设置和设备存储空间无法满足他们的需求。这些用户通常会自行配置日志参数，将数据存储在NAS设备或任意关系型数据库（MySQL、MariaDB、PostgreSQL或MS SQL Server）中，以便分析TB级的数据。他们清楚这类数据库需要充足存储空间，且版本更新后迁移海量数据可能耗时数小时甚至数天（Home Assistant论坛上的真实案例）。

基于以上考量，同时考虑到禁用记录器后设备运行更快、更新后启动时间更可预测，我们决定默认关闭历史数据记录功能。

这并非完美方案，部分需要基础历史数据的用户需参照文档手动启用该功能：[记录器](https://www.home-assistant.io/integrations/recorder/)。

此方案折衷了两种用户需求：不需要日志功能且希望设备快速更新的用户群体，与需要日志功能并能自主管理数据库存储空间的高级用户群体。

> 如果更新后发现缺少"历史记录"选项卡，您可以在配置中轻松添加。
当然请记住，如果您有数十台设备生成数千个事件，那么设备上仅有的几个GB空闲存储空间可能会很快耗尽。因此我们建议先熟悉**[记录器组件](https://www.home-assistant.io/integrations/recorder/)的设置。

![历史记录](/img/en/blog/history.png)

只需在[配置文件](/docs/ais_gate_faq_config_yaml)中添加2行代码：

```yaml
recorder:
history:
```

## Home Assistant

最新稳定版[Home Assistant](https://www.home-assistant.io/blog/2019/10/30/release-101/" target="_blank">0.101)集成了由波兰开发者[Maciej Bieniek](https://github.com/bieniu)开发的Airly空气质量监测(https://airly.eu/pl/) 👏 https://www.home-assistant.io/integrations/airly/ 以及大量修复和改进 - 超过300名开发者贡献了上千项变更。令人印象深刻 👌

## 待办事项

我们曾承诺要介绍办公室的暖气控制系统，但由于当前版本功能扩展，我们没来得及完成详细说明和示意图...**将在近期补充完整文档**。

用户Piotr向我们分享了如何在网关上配置Z-wave。非常感谢 - 我们喜欢这样的专业💪用户。我们已将此加入待办清单，计划在后续版本中为所有感兴趣的用户开放此功能。

我们正在开发Zigbee集成并取得了一些进展 :) 目标是无需IKEA网关就能控制30兹罗提的IKEA可调光灯泡。希望在后续更新中展示完整解决方案。这是当前进展效果。

![zigbee开发](/img/en/blog/zigbee_dev.png)

----

欢迎进行更新！
AI-Speaker 2019年11月