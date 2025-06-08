---
author: Jola AI-Speaker
authorURL: https://github.com/sviete
author_title: Asystentka
authorImageURL: https://avatars3.githubusercontent.com/u/43966761?s=460&v=4
title: Wersja systemu 0.110.7
tags: ["armbian", "zigbee", "home assistant", "stress tests"]
---

# 0.110.7版Home Assistant、Armbian、网关压力测试、Zigbee

- ![Home Assistant](/img/en/blog/202006/hass.png) 新版Home Assistant——堪称最大规模版本更新 :)
- ![Armbian](/img/en/blog/202006/armbian.png) Armbian——在AIS dom网关上运行搭载最新5.x内核的Linux系统
- ![Stress](/img/en/blog/202006/tuning.png) 网关压力测试及优化改进
- ![Zigbee](/img/en/blog/202006/zigbee.png) Zigbee2Mqtt再次更新，现已支持[140个厂商的785种设备](https://www.zigbee2mqtt.io/information/supported_devices.html)

<!--truncate-->

:::tip[温馨提示]
注意：更新前建议先进行[配置备份](/docs/ais_bramka_configuration_software#kopia-zapasowa-konfiguracji)。通过预先验证配置完整性可显著提升更新成功率。
:::

:::important[重要通知]
若更新后遇到问题，请参考[控制台更新指南](/docs/ais_bramka_update_manual)或[执行应用完全重置](/docs/ais_bramka_reset_ais_step_by_step)——特别是安装了非标准组件的用户需特别注意此流程。
:::

:::caution[注意事项]
 **更新后首次启动可能耗时长达20分钟**

 ![wait](/img/en/blog/202006/wait.png) 在此期间系统将更新网关集成的所有依赖库...

 **请耐心等待更新完成**
:::

## ![Home Assistant](/img/en/blog/202006/hass.png) 新版Home Assistant——重大版本更新 :)

最新稳定版[Home Assistant 0.110.7](https://www.home-assistant.io/blog/2020/05/20/release-110/)
本次更新除新增功能与集成组件外，还包含大量优化代码体积和运行速度的改进！

![Home Assistant](/img/en/blog/202006/ha_integrations.png)

## ![Armbian](/img/en/blog/202006/armbian.png) Armbian——在AIS dom网关上运行最新5.x内核Linux

Armbian是面向多种单板计算机(SBC)的Linux操作系统。其功能特性详见官方文档：https://docs.armbian.com/ 及社区论坛：https://forum.armbian.com/
作为成熟度极高的项目，若您需要搭载最新5.5.x内核的"纯净Linux"用于服务器场景，Armbian将是理想选择（三年前我们曾基于Armbian和Mopidy音乐服务器构建音箱平台，但多媒体处理始终是原生Linux的弱项，因此当前方案转向Android系统）。

![Armbian](/img/en/blog/202006/armbian.jpeg)

在论坛上我们逐步展示了如何：

1. 在ais dom网关上运行Armbian -> [论坛说明](https://ai-speaker.discourse.group/t/armbian-ubuntu-na-bramce-ais-dom/500)

![Armbian](/img/en/blog/202006/armbian_1.png)

2. 在Armbian上进行基准测试 -> [论坛说明](https://ai-speaker.discourse.group/t/benchmarking-na-armbian/501)

![Armbian](/img/en/blog/202006/animated.gif)

3. 在Armbian上安装Supervised Home Assistant及/或其他多种现成应用 -> [论坛说明](https://ai-speaker.discourse.group/t/armbian-supervised-home-assistant-na-bramce-ais-dom/511)

![Armbian](/img/en/blog/202006/armbian_softy.png)

## ![Stress](/img/en/blog/202006/tuning.png) 网关压力测试与优化

在开发0.110版本期间，我们进行了系列压力测试。测试成果包括更改了网关的输入输出管理模式（Linux中的io调度器）。

论坛新增说明 -> [压力测试主题导引](https://ai-speaker.discourse.group/t/armbian-stres-testy-na-bramce/512)

![Stress](/img/en/blog/202006/stress.png)

我们最推荐使用monkey应用进行测试 :monkey_face:
虽然原理简单...但通过生成数十万次高度随机事件，能产生相当有趣的效果 :wink:

<iframe width="720" height="460"  src="https://www.youtube.com/embed/-1uBMCmMaHg" frameBorder="0" allowFullScreen></iframe>

## ![Zigbee](/img/en/blog/202004/honeybee.png) Zigbee2Mqtt更新至1.13.1版本

### [支持140个厂商的785种设备](https://www.zigbee2mqtt.io/information/supported_devices.html)

Zigbee更新将与其他组件更新一样自动执行。

![网关软件](/img/en/blog/202006/update.png)

----

欢迎参与更新并[在论坛讨论 :)](https://ai-speaker.discourse.group/)
AI-Speaker 2020年6月
----