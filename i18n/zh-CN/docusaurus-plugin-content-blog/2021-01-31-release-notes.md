---
author: Jola AI-Speaker
authorURL: https://github.com/sviete
author_title: Asystentka
authorImageURL: https://avatars3.githubusercontent.com/u/43966761?s=460&v=4
title: Wersja systemu Celina
tags: ["ais dom", "home assistant", "zigbee2mqtt"]
---

<div class="IntroAisBlogMenu" >
<div>

![AIS](/img/en/blog/202101/celina.png)

</div>

<h2>Ewolucja</h2>

</div>

![AIS 移动应用](/img/en/blog/202101/mob_app.png) 移动应用 ![AIS 摄像头](/img/en/blog/202101/camera.png) 摄像头 ![AIS 媒体投射](/img/en/blog/202101/mobile-request.png) 媒体重定向 ![AIS Zigbee2Mqtt](/img/en/blog/202101/zigbee.png) Zigbee2Mqtt ![AIS 电视](/img/en/blog/202101/tv.png) 电视控制 ![AIS TTS](/img/en/blog/202101/tts_icon.png) 欢迎文本 ![AIS 家庭助理](/img/en/blog/202101/hass.png) 家庭助理 ![AIS 编辑](/img/en/blog/202101/bridge.png) MQTT桥接

<!--truncate-->

## 无忧升级指南

:::tip[数据备份]
### ![A](/img/en/blog/202009/alpha-a-circle.png) 数据备份

注意：升级前建议先执行[配置备份](/docs/ais_bramka_configuration_software#kopia-zapasowa-konfiguracji)。通过此操作可在升级前验证配置的正确性，显著提高升级成功率。
:::

:::important[网关控制台与日志]
### ![B](/img/en/blog/202009/alpha-b-circle.png)网关控制台与日志

若升级遇到问题，请查阅[通过控制台升级](/docs/ais_bramka_update_manual)或[执行应用完全重置](/docs/ais_bramka_reset_ais_step_by_step)流程。此情况尤其适用于在网关上安装了非标准组件的用户。
:::

:::caution[耐心等待]
### ![C](/img/en/blog/202009/alpha-c-circle.png) 耐心等待。升级后首次启动耗时较长——请保持耐心

**升级完成后首次启动可能耗时长达20分钟**
此时系统正在更新网关集成库并将数据库迁移至新格式
**请耐心等待升级完成**
:::

## ![](/img/en/blog/202101/celina.png) 进化之路

:::caution[动画显示]
动画仅会在屏幕宽度≥600px的设备显示，手机端可能无法呈现。
:::

家庭助理与AI-Speaker正持续进化，从软件形态逐步发展为通过网关实现的智能音箱。我们已进入最后冲刺阶段：

<div className="shapeshifter play"></div>

实现最终愿景仅差最后一步——将网关转变为智能音箱：

<div className="shapeshifter2 play"></div>

现在的问题已不再是AI-Speaker是否会推出智能音箱，而是实际上;)AI-Speaker何时会推出智能音箱。
距离将这些元素整合为一个完整产品只差临门一脚，我们将在几周后（99%的概率在2021年2月内）展示开发套件(KIT)，用于将网关改造成智能音箱。

