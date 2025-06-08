---
author: Jola AI-Speaker
authorURL: https://github.com/sviete
author_title: Asystentka
authorImageURL: https://avatars3.githubusercontent.com/u/43966761?s=460&v=4
title: Wersja systemu Ewa
tags: ["ais dom", "home assistant", "zigbee2mqtt"]
---

<div class="IntroAisBlogMenu" >
<div>

![AIS](/img/en/blog/202103/eva.png)

</div>

<h2>Ewa</h2>

</div>

![DEV3](/img/en/blog/202103/dev3.png) DEV3 ![AIS Python](/img/en/blog/202102/snake.png) Python3.9.2 ![AIS Zigbee2Mqtt](/img/en/blog/202102/honeybee.png) Zigbee2Mqtt ![AIS Radio](/img/en/blog/202103/radio.png) AIS音频

<!--truncate-->

## 无忧升级指南

:::tip[备份。]
### ![A](/img/en/blog/202009/alpha-a-circle.png) 备份配置

注意：升级前建议先执行[配置备份](/docs/ais_bramka_configuration_software#kopia-zapasowa-konfiguracji)。这能帮助您在升级前验证配置的正确性，大幅提高顺利升级的概率。
:::

:::important[网关控制台与日志。]
### ![B](/img/en/blog/202009/alpha-b-circle.png)网关控制台与日志

若升级遇到问题，请参照[通过控制台升级](/docs/ais_bramka_update_manual)或[执行应用完全重置](/docs/ais_bramka_reset_ais_step_by_step)流程处理。
此情况尤其可能发生在安装了非标准组件的网关设备上。
:::

:::caution[耐心等待。]
### ![C](/img/en/blog/202009/alpha-c-circle.png) 保持耐心。升级后首次启动耗时较长——请耐心等待。

 **升级后的首次启动可能长达20分钟。**
 在此期间，网关会更新所有集成组件的依赖库，并将数据库迁移至新格式。
 **请耐心等待升级完成。**
:::

## ![](/img/en/blog/202103/eva.png) 艾娃

本次版本更新了多个软件包，包括升级Python至3.9.2版本、mosquitto至2.0.7版本。
技术细节已发布在博客：[Python 3.9.2](https://ai-speaker.discourse.group/t/nowe-wersje-pakietow-binarnych-w-repozytorium-apt/1492) 与 [mosquitto 2.0.7](https://ai-speaker.discourse.group/t/broker-mqtt-nowe-mosquitto-2-0-7/1493)

同时更新了Android应用，使整个系统界面更美观，屏幕切换操作更直观。相关功能改进详见博客文章[启动优化](https://ai-speaker.discourse.group/t/aktualizacja-aplikacji-android-na-bramce-ulatwienia-na-starcie/1477)

我们深知这些软件中的"革命性变更"在安装过程中需要耐心。某些配置下甚至可能在安装时出现异常情况...对此我们已做好准备。若用户遇到自动更新问题，始终可通过执行完整应用重置——下载包含我们最新默认代码的初始安装包来解决。

完整操作步骤详见：[完整应用重置指南](/docs/ais_bramka_reset_ais_step_by_step)
这个听似严重的"完整应用重置"实际上类似于安卓应用的清除数据功能...真的没有想象中那么可怕 :)

![重置](/img/en/bramka/settings_ais_service_app_reset_1.jpeg)

当然我们理解并非所有人都能顺利完成——可能电视/显示器故障、网络中断、突然断电...或是干脆想让Jolka代劳！;)

好消息是：**Jolka热衷设备编程且乐意效劳 :) !**

:::caution[获得全面支持！]
若遇到任何问题请勿担忧，现在无需在论坛发帖求助"我的设备故障了"，也无需等待他人逐步指导如何查看日志或重复执行文档/论坛中已说明多次的流程...

遇到更新问题时，只需联系Celina启用[AI-Speaker设备编程服务](https://ai-speaker.discourse.group/t/usluga-programowania-urzadzen-w-ai-speaker/1368)，费用仅为象征性收取（用于包装和Jolka在便利店买咖啡）。

**您将获得由Jolka亲自编程、搭载AI-Speaker最新固件的设备！**

论坛详情：[AI-Speaker设备编程服务](https://ai-speaker.discourse.group/t/usluga-programowania-urzadzen-w-ai-speaker/1368)
:::

### 语音触发自动化

来自论坛话题[Jolka说了什么](https://ai-speaker.discourse.group/t/co-powiedziala-jolka/1544/14)的灵感催生了这项有趣功能。
现在添加自定义语音指令的最简方式——在自动化名称前添加"Jolka: [自定义指令]"前缀即可。

![指令操作示意](/img/en/frontend/jolka-assistant-automation.jpeg)

详情参见[添加语音指令](/docs/ais_app_assistent_add_command/)

### 媒体资源添加

现在可通过简易表单轻松添加网络电台，新增的媒体资源还可共享给其他用户：

![添加电台](/img/en/frontend/ais_add_media_3.png)

详情请见[添加媒体](/docs/ais_app_add_media)

### 选择器

现在无需在YAML中手动输入标识符来调用服务，只需在表单中填写或从列表选择数值即可。这将大幅减少错误发生率 👍  
该机制不仅适用于开发者工具，还将应用于自动化模板、脚本和场景配置。

![](/img/en/blog/202103/selektory.png)

### ![](/img/en/blog/202102/honeybee.png) Zigbee2Mqtt

已升级至Zigbee2Mqtt 1.8.1最新版本  
新增控制面板、多项修复、支持新设备，完整更新日志详见[1.18.1](https://github.com/Koenkk/zigbee2mqtt/releases/tag/1.18.1)

![z2m](/img/en/blog/202103/z2m.png)

若您的Zigbee适配器遇到问题，我们已提供设备编程服务（详情见论坛）：

[![](/img/en/blog/202102/ais_devices_suport.png)](https://ai-speaker.discourse.group/t/usluga-programowania-urzadzen-w-ai-speaker/1368)

### ![](/img/en/blog/202101/hass.png) 家庭助理

最新版家庭助理「ais-dom」套件基于当前最稳定的Home Assistant Core构建。

![家庭助理](/img/en/blog/202103/social.png)

Home Assistant的详细更新内容请参阅官方博客：[2021.3: My Oh My](https://www.home-assistant.io/blog/2021/03/03/release-20213/)

## ![](/img/en/blog/202103/dev3.png) DEV3

我们推出全新DEV3网关——这是目前配置最简单、运行最快速的AIS网关设备。

该设备在论坛首发[DEV3 - 全新AIoT网关现已上市](https://ai-speaker.discourse.group/t/dev3-nowa-bramka-aiot-juz-jest/1496)时遭遇"小插曲"，其顶盖被发现存在易凹陷问题。

![](/img/en/blog/202103/dev3_dekielek.png)

我们已暂停销售并更换为更坚固的新顶盖，目前新部件正在运输途中：

![](/img/en/blog/202103/dekielek1.png)

复活节假期结束后，我们将有序恢复销售并提供"顶盖更换"服务。

新网关的参数在此处描述：[AIoT网关](/docs/ais_bramka_index)，我们还新增了一个配置工具以简化[首次启动](/docs/ais_bramka_first_run_the_gate)流程。

-------

**值此复活节来临之际，我们衷心祝愿您度过一个健康、祥和、充满爱的节日。**

![AIS](/img/en/blog/202103/eva.png)

**复活节平安喜乐。**

##### AI-Speaker 2021年3月版