---
author: Jola AI-Speaker
authorURL: https://github.com/sviete
author_title: Asystentka
authorImageURL: https://avatars3.githubusercontent.com/u/43966761?s=460&v=4
title: Wersja systemu Hugo
tags: ["ais dom", "mqtt", "tts", "home assistant", "zigbee", "tasmota", "zwave"]
---

<div>

![AIS](/img/en/blog/202106/tts_local.png)

</div>

<!--truncate-->

## 无忧升级指南

:::tip[备份]
### ![A](/img/en/blog/202009/alpha-a-circle.png) 备份

注意：升级前建议先进行[配置备份](/docs/ais_bramka_configuration_software#kopia-zapasowa-konfiguracji)。通过这种方式可以在升级前验证配置的正确性，提高升级成功率。
:::

:::important[网关控制台与日志]
### ![B](/img/en/blog/202009/alpha-b-circle.png) 网关控制台与日志

若升级遇到问题，请查阅[控制台手动升级指南](/docs/ais_bramka_update_manual)或[应用完全重置步骤](/docs/ais_bramka_reset_ais_step_by_step)。
此操作尤其适用于在网关上安装了额外非标准组件的用户。
:::

:::caution[耐心等待]
### ![C](/img/en/blog/202009/alpha-c-circle.png) 耐心等待。升级及升级后的首次启动耗时较长——请保持耐心。

**升级后首次启动可能耗时较长。**
此时系统正在更新网关已安装集成所需的库文件。
**请耐心等待升级完成。
可通过控制台命令``htop``或``pm2 logs``查看系统启动状态（了解当前运行进程）**
:::

## ![](/img/en/blog/202106/hugo.png) Hugo

### 🆓 免费云服务 ☁️

我们DEV网关的云服务由fosshost.org组织托管。

![](/img/en/blog/202106/fosshost_big.png)

Fosshost是一家专注于支持开源项目的非营利机构。

更多关于AIS免费服务的说明详见文档：[远程服务条款](/docs/ais_dom_cloud_services_terms)

### zWave与Zigbee

本版本起支持同时使用两个适配器。系统将自动识别``/dev/ttyACM...``端口的适配器，并调整服务设置及启动相应服务。

更多集成信息请查阅文档：[Zwave](/docs/ais_app_integration_zwave) 和 [Zigbee](/docs/ais_app_integration_zigbee)

![](/img/en/blog/202106/zwave.png)

### USB设置

在配置中可选择是否让系统自动识别USB适配器并启动默认Zigbee/Zwave服务，以及是否通过语音通知USB设备的插拔状态。

![](/img/en/blog/202106/usb.png)

若您希望使用除我们标准集成Zigbee2Mqtt和zWaveJs2Mqtt之外的其他zWave与Zigbee集成方案，只需关闭设备自动识别功能，即可根据需求自行配置集成模块。

[文档-网关配置-USB接口](/docs/ais_bramka_configuration_usb)

### 事件记录过滤

部分集成模块会高频记录事件并生成海量数据，因此我们要求必须定义数据库写入过滤器。该过滤器可指定需要入库的数据（include参数）和需排除的数据（exclude参数），命名规范与Home Assistant保持一致。标准配置中已提供包含所有可能属性的示例过滤配置。

![](/img/en/blog/202106/filtr.png)

更多信息详见文档[网关配置-日志与数据库](/docs/ais_bramka_configuration_logs_and_db)

### AIS本地TTS增强

![](/img/en/blog/202106/tts_local.png)

我们在博客中详解为何AIS网关的本地TTS适合专业场景应用：
[AIS专业级离线TTS系统](https://ai-speaker.discourse.group/t/ais-profesjonalny-offline-tts/1893)

由于其他智能音箱无法像AIS网关那样同步处理音乐播放与文本朗读（缺乏TTS功能），自本版本起我们将以音频形式向这些设备发送通知：

![](/img/en/blog/202106/tts.jpeg)

### Conbee2

我们已成为Conbee2在波兰的官方经销商

![](/img/en/blog/202106/ais.jpeg)

论坛详情：[Zigbee ConBee 2现已发售！](https://ai-speaker.discourse.group/t/zigbee-conbee-2-juz-w-sprzedazy/1844)

这还不是我们计划引入和支持的全部精彩产品——更多惊喜即将登场;)

![](/img/en/blog/202106/ais2.jpeg)

### ![](/img/en/blog/202102/honeybee.png) Zigbee2Mqtt

Zigbee2Mqtt已更新至1.9.1版本，支持超过**1490**种设备并提供波兰语界面：

![z2m](/img/en/blog/202106/zigbee2mqtt_pl.png)

完整更新日志参见[1.19.1版本](https://github.com/Koenkk/zigbee2mqtt/releases/tag/1.19.1)

### ![](/img/en/blog/202101/hass.png) 家庭助理

最新版家庭助理（即我们的`ais-dom`软件包）基于最新稳定版Home Assistant Core构建。此版本包含大量修复和库更新。**注意**：前端（Web应用）已升级至Lit 2.0（应用中的Web组件）：

https://lit.dev/

一如既往，本次更新不仅带来大量卓越改进，还包含若干突破性变更。

:::caution[Lit 2.0 - Web应用重大库更新]
### 我们所有的Web应用组件均已通过测试，可完美兼容Lit 2.0

若您使用自定义卡片或其他界面元素，需确保其开发者已适配Lit 2.0...否则可能导致该卡片在Web应用中无法正常显示。
:::

Home Assistant的详细变更说明请参阅项目博客：

[升级至Lit 2.0](https://developers.home-assistant.io/blog/2021/05/19/lit-2.0)

## 公告

### PRO START

我们正在文档中添加PRO网关的相关信息，这是其正式上市前的最后准备阶段。

![pro](/img/en/blog/202106/pro.png)

PRO不仅是新款高速网关，更是我们的全新商业模式，也是首款面向企业客户的产品方案，支持功能定制和服务保障。

待文档补充完成后（预计本周末前），我们将详细介绍PRO的更多细节。

-------------------------------------------------------------------------

### ![](/img/en/blog/202105/placard.png) AIS DEV3

我们已将新款**AIS DEV3**网关正式纳入产品线——这是目前速度最快、配置与操作最简便的AIS网关。

AIS DEV3网关开箱后数分钟即可实现语音控制设备，内置音频支持功能，并通过用户界面实现远程访问与配置。使用AIS DEV3无需再烧录SD卡系统、调整路由器设置，也无需了解动态DNS或YAML配置。当然，所有功能均无月费且应用内无广告。

![AIS dom DEV3](/img/en/bramka/ais_dev3_in_box.jpg)

听听Hugo对AIS DEV3网关的评价：

:::tip[Hugo]

"AIS DEV3的运行体验非常出色！这款设备性能强大且功能丰富！我真诚推荐大家使用。"

:::

![Greta](/img/en/blog/202106/hugo.png)

新网关的参数详情请参阅：[AIoT网关](/docs/ais_bramka_index)，我们还新增了配置向导以简化[首次启动](/docs/ais_bramka_first_run_the_gate)流程。

-------

##### AI-Speaker 2021年6月版