正如我们此前承诺的，我们将发布详细指南，让每个人都能自行采购所需组件（不一定从我们这里购买——因为我们甚至不会有太多库存）来改造网关为智能音箱。
论坛上可查阅相关细节 [DEV KIT智能音箱项目](https://ai-speaker.discourse.group/t/dev-kit-glosnik-ankieta/1108)

![](/img/en/blog/202101/dev-kit.jpeg)

## ![](/img/en/blog/202012/mob_app.png) 移动应用2.0.2.CamCast版

最新版AIS dom应用带来了更多简化和新功能。

由于该应用需适配多种设备（从智能手表、手机、平板到电视），为便于用户根据使用场景选择功能，我们新增了按需启用特定功能的选项。
虽然可以根据设备类型自动配置，但我们不愿限制用户选择或强加"唯一正确方案"。这使得旧手机也能作为控制面板使用（而不仅限于平板电脑）等场景成为可能。

![移动端](/img/en/frontend/mob_special_functions.png)

应用所有功能详情可查阅最新文档：

- [AIS dom移动版](/docs/ais_app_android_dom_mob)
- [AIS dom面板版](/docs/ais_app_android_dom_tablet)

版本号命名为2.0.2.CamCast，因为此版本新增了将网关摄像头视频流重定向至AIS dom应用的功能。
要使AIS dom应用成为远程播放器，需通过集成向导添加 [添加播放器至网关](/docs/ais_app_player#dodanie-odtwarzacza-do-bramki)

![AIS广播](/img/en/frontend/ais_exo_player_add_new2.png)

现在除了文档所述音频重定向功能 [媒体重定向](/docs/ais_app_player#przekierowanie-mediów) 外，

![智能眼镜设置](/img/en/frontend/redirect_media_to_client_gate.png)

还能将摄像头带音频的视频流重定向至应用：

![移动端](/img/en/frontend/video_doorbell.png)

:::caution[注意：摄像头画面重定向功能目前尚未简化]
在[网关API文档](/docs/ais_bramka_api_index)中，我们在```command```资源部分添加了实现该功能的```showCamera```命令说明及语法格式。
该命令也可通过网关服务```redirect_camera_stream```调用。
此功能最终将通过应用程序界面直接调用（无需使用API）。
:::

## ![](/img/en/blog/202101/tv.png) 电视控制

当网关连接至电视或显示器时，现可通过浏览器或AIS dom应用程序远程控制网关上的活动界面/屏幕：

![Gate to tv](/img/en/frontend/gate_to_tv.jpeg)

通过该功能可播放流媒体服务或摄像头的视频内容。

我们在论坛新增了关于网关通过HDMI-CEC功能控制HDMI连接设备的说明：[HDMI-CEC控制HDMI连接设备](https://ai-speaker.discourse.group/t/hdmi-cec-sterowanie-urzadzeniami-podlaczonymi-po-hdmi/1254)

![Gate to tv](/img/en/blog/202101/cec.jpeg)

结合这些功能可实现视频门铃系统，未来我们将提供自动化模板实现方案。

## ![](/img/en/blog/202101/tts_icon.png) 欢迎词设置

在[网关配置-语音助手设置](/docs/ais_bramka_configuration_tts)中新增欢迎词自定义功能（留空可禁用）。

![网关软件](/img/en/bramka/config_ais_dom_section4.jpeg)

## ![](/img/en/blog/202101/zigbee.png) Zigbee2Mqtt

Zigbee2Mqtt已更新至1.7.0版本
包含多项修复及新设备支持，详见[1.17.0](https://github.com/Koenkk/zigbee2mqtt/releases/tag/1.17.0)

新增通过应用程序修改zigbee2mqtt配置及重启zigbee服务功能：

![网关软件](/img/en/blog/202101/zigbee_config.png)

该功能适用于故障排查及Zigbee工作频道调整：
详见文档[AIS Zigbee2MQTT](/docs/ais_app_integration_zigbee)
及论坛讨论：[Zigbee2mqtt cc2531停止工作](https://ai-speaker.discourse.group/t/zigbee2mqtt-cc2531-przestalo-dzialac/743/93)

## ![](/img/en/blog/202101/hass.png) 家庭助手

最新版家庭助手即我们的``ais-dom``套件，基于最新稳定版Home Assistant Core构建。

![家庭助理](/img/en/blog/202101/ha_social.png)

Home Assistant的详细变更说明可查阅项目博客：[2021.1: 新年快乐！](https://www.home-assistant.io/blog/2021/01/06/release-20211/)

## ![](/img/en/blog/202101/bridge.png) MQTT桥接

正如我们在论坛[构建桥梁](https://ai-speaker.discourse.group/t/kolejna-celina-beta-wydana/1277)中所预告的

![MQTT桥接](/img/en/blog/202101/mqtt_bridge.jpeg)

该功能将实现与SUPLA云服务的便捷集成。我们已与SUPLA团队达成协议并获得了集成开发权限。
下个版本我们将重点优化该功能，最终实现在应用中仅需点击几次即可完成集成。

若您希望提前测试SUPLA MQTT集成，我们已在MQTT配置中新增了通过应用界面修改MQTT代理配置的功能

![MQTT](/img/en/integrations/mqtt_edit_mosquito_config.png)

更多信息详见文档：[MQTT代理配置](/docs/ais_app_integration_mqtt#konfiguracja-brokera-mqtt)

-------

##### AI-Speaker 2021年1月