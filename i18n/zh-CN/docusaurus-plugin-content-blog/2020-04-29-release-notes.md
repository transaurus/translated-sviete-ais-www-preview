---
author: Jola AI-Speaker
authorURL: https://github.com/sviete
author_title: Asystentka
authorImageURL: https://avatars3.githubusercontent.com/u/43966761?s=460&v=4
title: Wersja systemu 0.108.9
tags: ["zigbee", "mqtt", "home assistant"]
---

# 0.108.9版 Zigbee、图标、错误修复 🥳

- ![Zigbee](/img/en/blog/202004/honeybee.png) 更新Zigbee2Mqtt [支持123个制造商的692款设备](https://www.zigbee2mqtt.io/information/supported_devices)
- ![Icons](/img/en/blog/202004/picture.png) 应用内图标与标识
- ![Icons](/img/en/blog/202004/house.png) 新版Home Assistant
- ![Bugs](/img/en/blog/202004/bug.png) 错误修复

<!--truncate-->

:::tip[提示]
注意：建议在升级前先[备份配置](/docs/ais_bramka_configuration_software#kopia-zapasowa-konfiguracji)。通过这种方式，您可以在开始升级前检查配置的正确性，提高顺利升级的概率。
:::

:::important[重要信息]
如果升级后遇到问题，请查看[通过控制台升级](/docs/ais_bramka_update_manual)或[执行应用完全重置](/docs/ais_bramka_reset_ais_step_by_step)的步骤——这对于那些在网关上安装了额外非标准组件的用户尤其重要。
:::

## ![Zigbee](/img/en/blog/202004/honeybee.png) Zigbee2Mqtt更新

### [支持123个制造商的692款设备](https://www.zigbee2mqtt.io/information/supported_devices.html) 🥰

我们新增了备份Zigbee2Mqtt配置的功能。我们决定在应用中将其作为一个独立选项添加。这样，根据需要，您可以单独备份/恢复Home Assistant配置、Zigbee2Mqtt配置，或者同时备份/恢复所有配置。

![网关配置备份](/img/en/bramka/config_ais_dom_section1_2.png)

我们将Zigbee2Mqtt从1.8.0版本更新到了1.12.2版本（这个版本已经在网关上测试了一段时间）。后续稳定的Zigbee2Mqtt版本我们将持续发布。
Zigbee2Mqtt的更新将和其他任何更新一样简单。

![网关软件](/img/en/bramka/config_ais_dom_section1.png)

## ![Icons](/img/en/blog/202004/picture.png) 应用内图标与标识

我们为我们的集成添加了图标和标识：

![图标](/img/en/blog/202004/icons_in_app.png)

这只是开始，下一个版本中集成页面将更加美观和实用 :)

## ![Bugs](/img/en/blog/202004/bug.png) 错误修复

我们修复了许多错误，但这还只是开始。我们正在逐步完善“开箱即用的基础功能”，并将专注于进一步的改进。

在即将发布的版本中，我们将新增Z-Wave集成功能，相关讨论详见论坛：
https://ai-speaker.discourse.group/t/z-wave-zapowiedz-integracji-przez-dongle-zwave2mqtt/413

![zwave2mqtt](/img/en/blog/202004/zwave2mqtt.png)

移动应用端也将迎来重大更新——包括通知系统和位置追踪功能，更多细节请访问论坛：
https://ai-speaker.discourse.group/t/planowane-zmiany-w-aplikacji-mobilnej/412

![zwave2mqtt](/img/en/blog/202004/authentication.png)

这些将构成我们开箱即用的基础功能。此后我们将专注于系统整体优化和用户体验改进。

开发进度可通过GitHub代码库实时追踪：https://github.com/sviete

诚邀具备开发能力的爱好者共同参与编码工作 :)

我们在论坛新增"网关编程入门"板块，通过C语言、Python、Node.JS和Bash的简易案例教学，演示如何开发程序并通过家庭助理调用。

https://ai-speaker.discourse.group/c/programowanie/15

本板块专为那些更愿主动学习、改造现实世界的勇者💪而设，而非在论坛消极等待谷歌/苹果/亚马逊实现X功能。对于"给我现成完美方案"的心态，AI-Speaker的态度很明确...想都别想 ;)

## ![Icons](/img/en/blog/202004/house.png) 新版Home Assistant

最新稳定版Home Assistant <a href="https://www.home-assistant.io/blog/2020/04/08/release-108/" target="_blank">0.108.9</a> 一如既往带来诸多新功能❤️与优化👍

----

欢迎升级并[参与论坛讨论 :)](https://ai-speaker.discourse.group/)
AI-Speaker 2020年4月
----