---
author: Jola AI-Speaker
authorURL: https://github.com/sviete
author_title: Asystentka
authorImageURL: https://avatars3.githubusercontent.com/u/43966761?s=460&v=4
title: Wersja systemu Ola
tags: ["home assistant", "zigbee2mqtt"]
---

<div class="IntroAisBlogMenu" >

![AIS](/img/en/blog/202306/ais_version.png)

</div>

<!--truncate-->

## 无忧升级指南

:::tip[备份 ![A](/img/en/blog/202112/cloud-upload.png)]

升级前建议先进行[配置备份](/docs/ais_bramka_configuration_software#kopia-zapasowa-konfiguracji)。通过这种方式，您可以在升级前验证配置的正确性，提高升级成功率。

:::

:::important[控制台 ![B](/img/en/blog/202112/console.png)]

若遇应用升级问题，请通过[控制台手动升级](/docs/ais_bramka_update_manual)，实时查看日志和升级进度，便于问题诊断。
:::

:::caution[耐心等待 ![C](/img/en/blog/202112/timer-sand.png)]

升级过程及首次启动可能耗时较长——请保持耐心。您随时可通过控制台命令``htop``或``pm2 logs``查看系统状态（了解网关当前运行情况）。
:::

## 需要帮助？

:::warning[重置 ![D](/img/en/blog/202112/broom.png)]
若无法自行诊断问题——无需担心，我们已准备好为您提供支持。我们专门设计了简易流程帮助恢复默认代码和系统设置，请参阅：[执行完整应用重置](/docs/ais_bramka_reset_ais_step_by_step)。
:::

:::important[返厂编程 ![D](/img/en/blog/202112/lifebuoy.png)]
若无法完成完整重置流程且系统仍无法运行，您可将设备寄回我们进行编程修复。详情参见论坛帖子：[返厂编程服务](https://ai-speaker.discourse.group/t/usluga-programowania-urzadzen-w-ai-speaker/1368)
:::

## ![](/img/en/blog/202306/ais_version.png) Ola版本

本次系统更新包含11个zigbee2mqtt版本：1.29.0、1.29.1、1.29.2、1.30.0、1.30.1、1.30.2、1.30.3、1.30.4、1.31.0、1.31.1、1.31.2，以及6个Home Assistant版本：2023.1、2023.2、2023.3、2023.4、2023.5、2023.6。

### ![](/img/en/blog/202102/honeybee.png) Zigbee2Mqtt

Zigbee2Mqtt已更新至最新版本1.31.2。新版本支持[来自370余家厂商的2900余款设备](https://www.zigbee2mqtt.io/supported-devices/)：

[![](/img/en/blog/202306/zigbee2mqtt.png)](https://www.zigbee2mqtt.io/supported-devices/)

Zigbee2Mqtt详细文档请参阅：https://www.zigbee2mqtt.io/

各版本Zigbee2Mqtt的新特性可在项目Github页面查阅：

- [1.29.0](https://github.com/Koenkk/zigbee2mqtt/releases/tag/1.29.0)
- [1.29.1](https://github.com/Koenkk/zigbee2mqtt/releases/tag/1.29.1)
- [1.29.2](https://github.com/Koenkk/zigbee2mqtt/releases/tag/1.29.2)
- [1.30.0](https://github.com/Koenkk/zigbee2mqtt/releases/tag/1.30.0)
- [1.30.1](https://github.com/Koenkk/zigbee2mqtt/releases/tag/1.30.1)
- [1.30.2](https://github.com/Koenkk/zigbee2mqtt/releases/tag/1.30.2)
- [1.30.3](https://github.com/Koenkk/zigbee2mqtt/releases/tag/1.30.3)
- [1.30.4](https://github.com/Koenkk/zigbee2mqtt/releases/tag/1.30.4)
- [1.31.0](https://github.com/Koenkk/zigbee2mqtt/releases/tag/1.31.0)
- [1.31.1](https://github.com/Koenkk/zigbee2mqtt/releases/tag/1.31.1)
- [1.31.2](https://github.com/Koenkk/zigbee2mqtt/releases/tag/1.31.2)

### ![](/img/en/blog/202101/hass.png) 家庭助理

最新版家庭助理2023.6.3，即我们基于Home Assistant Core开发的``ais-dom``套件。
当前版本[支持2476种集成](https://www.home-assistant.io/integrations/)：

[![](/img/en/blog/202306/ha.png)](https://www.home-assistant.io/integrations/)

各版本Home Assistant的新特性可查阅官方博客：

- 2023.1 [![](https://www.home-assistant.io/images/blog/2023-01/social.png)](https://www.home-assistant.io/blog/2023/01/04/release-20231/)

- 2023.2 [![](https://www.home-assistant.io/images/blog/2023-02/social.png)](https://www.home-assistant.io/blog/2023/02/01/release-20232/)

- 2023.3 [![](https://www.home-assistant.io/images/blog/2023-03/social.png)](https://www.home-assistant.io/blog/2023/03/01/release-20233/)

- 2023.4 [![](https://www.home-assistant.io/images/blog/2023-04/social.png)](https://www.home-assistant.io/blog/2023/04/05/release-20234/)

- 2023.5 [![](https://www.home-assistant.io/images/blog/2023-05/social.png)](https://www.home-assistant.io/blog/2023/05/03/release-20235/)

- 2023.6 [![](https://www.home-assistant.io/images/blog/2023-06/social.png)](https://www.home-assistant.io/blog/2023/06/07/release-20236/)

--------

##### AI-Speaker 2023年6月