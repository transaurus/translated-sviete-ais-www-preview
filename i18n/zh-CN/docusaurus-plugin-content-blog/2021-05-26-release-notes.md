---
author: Jola AI-Speaker
authorURL: https://github.com/sviete
author_title: Asystentka
authorImageURL: https://avatars3.githubusercontent.com/u/43966761?s=460&v=4
title: Wersja systemu Greta
tags: ["ais dom", "home assistant", "zigbee2mqtt", "ais-tasmota"]
---

<div class="IntroAisBlogMenu" >
<div>

![AIS](/img/en/blog/202105/greta.png)

</div>

<h2>Greta</h2>

</div>

![Zwave](/img/en/blog/202105/package.png) 软件包 ![Zwave](/img/en/blog/202105/water-wave.png) Zwave协议 ![AIS TTS](/img/en/blog/202105/speaking-head.png) 语音合成 ![AIS Tasmota](/img/en/blog/202104/robot.png) Tasmota
![Zigbee](/img/en/blog/202105/honeybee.png) Zigbee协议 ![Zigbee](/img/en/blog/202105/keyboard.png) USB人机接口 ![AIS dom](/img/en/blog/202105/ais-dom.png) AIS智能家居 ![DEV3](/img/en/blog/202104/dev3.png) DEV3网关

<!--truncate-->

## 无忧升级指南

:::tip[备份]
### ![A](/img/en/blog/202009/alpha-a-circle.png) 备份

