---
author: Jola AI-Speaker
authorURL: https://github.com/sviete
author_title: Asystentka
authorImageURL: https://avatars3.githubusercontent.com/u/43966761?s=460&v=4
title: Wersja systemu Kasia
tags: ["mqtt", "home assistant", "zigbee"]
---

<div class="IntroAisBlogMenu" >

![AIS](/img/en/blog/202109/kasia.png)

</div>

<!--truncate-->

## 无忧升级指南

:::tip[备份]
### ![A](/img/en/blog/202009/alpha-a-circle.png) 备份

注意：升级前建议先进行[配置备份](/docs/ais_bramka_configuration_software#kopia-zapasowa-konfiguracji)。这能帮助您在升级前验证配置的正确性，并显著提高顺利升级的概率。
:::

:::important[网关控制台与日志]
### ![B](/img/en/blog/202009/alpha-b-circle.png) 网关控制台与日志

若升级遇到问题，请参考[控制台手动升级指南](/docs/ais_bramka_update_manual)或[应用完全重置步骤](/docs/ais_bramka_reset_ais_step_by_step)。
特别提醒安装非标准组件的用户需重点关注此部分。
:::

:::caution[耐心等待]
### ![C](/img/en/blog/202009/alpha-c-circle.png) 耐心等待。升级及升级后首次启动耗时较长——请保持耐心。

 **升级后的首次启动可能耗时较久。**
 此时系统正在更新网关已安装集成所需的依赖库。
 **请耐心等待升级完成。
 您可通过命令``htop``或``pm2 logs``在控制台查看系统启动状态（了解当前运行进程）**
:::

## ![](/img/en/blog/202109/kasia.png) 卡西亚

本次版本中，我们的核心移动应用AIS dom从通用型转向专用型发展，将逐步演变为平板专属应用。近期新增的SIP协议和RTSP流媒体支持功能导致应用体积显著增长——目前已超过100MB。诸多功能专为平板设计（如可视门禁、手势操作、音频重定向及音频控制）。

自此版本起，我们的移动应用将成为Home Assistant移动应用的分支版本。
AIS移动应用与HA移动应用的主要差异体现在：

- 默认波兰语界面
- 配色方案
- 品牌标识
- 免费隧道服务
- 更高每日通知限额→999条

其余功能均与HA保持100%一致。

我们实现的突破：

- 推出Apple专属应用
- 发布Android专用移动应用
- 推出控制面板（平板）专用应用
- HA志愿者开发者编写的移动应用代码将自动同步至AIS

这使得AI-Speaker成为能为所有用户提供智能家居应用解决方案的集成平台。

### Android系统

####  AIS dom平板应用 - 视频门禁

AIS dom作为我们的核心移动应用，其定位正从通用型转向更专业的平板专用应用。近期新增的SIP协议和RTSP协议支持功能显著增加了应用体积——目前已超过100MB。许多功能专为平板设计（如视频门禁系统、手势操作、音频重定向及音频控制）。

![智能玻璃设置](/img/en/frontend/video_doorbell.png)

"触控面板/Smart panel"功能详见文档：[AIS dom平板应用](/docs/ais_app_android_dom_tablet)

####  AIS dom移动版

这是我们专为Android移动设备开发的新应用，现已在Google Play上架：

![](/img/en/blog/202109/mob.png)

"AIS dom移动版"功能将记录在文档中：[AIS dom移动版](/docs/ais_app_android_dom_mob)

### AIS dom iOS/macOS版

我们正在向App Store提交应用。iOS/macOS应用不仅涉及代码开发，还需向苹果提交包含"关键通知权限"、"本地通知权限"等合规说明，并详细解释为何需要"com.apple.security.device.camera"和"com.apple.security.files.downloads.read-write"等权限。目前应用尚未通过苹果审核，预计仍需时日...所以苹果图标暂时还是绿色的;)

