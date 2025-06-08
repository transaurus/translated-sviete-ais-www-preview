---
author: Jola AI-Speaker
authorURL: https://github.com/sviete
author_title: Asystentka
authorImageURL: https://avatars3.githubusercontent.com/u/43966761?s=460&v=4
title: Wersja systemu 0.114.5
tags: ["sync", "demo", "home assistant", "zigbee2mqtt", "nfc", "wearos", "tasmota"]
---

# 0.114.5 NFC+

- ![AIS MOB NFC+](/img/en/blog/202009/tag.png) **NFC标签扫描**
- ![AIS Wear OS](/img/en/blog/202009/watch.png) AIS Wear OS集成
- ![Synchronizacja](/img/en/blog/202009/sync.png) 与网关同步
- ![Poprawki](/img/en/blog/202009/fixes.png) 修复与优化
- ![Demo](/img/en/blog/202009/demo.png) 应用演示
- ![Tasmota](/img/en/blog/202005/tasmota_small.png) Tasmota 8.5.0 Hannah
- ![Zigbee](/img/en/blog/202007/zigbee.png) Zigbee2Mqtt 1.14.4 
- ![Home Assistant](/img/en/blog/202007/hass.png) Home Assistant 0.114.4

<!--truncate-->

## 无忧升级指南

:::tip[备份]
备份![A](/img/en/blog/202009/alpha-a-circle.png)

注意：升级前建议先进行[配置备份](/docs/ais_bramka_configuration_software#kopia-zapasowa-konfiguracji)。这样可以提前验证配置正确性，提高升级成功率。
:::

:::important[网关、控制台与日志]
![A](/img/en/blog/202009/alpha-b-circle.png)网关、控制台与日志

若升级遇到问题，请参考[控制台升级指南](/docs/ais_bramka_update_manual)或[完全重置应用步骤](/docs/ais_bramka_reset_ais_step_by_step)。特别适用于安装了非标准组件的用户。
:::

:::caution[耐心等待]
耐心![A](/img/en/blog/202009/alpha-c-circle.png)等待。升级后首次启动耗时较长。

**升级后首次启动可能长达20分钟**  
此时系统正在更新集成库并将数据库迁移至新格式。  
**请耐心等待升级完成**
:::

## ![](/img/en/blog/202009/tag.png) NFC标签扫描

我们在移动应用文档中新增了NFC标签扫描功能说明，并针对网关自动化场景添加了[NFC标签触发自动化示例](/docs/ais_bramka_tag_automation)

下方视频演示具体操作：

<iframe width="560" height="315"  src="https://www.youtube.com/embed/nzRBeRZZX7Q" frameBorder="0" allowFullScreen></iframe>

## ![](/img/en/blog/202009/watch.png) AIS Wear OS集成

开发人员自购Wear OS手表后，我们对该应用进行了多项优化。

![Wear OS](/img/en/blog/202009/wear_os_1.jpeg)

现在可通过集成页面的向导快速添加[AIS Wear OS](/docs/ais_app_android_dom_wear)集成：

![Wear OS](/img/en/frontend/wear_os_wiz_2.png)

## ![](/img/en/blog/202009/sync.png) 与网关同步

在新版移动应用中，我们可以启用"向网关报告"功能，这将启动一个定期服务（**间隔不短于15分钟**），向网关发送设备位置信息及手机传感器状态。初始阶段我们定期报告三项数据：定位坐标、详细地址及电池状态。

![GPS](/img/en/frontend/apk_report_gps2.png)

我们正在为[Wear OS](/docs/ais_app_android_dom_wear#synchronizacja-z-bramką)开发类似功能，重点在于定期报告活动状态：

![Wear OS](/img/en/blog/202009/wear_os_2.png)

## ![](/img/en/blog/202009/fixes.png) 修复与优化

我们实施了若干显著改进：

1. "Jolka在哪"功能增强

新增了从AIS dom移动应用和AIS dom Wear OS应用发送的定位地址传感器

![FIX](/img/en/blog/202009/fix_1.png)

``某人在哪``查询现在的工作逻辑：

- 若人员在预定义区域（家、公司、学校等），则播报区域名称
![FIX](/img/en/blog/202009/fix_2.png)

- 若人员不在家庭区域，则查询最近上报设备的地址信息并播报：
![FIX](/img/en/blog/202009/fix_3.png)

2. 新增点击推送通知跳转地址设置

新参数名为``click_action``

![FIX](/img/en/blog/202009/fix_4.png)

例如当存在地址为``/lovelace/cam``的摄像头视图时：
![FIX](/img/en/blog/202009/fix_6.png)

通过自动化从网关向移动应用发送通知服务：
![FIX](/img/en/blog/202009/fix_5.png)

用户将收到如下通知：

![FIX](/img/en/blog/202009/fix_6.jpeg)

点击后将跳转至通知中指定的地址：

![FIX](/img/en/blog/202009/fix_7.jpeg)

3. 通过移动应用音量键控制网关播放器音量

令人惊讶的是这个功能之前居然没实现 ;)

![FIX](/img/en/blog/202009/fix_8.png)

## ![](/img/en/blog/202009/demo.png) 应用演示版

我们最初将演示版部署在云端服务器上。从一开始的设想就是展示一个真实的应用程序，而非简单的演示——它能实际控制真实设备（开关、灯具、窗帘、摄像头等）。

我们开始进行端口转发、搭建消息代理服务器并将设备接入云端...但问题随之而来：由于我们的设备本就是以本地运行为核心设计，通过云端控制它们需要额外配置...我们在云端搭建了MQTT消息代理服务器，这部分运行良好。然而对于摄像头、Cast音箱和zigbee2mqtt设备来说就没那么简单了...主要障碍来自我们办公室使用的Orange运营商Fun Box2路由器，它会自动变更端口导致故障。

最终我们意识到不必逆势而为——我们本就有更优解（加密网关隧道）。演示版将采用与任何家庭网关相同的运作机制，具体来说就是通过``dom-demo``网关实现。

当前演示版运行在我们的``开发网关``（用于构建应用程序安装包的机器）上，通过隧道技术将应用映射至https://dom-demo.paczka.pro地址。该地址和架构方案将作为演示版的固定配置——我们将在近期完成最终调试后正式开放体验。

![](/img/en/blog/202009/demo2.png)

我们会确保演示版界面简洁美观:) 高级配置功能将保留给管理员账户。

