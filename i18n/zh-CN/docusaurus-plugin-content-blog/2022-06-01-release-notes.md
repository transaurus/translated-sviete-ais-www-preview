---
author: Jola AI-Speaker
authorURL: https://github.com/sviete
author_title: Asystentka
authorImageURL: https://avatars3.githubusercontent.com/u/43966761?s=460&v=4
title: Wersja systemu Maja
tags: ["mqtt", "home assistant", "zigbee"]
---

<div class="IntroAisBlogMenu" >

![AIS](/img/en/blog/202206/ais_version.png)

</div>

<!--truncate-->

## 无忧升级指南

:::tip[备份 ![A](/img/en/blog/202112/cloud-upload.png)]

升级前建议先进行[配置备份](/docs/ais_bramka_configuration_software#kopia-zapasowa-konfiguracji)。通过这种方式，您可以在升级前验证配置的正确性，提高升级成功率。

:::

:::important[控制台 ![B](/img/en/blog/202112/console.png)]

若遇应用升级问题，可通过[控制台手动升级](/docs/ais_bramka_update_manual)，实时查看日志和升级进度，便于问题诊断。
:::

:::caution[耐心等待 ![C](/img/en/blog/202112/timer-sand.png)]

升级及首次启动可能耗时较长，请保持耐心。您随时可通过``htop``或``pm2 logs``命令查看系统状态（了解网关当前运行情况）。
:::

## 需要帮助？

:::warning[重置 ![D](/img/en/blog/202112/broom.png)]
若无法自行诊断问题，请放心，我们已为您准备好解决方案。我们专门设计了简易流程帮助恢复系统默认设置，详见：[逐步执行完整应用重置](/docs/ais_bramka_reset_ais_step_by_step)。
:::

:::important[返厂编程 ![D](/img/en/blog/202112/lifebuoy.png)]
若无法完成完整重置流程且系统仍无法运行，您可将设备寄回我们进行编程修复。详情参见论坛帖子：[返厂编程服务](https://ai-speaker.discourse.group/t/usluga-programowania-urzadzen-w-ai-speaker/1368)
:::

## ![](/img/en/blog/202102/honeybee.png) 马亚系统

本次系统更新新增了与伊顿Easy PLC控制器的通信集成。通过该功能，用户可借助伊顿Easy PLC实现AIS有线控制。由于需要在PLC端进行特殊编程，该集成将作为PRO版专属功能提供支持。

![](/img/en/integrations/ais_easy.png)

### ![](/img/en/blog/202102/honeybee.png) Zigbee2Mqtt

Zigbee2Mqtt已更新至最新版1.25.1。新版本支持来自301家厂商的2195种设备：

![](/img/en/blog/202206/z2m.png)

详见Zigbee2Mqtt文档：https://www.zigbee2mqtt.io/

### ![](/img/en/blog/202101/hass.png) 家庭助理

最新版家庭助理2022.5，即我们基于Home Assistant Core开发的``ais-dom``软件包。
最新版本支持1969种集成：

![](/img/en/blog/202206/ha.png)

详情参阅Home Assistant文档：https://www.home-assistant.io/integrations/

--------

##### AI-Speaker 2021年12月版