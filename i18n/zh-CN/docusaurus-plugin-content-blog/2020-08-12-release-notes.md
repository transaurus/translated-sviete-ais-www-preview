---
author: Jola AI-Speaker
authorURL: https://github.com/sviete
author_title: Asystentka
authorImageURL: https://avatars3.githubusercontent.com/u/43966761?s=460&v=4
title: Wersja systemu 0.113.4
tags: ["location", "gps", "demo", "home assistant", "zigbee2mqtt", "apk api"]
---

# 0.113.4 小雅在哪里？

- ![GPS](/img/en/blog/202008/spy.png) 地址上报功能 [...](/blog/2020/08/12/release-notes#location-raportowanie-adresu)
- ![Komendy](/img/en/blog/202007/mobile-request.png) 远程查询人员实时位置 [...](/blog/2020/08/12/release-notes#komendy-zdalne-zapytania-i-komendy) 
- ![Demo](/img/en/blog/202008/demo_icon.png) 应用演示版 [...](/blog/2020/08/12/release-notes#demo-demo-aplikacji)
- ![Tasmota](/img/en/blog/202005/tasmota_small.png) Tasmota 8.4.0 George固件 [...](/blog/2020/08/12/release-notes#tasmota-tasmota-840-george)
- ![Zigbee](/img/en/blog/202007/zigbee.png) Zigbee2Mqtt 1.14.2 [...](/blog/2020/08/12/release-notes#zigbee-zigbee2mqtt-1142)
- ![EXTA LIFE](/img/en/blog/202007/exta_life.png) EXTA LIFE集成最新版本 [...](/blog/2020/08/12/release-notes#exta-life-najnowsza-wersja-integracji-exta-life)
- ![Home Assistant](/img/en/blog/202007/hass.png) Home Assistant 1.13.3 [...](/blog/2020/08/12/release-notes#home-assistant-nowy-home-assistant)

<!--truncate-->

## 无忧升级指南

:::tip[A 备份配置]
重要提示：升级前建议先执行[配置备份](/docs/ais_bramka_configuration_software#kopia-zapasowa-konfiguracji)。通过此操作可在升级前验证配置的正确性，显著提高升级成功率。
:::

:::important[B 控制台与日志]
若升级遇到问题，请查阅[通过控制台升级](/docs/ais_bramka_update_manual)或[执行应用完全重置](/docs/ais_bramka_reset_ais_step_by_step)流程说明。
特别是为网关安装了非标准组件的用户需特别注意此项。
:::

:::caution[C 升级后首次启动]
 **升级后的首次启动过程可能持续长达20分钟。**
 在此期间，网关将更新已安装集成所需的依赖库，并将数据库迁移至新格式。
 **请耐心等待升级完成。**
:::

## ![Location](/img/en/blog/202008/spy.png) 地址上报功能

家庭助理系统提供多种存在检测方案。我们理解并非所有用户都能掌握webhook、API等技术细节，因此新增了通过AIS dom应用直接向家庭网关上报位置的简易方案。

![Location](/img/en/blog/202008/presence_detection_00.png)

文档中详细说明了如何配置[存在检测及创建基于地理围栏的自动化](/docs/ais_bramka_presence_detection)。

我们还新增了[人员位置查询](/docs/ais_app_assistent_commands/#sprawdzenie-lokalizacji-osoby)指令，只需询问

```text
Gdzie jest {osoba}
```

或

```text
Lokalizacja {osoba}
```

即可获取实时位置信息。该数据来源于与该人员关联的追踪设备上报至网关的最新定位信息。
系统会从应用程序传输包括人员地址（若可通过坐标解析）在内的多项定位数据，使得"某人在哪里"的应答更具信息量。

![Location](/img/en/blog/202008/person_info.png)

:::info[该功能需AIS dom应用1.4.4及以上版本]
是否传输地址数据取决于以下条件：

1. 是否授予AIS dom应用位置访问权限
2. 是否启用位置上报服务
3. 能否通过坐标解析出地址（若失败则仅传输GPS坐标数据）
:::

## ![Komendy](/img/en/blog/202007/mobile-request.png) 远程查询与指令

用户可通过网关向移动端发送指令，例如查询人员的实时位置。

网关提供``ais_ai_service.mob_request``服务，支持向**AIS dom**移动应用发送指令（查询/请求）。
通过自动化功能，用户可远程触发设备定位上报（开启临时位置追踪）。

完整指令说明详见文档《从网关发送至移动应用的指令》

:::caution[注意]
仅当移动设备已启用相应权限（麦克风/定位）时，登录网关的用户才能远程触发定位上报或麦克风启用指令。

系统会在通知栏明确显示远程指令的执行状态，确保设备所有者知情。
:::

## ![Demo](/img/en/blog/202008/demo_icon.png) 应用演示版

我们正在持续开发[家庭助理演示平台](https://demo.ai-speaker.com/)，用于展示系统核心功能。
计划通过独立界面呈现家庭助理中的基础实体*类型，包括：

*实体是设备（最常见）的抽象表示，每个实体定义了特定类型设备的功能集。通过这种方式，当用户了解了系统中如何控制例如IKEA品牌的灯泡后，就能明确PHILIPS等品牌的灯泡操作逻辑也将相同（无论设备制造商采用何种通信协议或API）。

![DEMO](/img/en/blog/202008/demo.png)

演示版设计为交互式体验——用户可点击控制设备，或通过语音指令测试功能。我们还计划通过实时摄像头展示系统操作的实际效果——演示环境连接了真实物理设备。

我们首批描述的实体类型包括：

- 空气质量传感器
- 报警控制面板  
- 二进制传感器
- 摄像头
- 气候控制
- 窗帘控制器
- 设备追踪器
- 风扇
- 灯光
- 门锁
- 媒体播放器
- 人员
- 遥控器
- 传感器
- 开关
- 吸尘器
- 热水器
- 天气

## ![Tasmota](/img/en/blog/202005/tasmota_small.png) Tasmota 8.4.0 George版本

我们发布了基于ESP8266的物联网设备固件新版本。

本次更新包含多项改进与修复，完整说明详见论坛：
https://ai-speaker.discourse.group/t/ais-tasmota-v8-4-0-george/640

最大变更是增加了更多编译版本，所有变体均可在[Github FIRMWARE](https://github.com/sviete/AIS-Tasmota/tree/firmware)仓库获取。

![AIS Tasmota](/img/en/blog/202008/ais_tasmota.png)

新增了对ESP32的实验性支持，目前测试显示Tasmota在ESP32平台上的稳定性和功能扩展性优于其他解决方案。期待这能为智能家居助手带来更多创新功能 :)
![AIS ESP32](/img/en/blog/202008/ESP32.png)

## ![Zigbee](/img/en/blog/202007/zigbee.png) Zigbee2Mqtt 1.14.2版本

主要是功能修复，同时新增设备支持。完整更新日志参见：
[![AIS zigbee2mqtt](/img/en/blog/202008/zigbee2mqtt.png)](https://github.com/Koenkk/zigbee2mqtt/releases/tag/1.14.2)

## ![EXTA LIFE](/img/en/blog/202007/exta_life.png) EXTA LIFE集成最新版本

引用dgtal1的说明：

> 此版本包含多项修复，并新增对Exta Free系列设备的支持——这些是EFC-01控制器官方兼容的设备。
完整变更日志：
[![AIS exta](/img/en/blog/202008/exta.png)](https://github.com/dgtal1/extalife_custom_component/releases/tag/2.0b2)

## ![Home Assistant](/img/en/blog/202007/hass.png) 新版Home Assistant

最新稳定版[Home Assistant 0.113.3](https://www.home-assistant.io/blog/2020/07/22/release-113/)
自动化功能修复 - 详见我们的论坛讨论：https://ai-speaker.discourse.group/t/0-113-beta-wydana/594

![Home Assistant](/img/en/blog/202008/ha_0.13.3.png)

----

欢迎升级并[参与论坛讨论 :)](https://ai-speaker.discourse.group/)
AI-Speaker 2020年7月
----