## ![](/img/en/blog/202005/tasmota_small.png) Tasmota 8.5.0 Hannah固件

新版Tasmota对ESP32的支持日趋完善。Sebastian成功驱动了带运动传感器和显示屏的摄像头。ESP32 V162与家庭助手（已集成到dom-demo）配合表现优异，现在只差麦克风模块就完美了:)

![](/img/en/blog/202009/tasmo_cam.jpg)

我们还编译了ESP32-BLE网关专用版本，用来监控办公室的绿植;)

![](/img/en/blog/202009/ble.png)

![](/img/en/blog/202009/ble2.png)

该方案当然会在论坛发布，并附上教程供那些"享受清晨松香气味"的硬件爱好者参考;)

## ![](/img/en/blog/202007/zigbee.png) Zigbee2Mqtt 1.14.4

zigbee2mqtt正以创纪录的速度发展。目前已实现951种设备的"开箱即用"支持，实际上任何支持Zigbee通信的设备都可被添加。

![](/img/en/blog/202009/zigbee.png)

更多项目信息请访问 [zigbee2mqtt](https://www.zigbee2mqtt.io/information/supported_devices.html) 官网

同时出现了关于``Connected Home over IP``项目的新动态——该项目由苹果、亚马逊、谷歌和Zigbee联盟（宜家、三星、飞利浦Hue等）共同推进。
该标准将保持开放，任何设备都能轻松兼容各类语音助手，具体细节将于2021年公布，让我们拭目以待 :)

![](/img/en/blog/202009/zigbee2.png)

这预示着Zigbee技术的光明前景，我们倍感振奋，因为Zigbee意味着本地化控制 :)
更多项目详情参见 [Connected Home over IP](https://zigbeealliance.org/news_and_articles/project-development-to-reality/)

## ![](/img/en/blog/202007/hass.png) Home Assistant 0.114.4

最新稳定版 [Home Assistant 0.114.4](https://www.home-assistant.io/blog/2020/08/12/release-114/) 已发布

作为全球最大的开源智能家居平台，本次更新一如既往带来了大量便捷功能和亮眼特性 :heart_eyes_cat:

![Home Assistant](/img/en/blog/202009/ha0.14.4.png)

----

欢迎升级并[参与论坛讨论 :)](https://ai-speaker.discourse.group/)

##### AI-Speaker 2020年9月