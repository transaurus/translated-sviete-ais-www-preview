---
author: Jola AI-Speaker
authorURL: https://github.com/sviete
author_title: Asystentka
authorImageURL: https://avatars3.githubusercontent.com/u/43966761?s=460&v=4
title: Wersja systemu Asia
tags: ["google calendars", "home assistant", "automatyzacje", "zigbee2mqtt", "tasmota"]
---

# 亚洲 ![](/img/en/blog/202012/asia.png)

- ![AIS NBP](/img/en/blog/202012/nbp.png) AIS 波兰国家银行
- ![AIS LTS](/img/en/blog/202012/handshake.png) AIS 长期支持版
- ![AIS 日历](/img/en/blog/202011/ais_calendar.png) AIS 日历
- ![Zigbee](/img/en/blog/202007/zigbee.png) Zigbee2Mqtt 1.16.2
- ![Home Assistant](/img/en/blog/202007/hass.png) AIS HA 0.118.5 + Home Assistant 开发者大会

<!--truncate-->

## 无忧升级指南

:::tip[备份]
### ![A](/img/en/blog/202009/alpha-a-circle.png) 备份

注意 升级前建议先执行[配置备份](/docs/ais_bramka_configuration_software#kopia-zapasowa-konfiguracji)。这能帮助您在升级前验证配置的正确性，大幅降低升级失败风险。
:::

:::important[网关控制台与日志]
### ![B](/img/en/blog/202009/alpha-b-circle.png)网关控制台与日志

若升级遇到问题，请参考[通过控制台升级](/docs/ais_bramka_update_manual)或[执行应用完全重置](/docs/ais_bramka_reset_ais_step_by_step)流程。
特别是安装了非标准组件的用户需重点关注此项。
:::

:::caution[耐心等待]
### ![C](/img/en/blog/202009/alpha-c-circle.png) 耐心。升级后首次启动耗时较长 - 请保持耐心。

 **升级后的首次启动可能长达20分钟。**
 在此期间会更新网关集成库并将数据库迁移至新格式。
 **请耐心等待升级完成。**
:::

## ![](/img/en/blog/202012/asia.png) 亚洲

#### 从本版本起，系统版本号将改用名称命名。

我们将系统版本命名为**Asia（亚洲）**，既非指代英国乐队Asia，也不是编号67的小行星，更不是古罗马的亚细亚行省，亦非希腊神话中的海洋女神...

在我们看来，**Asia**是Joanna的昵称。根据[维基百科](https://pl.wikipedia.org/wiki/Joanna)，这个源自希伯来语Jo-hanan（意为"上帝是仁慈的"）的女性名字，对应英文名Jan的变体。

改用名称命名的初衷，是让用户更容易记住系统版本。
就像我们更容易记住把车停在"刺猬停车场"，而非"108/5号停车场"。

欢迎使用**亚洲**系统，诚邀您立即升级 :)

### ![](/img/en/blog/202012/nbp.png) AIS - 波兰国家银行

我们新增了AIS NBP集成功能，具体操作说明详见文档：[AIS 波兰国家银行](/docs/ais_app_ai_integration_nbp)

![AIS NBP配置界面](/img/en/frontend/ais_nbp6.png)

更重要的是，该集成功能的开发过程已在论坛[编程专区](https://ai-speaker.discourse.group/c/programowanie/15)以分步教程形式详细记录
![](/img/en/blog/202012/programowanie.png)

集成模板已发布至GitHub仓库[AIS-hello](https://github.com/sviete/AIS-hello)。这是传感器/计数器的最小化实现方案，可作为自定义集成的开发模板。

![AIS Hello示例](/img/en/blog/202012/ais-hello.png)

#### 这意味着任何有时间、有创意且愿意学习新技术的人，都可以添加自己的集成功能。

### ![](/img/en/blog/202012/handshake.png) AIS长期支持版

我们当前的重点项目之一是建立长期支持机制，旨在提供预装二进制文件的设备版本，该版本将获得未来数年的持续维护。

最重大的更新是支持至2025年的Python 3.9：

![AIS LTS版本Python支持](/img/en/blog/202012/python.png)

论坛已发布完整的[LTS迁移指南](https://ai-speaker.discourse.group/t/ais-lts-long-time-support-dlugoterminowe-wsparcie/1013)。

执行[应用程序完全重置](/docs/ais_bramka_reset_ais_step_by_step)的用户将自动获取新版二进制文件，无需手动安装，因为我们已将其加入最新启动代码包(bootstrap)。

![AIS LTS启动包](/img/en/blog/202012/bootstrap.png)

升级至新版二进制文件完全自愿 :) 即便不升级，未来几个版本仍可正常使用和更新。数月后我们将终止对Python 3.7的支持，届时仍运行Python 3.7的系统将无法更新，我们会提前发布相关通知。

### ![](/img/en/blog/202011/ais_calendar.png) AIS日历

我们已获得Google日历API的使用授权。

![AIS日历功能](/img/en/blog/202012/calendar.png)

我们改进了集成功能的多个细节，后续版本将继续简化和优化，使日历成为系统的核心功能组件。

### ![](/img/en/blog/202007/zigbee.png) Zigbee2Mqtt 1.16.2

修复改进及新增设备支持。完整版本说明详见项目页面 [Zigbee2Mqtt](https://github.com/Koenkk/zigbee2mqtt/releases/tag/1.16.2)

![](/img/en/blog/202012/z2m.png)

### ![](/img/en/blog/202007/hass.png) AIS HA 0.118.5

AIS HA已升级至最新稳定版Home Assistant 0.118.5，包含大量功能改进与新增特性。完整更新清单请访问项目主页：[Home Assistant 0.118.5](https://www.home-assistant.io/blog/2020/11/18/release-118/)

![Home Assistant](/img/en/blog/202012/ha-social.png)

## ![](/img/en/blog/202007/hass.png) Home Assistant开发者大会

12月13日（本周日）将举办全球最大的开源家庭自动化平台Home Assistant开发者大会。

![Home Assistant](/img/en/blog/202012/conference-header.png)

大会将呈现多个精彩议题，完整议程请查看[Home Assistant Conference](https://hopin.com/events/home-assistant-conference#schedule)

### Home Assistant Core 1.0正式发布！ :)

本次大会将宣布Home Assistant Core 1.0版本发布，标志着历时7年的Beta阶段圆满结束，我们对此深感振奋。

### 2021年度计划与展望

下周我们将解读HA大会的重要公告（可能影响系统发布周期），并同步发布**2021年度发展规划与路线图**。

----

欢迎升级系统并[参与论坛讨论 :)](https://ai-speaker.discourse.group/)

##### AI-Speaker 2020年12月