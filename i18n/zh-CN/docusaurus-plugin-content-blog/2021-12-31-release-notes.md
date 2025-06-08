---
author: Jola AI-Speaker
authorURL: https://github.com/sviete
author_title: Asystentka
authorImageURL: https://avatars3.githubusercontent.com/u/43966761?s=460&v=4
title: Wersja systemu Leon
tags: ["mqtt", "home assistant", "zigbee"]
---

<div class="IntroAisBlogMenu" >

![AIS](/img/en/blog/202112/lion.png)

</div>

<!--truncate-->

## 无忧升级指南

:::tip[备份 ![A](/img/en/blog/202112/cloud-upload.png)]

升级前建议先进行[配置备份](/docs/ais_bramka_configuration_software#kopia-zapasowa-konfiguracji)。
通过预先验证配置完整性，可显著提升升级成功率。

:::

:::important[控制台 ![B](/img/en/blog/202112/console.png)]

若应用内升级遇到问题，请通过[控制台手动升级](/docs/ais_bramka_update_manual)。实时日志监控功能可帮助诊断问题根源。
:::

:::caution[耐心等待 ![C](/img/en/blog/202112/timer-sand.png)]

升级过程及首次启动可能耗时较长 - 请保持耐心。
随时可通过``htop``或``pm2 logs``命令查看系统实时状态。
:::

## 需要帮助？

:::warning[重置 ![D](/img/en/blog/202112/broom.png)]
若问题无法自行诊断，请放心，我们已准备好支援方案。
专为恢复出厂设置设计的简易流程详见：[完整重置操作指南](/docs/ais_bramka_reset_ais_step_by_step)。
:::

:::important[返厂编程 ![D](/img/en/blog/202112/lifebuoy.png)]
若无法完成重置操作，可将设备寄回我们进行系统重装。
论坛专帖说明：[返厂编程服务](https://ai-speaker.discourse.group/t/usluga-programowania-urzadzen-w-ai-speaker/1368)
:::

## ![](/img/en/blog/202112/mini_lion.png) 雄狮版

本次版本升级简化了安装流程，调整了发布周期（减少对Home Assistant等组件的依赖），并重构了系统代码分发渠道。同时正式在Apple App Store和Google Play发布新版移动应用。

这些改进既响应了用户需求，也标志着我们的PRO方案已满足商业客户的技术要求。

### AIS版本发布机制变更

#### 新版发布日历

正如早前在论坛公告说明，我们新增ALFA发布渠道并调整各渠道更新频率：

[![](/img/en/blog/202112/wydania_zapowiedz.png)](https://ai-speaker.discourse.group/t/wydania-ais-zapowiedz-zmiany/2163)

各发布通道的新版本周期：

- ALFA通道 -
实时发布，每当我们编写新代码或集成Home Assistant、Zigbee2Mqtt等功能时立即推送

- BETA通道 -
保持原有PROD通道的发布节奏，每月第一个周三发布一次月度更新

- PROD通道 -
初始每3个月发布一次稳定版，最终调整为每6个月发布一次，发布时间为季度末月的最后一个周五

#### 更简化的安装方式

我们不再需要在网关上编译依赖项。通过直接部署预编译的软件包，新版本安装过程更加便捷。当然，高级用户仍可选择在网关上从源码编译各类程序（C/C++、Go、Rust、TS/NodeJs等语言编写的应用）。

通过应用程序更新系统：

![AIS](/img/en/blog/202112/instalacja_z_aplikacji.png)

通过控制台更新系统：

![Aktualizacja](/img/en/bramka/update_from_console.png)

#### 新增协作角色 - "软件发布经理"与"Zigbee2Mqtt包构建者"

我们很高兴地宣布社区成员已加入版本发布工作：

- **"软件发布经理"** 由用户Stravi担任，负责协助版本构建和推送至各更新通道

- **"zigbee2mqtt包构建者"** 由用户Adam负责Zigbee2Mqtt组件的打包工作

#### 衷心感谢各位的贡献与支持 :)

这仅是开始，未来我们将逐步将整个**"版本构建与发布流程"**移交社区管理。这样既能减轻我们的工作负担，也能让用户对ais dom网关上的软件拥有更大控制权。

### AIS PRO1 - 首个大型商业项目实践

过去数月，AIS PRO1一直为某商业项目开发——套集成了有线自动化系统的智能家居配电箱解决方案。

虽然这个项目有许多值得称道的亮点，但正如我父母常说的**"与人为善固然重要，但诚实更为可贵"**。当实施前夕发现预期销售规模无法达成且缺乏运维预算时，整个项目不得不遗憾终止 :(

![End of The Pro](/img/en/blog/202112/end_of_the_pro.jpg )

当然，放弃这个项目对我们来说并不容易。我们曾以150%的投入参与其中。还需要一些时间来重新梳理、走出低谷，并以更强大的姿态回归更好的项目。

![End of The Pro](/img/en/blog/202112/obawy.jpg)

目前我们深刻认识到：商业模式不会自动成型。当客户自行找到我们却对需求不明确时，必须快速建立"强力防火墙"，否则就是浪费时间。但积极的一面是——这些人生课程无比珍贵，下次我们一定会做得更好！

### AIS - 附加应用程序

我们更新了平板端应用，同时发布了移动设备和智能手表的新版本应用。在首次启动AIS家庭网关时，系统会提示用户下载平板控制面板及移动设备的附加应用程序。

![AIS](/img/en/blog/202112/aplikacje_ais.jpeg)

### 文件管理器

网关内置了Web版文件管理器应用，支持文本编辑和文件预览（文本/音频/视频）。该应用允许通过任意电脑、手机或平板浏览器进行文件和目录操作。

![WEB cmd](/img/en/bramka/web_cmd.png)

更多集成信息详见文档 [文件管理器](/docs/ais_app_integration_manager)

### AIS安卓集成

我们深化了与网关安卓系统的集成，新增两项内置功能：

#### 1. AIS ADB

这是AIS家庭网关新增的内置集成功能。

![AIS](/img/en/blog/202112/AIS_Android.png)

集成详情见文档 [AIS安卓](/docs/ais_app_android)

#### 集成开发背景

我们的网关运行安卓系统。AIS DEV与树莓派的核心区别在于：AIS家庭网关不仅是无界面服务器(headless server)，更是完整的多媒体消费设备(media consumption device)。

论坛上出现的KODI、Amazon Prime、Plex集成方案启发了我们开发官方安卓多媒体控制功能，通过安卓支持的ADB接口实现控制。

得益于安卓系统，AIS家庭网关在多媒体处理方面表现卓越，相比树莓派能为终端用户提供更丰富的功能体验。

![AIS](/img/en/blog/202112/RIP.jpeg)

在AIS Android集成的首个版本中，我们重点实现了对网关预装的Spotify播放器的控制功能。通过这种方式将Spotify音乐库浏览与播放器控制功能解耦。更多技术细节请参阅文档：[Spotify音乐库](/docs/ais_app_spotify)

#### 2. AIS Android远程屏幕

这是AIS家庭网关新内置的应用程序，可通过浏览器（或移动端WebView）实时查看Android系统及应用界面。

[![](/img/en/blog/202112/android.png)](https://github.com/sviete/AIS-ScreenStream)

核心设计理念是将原生Android应用（如Spotify）的界面投射到AI-Speaker网页应用中展示。

[![](/img/en/blog/202112/android2.png)](https://github.com/sviete/AIS-ScreenStream)

### AIS Easy问卷调查总结

![](/img/en/blog/202108/open_question.jpg)

部分用户提交了极具创意的解决方案，我们对此深表感谢——这些精彩内容令人拍案叫绝！未来很可能会将部分方案付诸实践。至于那些提出"脑控智能家居"设想的朋友...恐怕还需耐心等待更长时间 ;)
本次开放式问答的大奖——AIS PRO1网关将授予某位提出多项创新构想的用户。获奖者承诺将在论坛展示奖品，并分享合法有趣的改造方案（我们已过滤掉少量不合规内容）。具体实施教程将逐步发布，敬请期待！

由于PRO1项目的影响，我们总部建设和AIS EASY套件进度有所延迟...不过AIS EASY本就是两年期的长期计划。现在我们采用预应力混凝土3D打印墙体技术，相信两年后能如期完工共饮庆功咖啡 :)

[![](/img/en/blog/202112/ais_easy.jpeg)](https://tasmota.github.io/docs/)

如有商务合作需求，也欢迎随时莅临：

[![](/img/en/blog/202112/ais1.jpg)](https://tasmota.github.io/docs/)

[![](/img/en/blog/202112/ais2.jpg)](https://tasmota.github.io/docs/)

### ![](/img/en/blog/202112/robot.png) Tasmota 10.0.0 Norman版本

面向ESP芯片设备的又一版固件发布。您可在项目文档中查阅所有变更与新特性：

[![](/img/en/blog/202112/tasmota.png)](https://tasmota.github.io/docs/)

我们最青睐的新功能是Tasmota Mesh（TasMesh），它通过ESP-NOW实现节点/代理间的通信。这意味着未来ESP设备的配对或将如Zigbee般简便。

我们在此描述了这一愿景：
https://github.com/arendst/Tasmota/discussions/14193

[![](/img/en/blog/202112/tasmo.png)](https://github.com/arendst/Tasmota/discussions/14193)

### ![](/img/en/blog/202102/honeybee.png) Zigbee2Mqtt

点击查看Zigbee2Mqtt项目全新首页：
[![](/img/en/blog/202112/z2m.png)](https://www.zigbee2mqtt.io/)

Zigbee2Mqtt已更新至最新版1.22.1（我们共提供3个版本的代码）：

- [1.21.2](https://github.com/Koenkk/zigbee2mqtt/releases/tag/1.21.2)
- [1.22.0](https://github.com/Koenkk/zigbee2mqtt/releases/tag/1.22.0)
- [1.22.1](https://github.com/Koenkk/zigbee2mqtt/releases/tag/1.22.0)

### ![](/img/en/blog/202101/hass.png) 家庭助理

家庭助理最新版本，即我们基于Home Assistant Core的「ais-dom」软件包。
本次我们带来了三个Home Assistant版本！**包含大量改进与新功能，敬请体验**：

[![](https://www.home-assistant.io/images/blog/2021-10/social.png)](https://www.home-assistant.io/integrations/#version/2021.10)

[![](https://www.home-assistant.io/images/blog/2021-11/social.png)](https://www.home-assistant.io/integrations/#version/2021.11)

[![](https://www.home-assistant.io/images/blog/2021-12/social.png)](https://www.home-assistant.io/blog/2021/12/11/release-202112/)

--------

##### AI-Speaker 2021年12月版