---
author: Jola AI-Speaker
authorURL: https://github.com/sviete
author_title: Asystentka
authorImageURL: https://avatars3.githubusercontent.com/u/43966761?s=460&v=4
title: Wersja systemu 0.115.9
tags: ["media", "galeria", "zigbee2mqtt", "home assistant", "tasmota"]
---

# 0.115.9 媒体功能

- ![AIS Media](/img/en/blog/202010/folders.png) **多媒体库**
- ![AIS Galeria](/img/en/blog/202010/gallery.png) 图库
- ![Zgłoszenia audio](/img/en/blog/202010/ai.png) 音频源搜索
- ![Zigbee](/img/en/blog/202007/zigbee.png) Zigbee2Mqtt 1.5.0
- ![Tasmota](/img/en/blog/202005/tasmota_small.png) Tasmota 8.5.1 Hannah
- ![Home Assistant](/img/en/blog/202010/ha.png) Home Assistant 0.115.6 生日特别版！

<!--truncate-->

## 无忧升级指南

:::tip[备份]
### ![A](/img/en/blog/202009/alpha-a-circle.png) 备份

注意 升级前建议先进行[配置备份](/docs/ais_bramka_configuration_software#kopia-zapasowa-konfiguracji)。通过这种方式可以在升级前验证配置的正确性，提高顺利升级的概率。
:::

:::important[网关控制台与日志]
### ![B](/img/en/blog/202009/alpha-b-circle.png)网关控制台与日志

若升级遇到问题，请查阅[通过控制台升级](/docs/ais_bramka_update_manual)或[完全重置应用](/docs/ais_bramka_reset_ais_step_by_step)流程。
特别是那些在网关上安装了额外非标准组件的用户需特别注意。
:::

:::caution[耐心等待]
### ![C](/img/en/blog/202009/alpha-c-circle.png) 耐心。升级后的首次启动耗时较长——请耐心等待。

 **升级后首次启动可能长达20分钟。**
 在此期间会更新网关集成组件库，并将数据库迁移至新格式。
 **请耐心等待升级完成。**
:::

## 注意 - 天气卡片将消失

我们致力于提升网关启动速度。导致启动缓慢的原因可能是网络连接问题或互联网访问受限。
我们的设计目标是确保系统在断网状态下仍可运行。因此为避免等待在线服务响应，我们将停止预装那些依赖网络连接的默认集成组件。

具体表现为本次升级后天气功能消失——因为获取天气数据需要连接OpenWeatherMap和DarkSky服务。
如果用户仍使用默认应用界面，升级后将看到如下效果：
![](/img/en/blog/202010/pogoda.png)

修复方法：进入界面配置：
![](/img/en/blog/202010/pogoda2.png)

并删除“孤立实体”：

![](/img/en/blog/202010/pogoda3.png)

新的“出厂默认界面”现在将如下所示：
![](/img/en/blog/202010/pogoda4.png)

当然，我们鼓励您配置自己的界面——这正是该系统的核心理念 :)

现在通过增强的图库功能和直接从移动应用相机添加房间照片的能力（我们将在下方文档和YouTube新视频中说明），创建美观界面变得更加简单。

## ![AIS Media](/img/en/blog/202010/folders.png) 多媒体库

此版本新增了浏览多媒体库及将其投送（Cast）至选定播放器的功能。

![AIS Galeria](/img/en/blog/202010/media_browser.png)

> 家庭助手仅作为控制器发送媒体链接。实际媒体由目标播放器（接收链接的设备）直接解码播放。
若目标播放器未内置Spotify支持或无法解码视频格式，则投送内容将无法播放。
**当然，我们在库中浏览的媒体可通过网关内置播放器直接播放，也可投送至其他网关（最终实现多音箱播放）。**

此外还支持直接在浏览器中播放媒体。

![AIS Galeria](/img/en/blog/202010/play_in_browser.png)

## ![AIS Galeria](/img/en/blog/202010/gallery.png) 图库

![AIS Galeria](/img/en/blog/202010/img1.png)

具体操作演示请见下方视频：

<iframe width="560" height="315"  src="https://www.youtube.com/embed/iIJcAOnQ6HI" frameBorder="0" allowFullScreen></iframe>

## ![Zgłoszenia audio](/img/en/blog/202010/ai.png) 优化音频源搜索

若某电台播放存在问题，可自动检测是否有更新源可用：
![AIS Galeria](/img/en/blog/202010/audio_report_1.png)

若自动检测未能解决，可将问题反馈至AI-Speaker平台。

![AIS Galeria](/img/en/blog/202010/audio_report_2.png)

收到反馈后我们将尽快修复问题。
若您已在集成商平台注册，问题解决后我们将通过您预留的邮箱/账号发送通知。

## ![Zigbee](/img/en/blog/202007/zigbee.png) Zigbee2Mqtt 1.5.0

Zigbee更新不再只是新增设备支持（目前已支持1015种设备） :)
![AIS Galeria](/img/en/blog/202010/zigbee1.png)

还包含全新应用，与家庭助手深度集成：
![AIS Galeria](/img/en/blog/202010/zigbee2.png)

![AIS Galeria](/img/en/blog/202010/zigbee3.png)

![AIS Galeria](/img/en/blog/202010/zigbee4.png)

这些是最新开发的功能，部分细节仍在完善中，但其潜力巨大，预计经过几次迭代后将更加成熟 ;)
**我们暂时保留旧版Zigbee配置界面，但下个版本将全面切换至新界面。**
若遇到操作问题或功能建议，可在[Zigbee2Mqtt项目页](https://github.com/koenkk/zigbee2mqtt)提交反馈。版本1.5.0的更新日志详见[Zigbee2Mqtt发布页](https://github.com/Koenkk/zigbee2mqtt/releases/tag/1.15.0)

## ![](/img/en/blog/202005/tasmota_small.png) Tasmota 8.5.1 Hannah

我们同步发布了Tasmota最新编译版本8.5.1

![Tasmota](/img/en/blog/202010/tasmota1.png)

该固件用于我们销售的设备中。**高级用户可免费使用**并刷入自有设备。支持超过[1600种设备模板](https://templates.blakadder.com/index.html)：

![Tasmota](/img/en/blog/202010/tasmota2.png)

论坛中我们以[灌溉电磁阀](https://ai-speaker.discourse.group/t/ponad-1540-urzadzen-wifi-co-to-znaczy/707)为例详细说明了刷机方法

版本8.5.1的更新日志详见[Tasmota项目发布页](https://github.com/arendst/Tasmota/releases/tag/v8.5.1)

## ![](/img/en/blog/202007/hass.png) Home Assistant 0.115.6

最新稳定版[Home Assistant 0.115.6](https://www.home-assistant.io/blog/2020/09/17/release-115/)

这是我们核心系统的周年纪念版本 :)

贺卡祝福已发送 ![](/img/en/blog/202010/love-letter.png) 并妥投：

![Home Assistant](/img/en/blog/202010/kartka.png)

----

欢迎升级并[参与论坛讨论 :)](https://ai-speaker.discourse.group/)

##### AI-Speaker 2020年9月