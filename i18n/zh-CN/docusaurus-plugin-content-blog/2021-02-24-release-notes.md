---
author: Jola AI-Speaker
authorURL: https://github.com/sviete
author_title: Asystentka
authorImageURL: https://avatars3.githubusercontent.com/u/43966761?s=460&v=4
title: Wersja systemu Darek
tags: ["ais dom", "home assistant", "zigbee2mqtt"]
---

<div class="IntroAisBlogMenu" >
<div>

![AIS](/img/en/blog/202102/darek.png)

</div>

<h2>Darek LTS!</h2>

</div>

![AIS Supla MQTT](/img/en/blog/202102/bridge.png) SUPLA MQTT桥接 ![AIS DEV KIT](/img/en/blog/202102/speaker.png) 开发套件 ![AIS Python](/img/en/blog/202102/snake.png) Python3.9.1 ![AIS Zigbee2Mqtt](/img/en/blog/202102/honeybee.png) Zigbee2Mqtt

<!--truncate-->

## 无忧升级指南

:::tip[数据备份]
### ![A](/img/en/blog/202009/alpha-a-circle.png) 数据备份

重要提示：升级前建议先执行[配置备份](/docs/ais_bramka_configuration_software#kopia-zapasowa-konfiguracji)。通过预先验证配置完整性可显著提升升级成功率。
:::

:::important[控制台与日志]
### ![B](/img/en/blog/202009/alpha-b-circle.png)控制台与日志

若遇升级问题，请参考[控制台升级指南](/docs/ais_bramka_update_manual)或[应用完全重置教程](/docs/ais_bramka_reset_ais_step_by_step)。
特别提醒：安装非标准组件的用户需重点关注此步骤。
:::

:::caution[耐心等待]
### ![C](/img/en/blog/202009/alpha-c-circle.png) 保持耐心。升级后首次启动耗时较长——请耐心等待。

**升级后首次启动可能长达20分钟**
此时系统正在更新集成库并将数据库迁移至新格式。
**请耐心等待升级完成**
:::

## ![](/img/en/blog/202102/darek.png) Darek长期支持版！

注意：本版本要求Python版本高于3.7，这是由于Home Assistant已升级至新版Python环境。

![](/img/en/blog/202102/python_update_ha.png)

若版本检测时出现提示**当前Python版本为3.x.x 请升级至LTS版**

![](/img/en/blog/202102/python_update.png)

则需在升级前手动更新网关二进制包（含Python语言环境）。我们未设置自动更新，您可通过两种方式操作：

1. 方式一 - 完全重置应用：

    a) 执行[配置备份](/docs/ais_bramka_configuration_software#kopia-zapasowa-konfiguracji)
    
    b) 进行[应用完全重置](/docs/ais_bramka_reset_ais_step_by_step)
    
    c) 在[首次启动应用时](/docs/ais_bramka_first_run_step_account)恢复配置

或

2. 方法二 - 运行脚本并耐心等待其完成：

    完整操作流程详见论坛帖子：[AIS LTS长期支持版本](https://ai-speaker.discourse.group/t/ais-lts-long-time-support-dlugoterminowe-wsparcie/1013)

更新完成后，网关将运行最新版Python语言环境：

![](/img/en/blog/202102/python.png)

后续更新将自动执行。我们已开始测试Python 3.9.2版本。只有升级到第4版时会再次复杂化，但那将是几年后的事了 :) 而且届时AIS的升级流程肯定会更加简便。

------------------------------

当然您可以选择不升级网关，但我们强烈建议进行更新，因为每个新版本都会带来更好的性能。请保持耐心，一切都会顺利进行。

如果遇到任何问题也无需担心——Celina已推出"AI-Speaker设备编程服务"，费用仅为象征性金额即可获得专业设备配置服务。
论坛详情请见：[AI-Speaker设备编程服务](https://ai-speaker.discourse.group/t/usluga-programowania-urzadzen-w-ai-speaker/1368)

## ![](/img/en/blog/202102/bridge.png) SUPLA MQTT桥接

我们在家庭助理系统中提供官方SUPLA MQTT集成。该集成面向希望通过语音控制SUPLA设备，并在AIS dom网关上实现自动化操作的用户。

![SUPLA集成](/img/en/frontend/integration_supla_2.png)

我们已与SUPLA团队建立合作，后续将公布更多细节。
整个集成过程仅需在应用中点击几下即可完成，具体操作参见[AIS SUPLA MQTT](/docs/ais_app_supla)文档

## ![](/img/en/blog/202102/speaker.png) AI-Speaker开发套件

如先前预告，我们现发布详细指南，让每位用户都能自行采购所需组件将网关改装为智能音箱。

![开发套件1](/img/en/iot/dev_kit_1.jpeg)

指南文档详见：[AI-Speaker开发套件1](/docs/ais_dev_kit_1_index)
明日（2021年2月25日）我们将补充组装过程照片，并在Allegro平台上线部分现货。

## ![](/img/en/blog/202102/honeybee.png) Zigbee2Mqtt

Zigbee2Mqtt已更新至1.7.1最新版本
包含大量修复、新增设备支持及新版zigbee适配器固件，完整更新日志参见[1.17.1](https://github.com/Koenkk/zigbee2mqtt/releases/tag/1.17.1)

![](/img/en/blog/202102/z2m.png)

若您的Zigbee适配器遇到问题，正如我们此前所述——我们已新增设备编程服务，详情请查阅论坛：

[![](/img/en/blog/202102/ais_devices_suport.png)](https://ai-speaker.discourse.group/t/usluga-programowania-urzadzen-w-ai-speaker/1368)

## ![](/img/en/blog/202101/hass.png) AIS Tasmota

最新版本的代码和固件一如既往可在我们的代码库获取：[AIS Tasmota v9.3.1 Kenneth](https://github.com/sviete/AIS-Tasmota/tree/firmware/firmware)

完整更新说明详见[Tasmota发布页](https://github.com/arendst/Tasmota/releases/tag/v9.3.1)：

[![](/img/en/blog/202102/tasmota.png)](https://github.com/arendst/Tasmota/releases/tag/v9.3.1)

## ![](/img/en/blog/202101/hass.png) 家庭助手

家庭助手的最新版本，即我们的``ais-dom``软件包，基于最新稳定版Home Assistant Core构建。

![家庭助手](/img/en/blog/202102/hasocial.png)

Home Assistant的详细更新内容可查阅其官方博客：[2021.2版本：Z-Wave... JS!](https://www.home-assistant.io/blog/2021/02/03/release-20212/)

-------

##### AI-Speaker 2021年2月版