![](/img/en/blog/202109/ios.png)

![](/img/en/blog/202109/macOS.png)

"AIS dom iOS/macOS版"功能将记录在文档中：[AIS dom iOS版](/docs/ais_app_ios_mob)

### Linux系统 - 二进制包

本次更新包含数十个关键二进制包的最新版本，涵盖系统运行核心组件：python、nodejs、rclone、mosquitto、ttyd、libwebsockets、llvm、ffmpeg等...

:::warning
请耐心等待系统更新完成及家庭助理启动。该过程耗时取决于网关性能及已安装的集成组件——Python包依赖项将在安装时实时编译，在PRO1设备上5分钟的编译过程，在DEV1设备上可能长达60分钟。
:::

![](/img/en/blog/202109/termuxhero.jpg)

由于libffi主版本更新导致ABI（二进制低级接口）变更，我们重建了1000余个依赖包。这是自2012年以来该库最重大的变更。所有依赖libffi的软件包均需重新编译：

- ctypes-sh
- ecl
- glib
- imagemagick
- libgmime
- libllvm
- p11-kit
- profanity
- python
- python2
- ruby
-  ... 以及依赖这些软件包的其他组件…

我们同时将Cloudflare隧道二进制文件更新至最新版本 [Cloudflare隧道](https://github.com/cloudflare/cloudflared/releases/tag/2021.9.0)

据Cloudflare称，新隧道采用智能路由算法，其速度甚至比直连快40%。

![Cloudflare隧道](https://aws1.discourse-cdn.com/free1/uploads/ai_speaker/optimized/2X/f/fb115cb8ae2bb2924d8638f67e2b82acef117c50_2_463x500.jpeg)

完成Cloudflare改进后，我们启用了新的隧道定义格式。现在配置文件采用网关上的yaml格式（禁止用户修改），可通过应用程序查看。

![](https://aws1.discourse-cdn.com/free1/uploads/ai_speaker/original/2X/5/5934b0c4f6552c9603fc8beeab2619c182a72c53.png)

### AIS Easy - 问卷调查

感谢参与问卷调查——您提供的宝贵意见将帮助我们优化产品方案。我们决定延续该活动，在奖品发放完毕前持续开放问卷（最迟至年底）。

![](/img/en/blog/202108/open_question.jpg)

### ![](/img/en/blog/202102/honeybee.png) Zigbee2Mqtt

Zigbee2Mqtt更新至1.21.1版本——支持**1667**种设备。完整更新日志见[1.21.1](https://github.com/Koenkk/zigbee2mqtt/releases/tag/1.21.1)

Zigbee技术持续演进，近期市场将出现两款高性价比Zigbee 3.0设备，可能重塑协调器市场格局：

#### 1. Sonoff适配器

![](/img/en/blog/202109/sonoff.jpg)

#### 2. 以太网网关

![](/img/en/blog/202109/ZB-GW03-ESP32-Ethernet-Zigbee-Gateway.jpg)

若这些设备通过CE认证且运行稳定，我们将予以支持以丰富Zigbee协调器选择。它们的出现标志着Zigbee市场新阶段——此前用户需选择认证版Conbee 2或非认证DIY焊接方案，现在第三方认证产品将冲击手工焊接解决方案的市场空间。

### ![](/img/en/blog/202101/hass.png) 家庭助理2021.9

最新版家庭助手，即我们的`ais-dom`软件包，基于最新稳定版Home Assistant Core构建。

![](/img/en/blog/202109/ha.png)

完整更新内容与特性说明详见[2021.9版本](https://www.home-assistant.io/blog/2021/09/01/release-20219/)

此版本无重大变更，HA团队正专注于Amber项目，我们在博客中对此有专门介绍：

[![](/img/en/blog/202109/amber.png)](https://ai-speaker.discourse.group/t/amber-by-home-assistant/2122)

--------

##### AI-Speaker 2021年9月版