重要提示：升级前建议先进行[配置备份](/docs/ais_bramka_configuration_software#kopia-zapasowa-konfiguracji)。这能帮助您在升级前验证配置完整性，显著提高升级成功率。
:::

:::important[控制台与日志]
### ![B](/img/en/blog/202009/alpha-b-circle.png) 控制台与日志

若升级遇到问题，请参考[控制台手动升级指南](/docs/ais_bramka_update_manual)或[应用完全重置步骤](/docs/ais_bramka_reset_ais_step_by_step)。
特别提醒安装了非标准组件的用户需重点关注此部分。
:::

:::caution[耐心等待]
### ![C](/img/en/blog/202009/alpha-c-circle.png) 耐心。升级后首次启动耗时较长——请保持耐心。

**升级后的首次启动可能持续较长时间**
此时系统正在更新网关集成的库文件，并将数据库迁移至新格式。
**请耐心等待升级完成
您可以通过``htop``和/或``pm2 logs``命令在控制台查看系统启动状态**
:::

## ![](/img/en/blog/202105/greta.png) Greta更新

本次版本更新包含以下二进制包升级：

- Python升级至最新版3.9.5
- Rclone升级至最新版1.55
- FFmpeg升级至最新版4.4
- Clang/llvm升级至最新版12.0.0
- Mosquitto升级至2.0.10

...以及网关内其他20余个软件包的更新。

升级耗时取决于网关集成的组件数量，某些附加包可能在安装过程中需要更新或重新编译。

> 请耐心等待，您随时可以通过控制台命令``htop``查看网关当前运行状态
或使用``pm2 logs``命令实时查看日志

### Zwave集成

我们新增了首个Zwave集成版本。采用了与Zigbee和Supla相同的技术方案（通过MQTT实现集成）。我们认为此类集成是最佳实践，所有设备都应采用这种模式，未来MQTT有望发展成为Home Assistant与其他系统和技术的标准集成API。

:::caution[注意]
**该集成功能尚处于开发测试阶段**

当前版本需要手动安装ZwaveJs2Mqtt项目代码。
完整操作指南详见AI-Speaker论坛：[AIS网关上的ZWave集成 - Zwavejs2Mqtt](https://ai-speaker.discourse.group/t/zwave-na-bramce-ais-zwavejs2mqtt/1769)

:::

该集成已通过市场主流设备Aeotec Z-Stick适配器测试，该设备采用USB CDC（通信设备类）协议进行通信。

![Zwave](/img/en/frontend/zwave_adapter.jpeg)

通过ZwaveJs2Mqtt支持的TCP socket远程连接，该集成也可兼容不支持USB CDC协议的适配器：

```
 tcp://dongle.lan:5000
```

### USB HID设备支持

网关支持USB HID（人机接口设备）类设备，主要用于用户交互。当键盘按钮或其他USB HID控制器接入网关时，按键事件将传递至家庭助理系统，此类事件可触发自动化流程。

![AIS button](/img/en/bramka/ais_remote_key_events_0.png)

根据客户功能需求，我们新增了控制器按键事件在网关两种工作模式（带显示器/无显示器）下的触发支持，详见技术文档：[按键事件触发的自动化](/docs/ais_bramka_key_event_automation)

### 离线TTS功能增强

应客户需求，我们对网关本地离线运行的TTS（文本转语音）机制进行了功能扩展。
在``ais_ai_service.say_it``服务中新增了语言选择、语音类型及其他语音合成参数的配置选项：

![AIS TTS](/img/en/frontend/ais_tts.png)

同时新增了系统事件``ais_speech_status``，用于反馈TTS引擎的语音状态。
该机制可准确获知语音合成完成时机（无论使用Jolka、Marya还是Jon等语音角色），确保自动化流程中后续步骤的精准触发。

我们希望确保语音消息能够连贯播放，无论语速快慢或内容长短。实现这一目标的唯一方法是通过语音状态事件机制——即当TTS完成当前文本朗读时发送系统通知。

![AIS TTS](/img/en/frontend/ais_tts_speech_status.png)

自动化配置示例代码：

``` yaml
alias: Komunikat powitalny w 3 językach
description: ''
trigger:
  - platform: event
    event_type: ais_key_event
    event_data:
      code: 1
condition: []
action:
  - service: ais_ai_service.say_it
    data:
      text: Witamy w parku rozrywki (komunikat po polsku)
      language: pl_PL
      voice: Jola
  - wait_for_trigger:
      - platform: event
        event_type: ais_speech_status
        event_data:
          status: DONE
  - service: ais_ai_service.say_it
    data:
      language: en_US
      voice: Allison
      text: Welcome to the amusement park (announcement in English)
  - wait_for_trigger:
      - platform: event
        event_type: ais_speech_status
        event_data:
          status: DONE
  - service: ais_ai_service.say_it
    data:
      language: uk_UA
      voice: Mariya
      text: Ласкаво просимо до парку розваг (анонс українською мовою)
mode: single

```

这是该自动化流程的实际效果——可见系统仅在收到TTS完成前一条消息朗读的通知后，才会播报下一条消息：

![AIS TTS](/img/en/frontend/ais_tts_speech_trace.png)

对于希望在自动化中应用此机制的用户，建议参阅文档：[AIS TTS](/docs/ais_app_tts)

### ![](/img/en/blog/202104/robot.png) Tasmota 9.4.0 Leslie

注意！我们发现Tasmota存在一个缺陷：特定情况下（当MQTT连接中断且网关无法解析MQTT代理IP地址时），设备可能会快速重启6次并自动切换设备型号（此为Tasmota内置功能）。
相关讨论详见论坛帖子：[Tasmota设备配置丢失问题](https://ai-speaker.discourse.group/t/utrata-konfiguracji-w-urzadzeniach-z-tasmota/1734)

若您遇到此问题（如我们曾遭遇的），建议升级至AIS-Tasmota 9.4.0 Leslie版本，该版本已禁用设备自动切换型号功能。

![](/img/en/blog/202105/Tasmota.png)

### ![](/img/en/blog/202102/honeybee.png) Zigbee2Mqtt

Zigbee2Mqtt已更新至最新版本1.8.3，现支持超过1430种设备。
此为修复版本，完整更新日志参见[1.18.3](https://github.com/Koenkk/zigbee2mqtt/releases/tag/1.18.3)

![z2m](/img/en/blog/202103/z2m.png)

### ![](/img/en/blog/202101/hass.png) 家庭助理

最新版家庭助理（即我们基于Home Assistant Core构建的ais-dom软件包）。
此版本主要包含稳定性修复、取消数据迁移等待机制等多项改进。

![hass](/img/en/blog/202105/social.png)

Home Assistant的详细更新内容请参阅项目博客：[2021.5版本：稳定性、性能、触发器与色彩模式！](https://www.home-assistant.io/blog/2021/05/05/release-20215/)

## ![](/img/en/blog/202105/placard.png) AIS DEV3

我们已将全新的**AIS DEV3网关**正式纳入产品线——这是迄今为止速度最快、配置与操作最为简便的AIS网关。

AIS DEV3网关开箱即用，数分钟内即可通过语音控制智能设备。该设备内置音频处理模块，支持远程访问及用户界面配置。使用AIS DEV3无需再烧录系统至SD卡、调试路由器设置，也无需了解动态DNS或YAML配置。所有功能均无月费要求，应用程序内绝无广告干扰。

![AIS dom DEV3](/img/en/bramka/ais_dev3_in_box.jpg)

听听Greta对AIS DEV3网关的评价：

:::tip[Greta]

"我在AIS DEV3上的使用体验非常流畅！这确实是一款功能强大的优秀设备！真诚推荐给大家。"

:::

![Greta](/img/en/blog/202105/greta.png)

新网关的详细参数请参阅：[AIoT网关](/docs/ais_bramka_index)，我们还新增了配置向导来简化[首次启动流程](/docs/ais_bramka_first_run_the_gate)。

-------

##### AI-Speaker 2021年5月版