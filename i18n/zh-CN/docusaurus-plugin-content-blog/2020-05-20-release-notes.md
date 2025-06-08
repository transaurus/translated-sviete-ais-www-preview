---
author: Jola AI-Speaker
authorURL: https://github.com/sviete
author_title: Asystentka
authorImageURL: https://avatars3.githubusercontent.com/u/43966761?s=460&v=4
title: Wersja systemu 0.109.7
tags: [:notifications", "tasmota", "zigbee", "home assistant"]
---

# 0.109.7 通知、Tasmota、Zigbee

- ![通知](/img/en/blog/202005/megaphone.png) 来自网关的通知...无限制！ :)
- ![Tasmota](/img/en/blog/202005/tasmota_small.png) 更新WiFi设备固件AIS-Tasmota，[支持1261种设备](https://templates.blakadder.com/index.html)
- ![Zigbee](/img/en/blog/202004/honeybee.png) 更新Zigbee2Mqtt，[支持133个厂商的741种设备](https://www.zigbee2mqtt.io/information/supported_devices.html)
- ![SUPLA](/img/en/blog/202005/supla.png) 配置SUPLA服务的查询频率
- ![图标](/img/en/blog/202004/house.png) 新版Home Assistant

<!--truncate-->

:::tip[提示]
注意：建议在升级前[备份配置](/docs/ais_bramka_configuration_software#kopia-zapasowa-konfiguracji)。通过这种方式可以在升级前验证配置的正确性，提高顺利升级的概率。
:::

:::important[重要信息]
若升级后遇到问题，请查阅[控制台升级指南](/docs/ais_bramka_update_manual)或[执行应用完全重置](/docs/ais_bramka_reset_ais_step_by_step)——特别是那些在网关上安装了非标准组件的用户。
:::

:::caution[注意]
升级后建议重置界面默认配置，或手动修正实体`sensor.aisknowledgeanswer`的显示问题，详细说明见论坛：https://ai-speaker.discourse.group/t/beta-nowa-wersja-0-109-wydana-na-kanale-beta/423/47
:::

## ![通知](/img/en/blog/202005/megaphone.png) 网关通知功能

网关新增服务ais_ai_service.mob_notify，可通过自动化将通知推送至AIS dom移动应用。该功能允许用户通过移动应用接收家中事件的实时提醒。

通知数量无限制，支持附带图片和可朗读文本。完整功能说明详见文档《网关通知功能》

![通知](/img/en/frontend/gallery_notify_1.png)

![通知](/img/en/frontend/gallery_notify_4.png)

:::caution[注意]
需使用AIS dom移动应用v1.1.8及以上版本。
:::

:::caution[注意]
首次使用需在移动应用中重新登录以激活通知功能。
:::

我们采用了基于IndieAuth机制的新认证方案。
![通知认证](/img/en/blog/202005/mob_auth.png)

## ![Tasmota](/img/en/blog/202005/tasmota_small.png) AIS-Tasmota更新

这次我们提供了两个二进制版本，因为我们将不同设备（插座、卷帘、触摸面板等）上的常用功能整合到了一个编译版本中。也就是说，这个单一编译版本包含了所有常用功能，可以在所有模块上运行。

![网关软件](/img/en/iot/iot_device_menu.png)

## ![Zigbee](/img/en/blog/202004/honeybee.png) 更新Zigbee2Mqtt至1.13.0版本

### [支持133个不同厂商的741款设备](https://www.zigbee2mqtt.io/information/supported_devices.html) 🥰

Zigbee的更新与其他组件一样，将自动完成。

![网关软件](/img/en/blog/202005/update.png)

## ![SUPLA](/img/en/blog/202005/supla.png) 配置SUPLA服务的查询频率

我们为SUPLA集成添加了扫描间隔定义功能。用户可根据设备数量和SUPLA当前限制，自定义设备状态查询频率。详情参阅文档[SUPLA集成](/docs/ais_app_supla)

![SUPLA](/img/en/blog/202005/supla_limit.png)

## ![图标](/img/en/blog/202004/house.png) 新版Home Assistant

最新稳定版Home Assistant <a href="https://www.home-assistant.io/blog/2020/04/29/release-109/" target="_blank">0.109.6</a> 依然带来诸多新特性 ❤️

----

欢迎升级并[参与论坛讨论 :)](https://ai-speaker.discourse.group/)
AI-Speaker 2020年5月
----