---
author: Jola AI-Speaker
authorURL: https://github.com/sviete
author_title: Asystentka
authorImageURL: https://avatars3.githubusercontent.com/u/43966761?s=460&v=4
title: Wersja systemu Franek
tags: ["ais dom", "home assistant", "zigbee2mqtt", "ais-tasmota"]
---

<div class="IntroAisBlogMenu" >
<div>

![AIS](/img/en/blog/202104/franek.png)

</div>

<h2>Franek</h2>

</div>

![DEV3](/img/en/blog/202104/dev3.png) DEV3 ![AIS Commands](/img/en/blog/202104/commands.png) 语音指令 ![AIS Tasmota](/img/en/blog/202104/robot.png) 自动化场景

<!--truncate-->

## 无忧升级指南

:::tip[备份]
### ![A](/img/en/blog/202009/alpha-a-circle.png) 备份

注意：升级前强烈建议先进行[配置备份](/docs/ais_bramka_configuration_software#kopia-zapasowa-konfiguracji)。这能帮助您在升级前验证配置有效性，大幅降低升级故障概率。
:::

:::important[网关控制台与日志]
### ![B](/img/en/blog/202009/alpha-b-circle.png) 网关控制台与日志

若遇升级问题，请参考[控制台手动升级指南](/docs/ais_bramka_update_manual)或[应用完全重置步骤](/docs/ais_bramka_reset_ais_step_by_step)。
特别提醒安装了非标准组件的用户需重点关注此环节。
:::

:::caution[耐心等待]
### ![C](/img/en/blog/202009/alpha-c-circle.png) 耐心。升级后首次启动耗时较长——请保持耐心。

**升级完成后的首次启动可能长达20分钟。**
此时系统正在更新网关集成库并将数据库迁移至新格式。
**请耐心等待升级流程完成。**
:::

## ![](/img/en/blog/202104/franek.png) Franek版本

本次版本更新涉及软件包较少（Python 3.9.4仍保留在apt测试库中，将于下月正式发布）。更小的更新范围意味着更低的故障率 :) 若遇自动升级问题，用户始终可通过完全重置应用——下载包含最新默认代码的基础安装包来解决。

这个听似骇人的"应用完全重置"操作，其实类似于安卓系统的恢复出厂设置...实际操作远没有想象中可怕 :) 
完整操作指南详见：[应用完全重置步骤](/docs/ais_bramka_reset_ais_step_by_step)

若升级过程中遇到困难，可联系Celina获取[AI-Speaker设备编程服务](https://ai-speaker.discourse.group/t/usluga-programowania-urzadzen-w-ai-speaker/1368)。

**您将获得由Jolka亲自编程、搭载AI-Speaker最新固件的设备！**

论坛上有详细说明：[AI-Speaker设备编程服务](https://ai-speaker.discourse.group/t/usluga-programowania-urzadzen-w-ai-speaker/1368)

### ![](/img/en/blog/202104/commands.png) 语音触发的自动化 - 别名功能

在上个版本中，我们展示了添加自定义语音命令的最简单方式——在自动化名称前添加前缀"Jolka: [自定义指令]"。

![命令操作示例](/img/en/frontend/jolka-assistant-automation.jpeg)

现在我们将功能进一步升级：

- 支持命令/指令别名功能，使得同一个自动化可通过多个不同命令触发：
![带别名的命令操作示例](/img/en/frontend/jolka-assistant-automation-aliases.jpeg)

- 可覆盖内置命令

:::caution[注意]
**从本版本起，用户添加的命令具有最高优先级，将覆盖系统内置命令。**
这意味着每位用户都能完全定制助手行为，甚至可以自行编程实现诸如报时等功能的响应逻辑。
:::

![](/img/en/blog/202104/kot1.jpeg)

详见文档：[添加语音命令](/docs/ais_app_assistent_add_command/)

### ![](/img/en/blog/202104/robot.png) Tasmota 9.4.0 Leslie版

实现本地全控制，支持快速配置与更新。通过MQTT、网页界面及HTTP协议控制设备。
这是为**ESP8266**设备开发的极致可扩展、灵活、开源且日益稳定的固件新版本。
[目前已支持**1940**种设备](https://templates.blakadder.com/index.html)。
本次更新加入了WiFi网络连接配置器，其专业程度足以媲美商业产品。

更多讨论请访问我们的论坛：

[![](/img/en/blog/202104/tasmota.jpeg)](https://ai-speaker.discourse.group/t/tasmota-v9-4-0-leslie/1703)

### ![](/img/en/blog/202102/honeybee.png) Zigbee2Mqtt

Zigbee2Mqtt更新至1.8.2版本，支持设备超过**1400**种。
此为修复版本，完整更新日志参见[1.18.2](https://github.com/Koenkk/zigbee2mqtt/releases/tag/1.18.2)

![z2m](/img/en/blog/202103/z2m.png)

若您的Zigbee适配器遇到问题，正如我们之前提到的——我们已推出设备编程服务，论坛详情：

[![](/img/en/blog/202102/ais_devices_suport.png)](https://ai-speaker.discourse.group/t/usluga-programowania-urzadzen-w-ai-speaker/1368)

### ![](/img/en/blog/202101/hass.png) 家庭助理

最新版家庭助理，即我们的`ais-dom`软件包，基于最新稳定版Home Assistant Core构建。

![家庭助理](/img/en/blog/202104/social.png)

Home Assistant的详细变更说明可查阅项目博客：[2021.4: 面向高级用户](https://www.home-assistant.io/blog/2021/04/07/release-20214/)

最重大的改进是新增了自动化执行追踪功能。下方截图展示了某次自动化运行的轨迹。系统通过交互式流程图呈现自动化执行路径，图中每个节点均可点击查看该步骤的详细执行情况。👏 为HA团队点赞！这个设计非常出色！

![](/img/en/blog/202104/trace.jpeg)

## ![](/img/en/blog/202103/dev3.png) DEV3

我们已将新型网关**AIS DEV3**正式纳入产品线——这是目前配置最简单、运行最迅捷的AIS网关。

![AIS dom DEV2](/img/en/bramka/ais_dev3_in_box.jpg)

新网关参数详见：[AIoT网关](/docs/ais_bramka_index)，我们还新增了配置向导来简化[首次启动](/docs/ais_bramka_first_run_the_gate)流程。诚意推荐！这款硬件性能卓越，未来两年我们将共同探索其无限可能。

-------

##### AI-Speaker 2021年4月版