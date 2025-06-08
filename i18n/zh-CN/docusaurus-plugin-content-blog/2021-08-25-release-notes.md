---
author: Jola AI-Speaker
authorURL: https://github.com/sviete
author_title: Asystentka
authorImageURL: https://avatars3.githubusercontent.com/u/43966761?s=460&v=4
title: Wersja systemu Jarek
tags: ["ais pro1", "mqtt", "home assistant", "zigbee"]
---

<div class="IntroAisBlogMenu" >

![AIS](/img/en/blog/202108/jarek.png)

</div>

<!--truncate-->

## 无忧升级指南

:::tip[备份]
### ![A](/img/en/blog/202009/alpha-a-circle.png) 备份

注意：升级前强烈建议先进行[配置备份](/docs/ais_bramka_configuration_software#kopia-zapasowa-konfiguracji)。这能帮助您在升级前验证配置的正确性，显著提高升级成功率。
:::

:::important[网关控制台与日志]
### ![B](/img/en/blog/202009/alpha-b-circle.png) 网关控制台与日志

若升级遇到问题，请参考[控制台手动升级指南](/docs/ais_bramka_update_manual)或[应用完全重置步骤](/docs/ais_bramka_reset_ais_step_by_step)。特别提醒：安装非标准组件的用户需重点关注此部分。
:::

:::caution[耐心等待]
### ![C](/img/en/blog/202009/alpha-c-circle.png) 耐心等待。升级及升级后首次启动耗时较长——请保持耐心

**升级后首次启动可能耗时较长**
此时系统正在更新网关集成的依赖库
**请耐心等待升级完成
可通过命令``htop``或``pm2 logs``查看系统启动状态**
:::

## ![](/img/en/blog/202108/jarek.png) 亚雷克系统

### PRO版持续演进

亚雷克系统是AIS新架构的延续，也是PRO服务的功能扩展

![](/img/en/blog/202107/aispro1.png)

网络是现代智能家居系统稳定运行的基石，同时也可能是大多数故障的根源。网络配置涉及NAT、端口转发、DHCP、TCP/UDP协议、防火墙等复杂概念，配置不当会导致整个系统异常。为此我们推出面向高级智能家居部署的预制网络层解决方案。目前该方案仅面向企业客户，未来将逐步开放给普通用户，让每个人都能购买到即插即用、专为物联网优化的VPN智能家居网络方案。这些网络层解决方案是我们正在开发的AIS Easy项目的重要组成部分。

我们提供网络层集成服务，当前主要面向物联网系统集成商和智能家居方案供应商。详见文档[网络基础设施](/docs/ais_dom_pro_network)

![AIS UISP](/img/en/pro/uisp_map.png)

### 视频门禁系统

我们已在网关上部署了可运行的SIP服务器：

![AIS UISP](https://aws1.discourse-cdn.com/free1/uploads/ai_speaker/original/2X/1/17ee19773ea2a6eaed8deacbb77b233d8c19287b.png)

关于该项目的更多信息请访问论坛 [AIS SIP (VoIP) 服务器/代理网关](https://ai-speaker.discourse.group/t/ais-sip-voip-serwer-broker-na-bramce-ais/1982)

我们还在AIS-dom中内置了SIP客户端：

![AIS UISP](https://aws1.discourse-cdn.com/free1/uploads/ai_speaker/original/2X/c/c0fb05e10bc4dd334c7bb3fb22475f61d7a63700.jpeg)

关于该项目的更多信息请访问论坛 [AIS SIP 2 (IP电话) 客户端应用](https://ai-speaker.discourse.group/t/ais-sip-2-ip-phone-klient-w-aplikacji-ais/2052)

这是构建视频对讲系统的两个核心组件，也是我们正在开发的AIS Easy项目的一部分。

### 远程访问网关应用程序

我们已将Cloudflare Tunnel二进制文件更新至最新版本 [Cloudflare Tunnel](https://github.com/cloudflare/cloudflared/releases/tag/2021.8.2)

![](/img/en/blog/202107/tunel.png)

本次更新的重要意义在于Cloudflare修复了我们报告的问题。这项改进为我们开启了隧道技术的新应用场景，后续我们将详细说明。

### AIS Easy计划

这是我们正在推进的新项目，旨在降低智能家居系统的使用门槛，让用户无需聘请系统集成商即可轻松配置。
我们已构思出解决方案，并期待获得广大用户的青睐。

该项目将持续至年底，几天后我们将邀请您参与问卷调查，以更精准地定位需要解决的痛点。
悄悄透露：完成问卷将获得保底奖励 🎉

还将设置竞赛问题——获得Jolki最多❤️的最佳答案作者将赢得AIS提供的大奖！

![](/img/en/blog/202108/open_question.jpg)

作为内部消息，我们先透露几个问题方便您准备 ;)

![](/img/en/blog/202108/ankieta_1.png)

![](/img/en/blog/202108/ankieta_2.png)

![](/img/en/blog/202108/ankieta_3.png)

![](/img/en/blog/202108/ankieta_4.png)

### ![](/img/en/blog/202102/honeybee.png) Zigbee2Mqtt

Zigbee2Mqtt已更新至1.21.0版本，支持设备突破**1600**款。

所有细节详见 [1.21.0](https://github.com/Koenkk/zigbee2mqtt/releases/tag/1.21.0)

### ![](/img/en/blog/202101/hass.png) 家庭助理 2021.8

最新版家庭助理，即我们基于最新稳定版Home Assistant Core构建的``ais-dom``软件包。

![](/img/en/blog/202108/ha.png)

所有变更与新特性说明 [2021.8](https://www.home-assistant.io/blog/2021/08/04/release-20218/)

能量满格！ :)

![](/img/en/blog/202108/power.png)

--------

##### AI-Speaker 2021年8月版