---
author: Jola AI-Speaker
authorURL: https://github.com/sviete
author_title: Asystentka
authorImageURL: https://avatars3.githubusercontent.com/u/43966761?s=460&v=4
title: Wersja systemu Iga
tags: ["ais pro1", "mqtt", "home assistant", "zigbee", "tasmota"]
---

<div class="IntroAisBlogMenu" >

![AIS](/img/en/blog/202107/iga.png)

</div>

<!--truncate-->

## 无忧升级指南

:::tip[备份]
### ![A](/img/en/blog/202009/alpha-a-circle.png) 备份

注意：升级前建议先进行[配置备份](/docs/ais_bramka_configuration_software#kopia-zapasowa-konfiguracji)。通过这种方式，您可以在升级前验证配置的正确性，并提高顺利升级的概率。
:::

:::important[网关控制台与日志]
### ![B](/img/en/blog/202009/alpha-b-circle.png) 网关控制台与日志

若升级遇到问题，请参考[通过控制台升级](/docs/ais_bramka_update_manual)或[执行应用完全重置](/docs/ais_bramka_reset_ais_step_by_step)流程。
特别是对于在网关上安装了额外非标准组件的用户更需注意。
:::

:::caution[耐心等待]
### ![C](/img/en/blog/202009/alpha-c-circle.png) 耐心等待。升级及升级后的首次启动耗时较长——请保持耐心。

**升级后的首次启动可能持续时间较长。**
此时系统正在更新网关已添加集成所需的库文件。
**请耐心等待升级完成。
您可以通过控制台命令``htop``和/或``pm2 logs``查看启动状态（了解系统当前运行情况）**
:::

## ![](/img/en/blog/202107/iga.png) 伊加

### AIS PRO1网关

AIS PRO1网关不仅搭载了市面上最强的ARM处理器和顶级硬件解决方案，更代表着我们全新的商业模式和面向企业客户的首款AIS产品。
我们能够基于该硬件实现从内核编译到系统各层（含服务、应用程序）直至浏览器运行应用的完整开发。

![](/img/en/blog/202107/aispro1.png)

就市面现有ARM架构设备而言，唯有最新款ODROID N2+能与AIS PRO1比肩。为直观展示性能差异，下图呈现了与树莓派3及搭载四核Arm Cortex A53（1.2GHz）处理器的Fibaro HC3旗舰网关的对比。

![](/img/en/blog/202107/AIS-PRO1-Benchmark.png)

AIS PRO1也可作为现有用户的硬件升级方案，实现数倍系统性能提升。我们深知许多用户期待已久，因此特别为现有AIS网关用户提供不含附加服务、合约及SLA保障（仅面向企业客户的付费增值项）的纯硬件购买选项。

当然，您也可以选择等待并购买商业化的完整解决方案，该方案包含质保、安装服务以及所有基于AIS PRO1构建系统所提供的配套服务。您也可以继续使用DEV1/2/3网关，自行集成和打造智能家居系统。我们后续还将推出AIS Easy选项（下文详述）。

我们希望每个人都能根据自身需求和预算找到最适合的解决方案。

### AI-Speaker.org

这是我们托管在Fosshost服务器上的新域名https://ai-speaker.org/，用于迁移原DEV网关的免费服务。

我们很荣幸邀请到用户兼好友Adam来管理该域名。Adam曾为我们解决过其他项目的网络问题，现在他主动承担起Fosshost服务器的管理工作，并已成功部署了我们此前未能实现的功能。**这台Fosshost服务器将由一位拥有多年经验的资深Linux系统管理员负责运维。感谢Adam！**

![](/img/en/blog/202107/ais-org.png)

### Cloudflare隧道

我们改进了网关的远程隧道功能，从本版本开始采用Cloudflare解决方案。Cloudflare不仅能实现网关的互联网访问，还能防范来自互联网的直接攻击。通过这种方式，我们在启用远程访问时保护了运行于AIS网关上的**Home Assistant/AIS dom服务器**。

![](/img/en/blog/202107/tunel.png)

下一版本中我们计划增加额外的安全机制。

:::info
所有Beta版网关均已启用新隧道，根据我们的观察其稳定性更高——在传输大量数据时远程访问不会出现"卡顿"。若更新后隧道功能异常，请按以下步骤操作：

1. 在应用中关闭远程访问功能，等待Jolka语音确认已关闭
2. 重新启用远程访问功能，等待Jolka语音确认已开启
3. 等待Cloudflare的DNS解析完成传播（约需数分钟）
:::

### Python 3.9.6

二进制文件更新：Python升级至最新版本，同步更新24个其他软件包。其中包含定制版command-not-found包——终端中不再提示使用pkg命令，而是推荐apt命令。

![](/img/en/blog/202107/python.png)

Python在此至关重要，因为家庭自动化平台Home Assistant正是用该语言编写的。

### AIS淡入功能

我们改进了按下麦克风按钮及Jolka语音播报时的音频淡入淡出机制。当按下遥控器麦克风键或触发语音消息时，多媒体音量会降至10%；待Jolka播报结束后，媒体音量将逐步恢复至原水平→实现"淡入"效果。

![](https://aws1.discourse-cdn.com/free1/uploads/ai_speaker/optimized/2X/d/decf05916341b345e3be3a5beccb55faaffea4aa_2_690x483.jpeg)

### 可折叠卡片

新增了'''ais-expansion-panel'''卡片类型，支持界面元素的折叠/展开操作。

![](/img/en/blog/202107/aisep1.png)

当前该卡片用于设备分组管理，并在PRO网关中实现音频相关的高级选项控制。

![](/img/en/blog/202107/aisep2.png)

PRO网关支持音频路由功能——可将音频定向输出至指定接口（3.5mm接口、光纤、HDMI或全选）。

### 动态天气图标

视觉优化：新增动态天气图标：

![](/img/en/blog/202107/pogoda.gif)

### ![](/img/en/blog/202102/honeybee.png) Zigbee2Mqtt

升级Zigbee2Mqtt至最新版1.2.0，现支持超**1540**种设备。同时修复了Conbee2的兼容性问题。

完整更新日志详见[1.20.0](https://github.com/Koenkk/zigbee2mqtt/releases/tag/1.20.0)

### ![](/img/en/blog/202101/hass.png) 家庭助理2021.7

家庭助理组件``ais-dom``已同步至最新稳定版Home Assistant Core。

![](/img/en/blog/202107/ha.png)

完整更新说明参见[2021.7](https://www.home-assistant.io/blog/2021/07/07/release-20217/)

## 功能预告

### 视频对讲系统

即将在BETA频道发布重大更新——视频对讲功能。该功能涉及大量代码重构，开发工作已持续多时...系统各层级均将更新：

- 网关服务层
- 平板应用层
- 集成商配置面板

我们将详细说明运作原理及配置方法。平板端应用界面预览如下：

![](/img/en/blog/202107/vido1.jpg)

![](/img/en/blog/202107/vido2.jpg)

### AIS简易模式

这是我们正在实施的新项目，旨在让用户更轻松地使用，同时无需为智能家居系统额外支付集成商费用。我们已构思出解决方案，并希望这一创新能赢得广大用户的青睐。

该项目将持续推进至年底，未来3-4周内我们将邀请您参与问卷调查，以便更精准地识别需求痛点并提供针对性解决方案。

**参与问卷的用户还将获得惊喜奖励 :)**

--------

##### AI-Speaker 2021年7月版