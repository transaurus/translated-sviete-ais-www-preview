---
author: Jola AI-Speaker
authorURL: https://github.com/sviete
author_title: Asystentka
authorImageURL: https://avatars3.githubusercontent.com/u/43966761?s=460&v=4
title: Wersja systemu 0.111.6
tags: ["spotify", "zigbee", "home assistant", "mqtt bridge", "exta life"]
---

# 0.111.6 Spotify音乐库、MQTT桥接、EXTA LIFE...

- ![Biblioteka Spotify](/img/en/blog/202007/spoify_icon.png) Spotify音乐库
- ![EXTA LIFE](/img/en/blog/202007/exta_life.png) EXTA LIFE集成
- ![Restore from backup](/img/en/blog/202007/system_restore.png) 更便捷的备份配置恢复
- ![MQTT bridge](/img/en/blog/202007/mqtt_bridge.png) 通过MQTT桥接实现系统扩展
- ![Home Assistant](/img/en/blog/202007/hass.png) 新版Home Assistant - 启动更快速
- ![Zigbee](/img/en/blog/202007/zigbee.png) Zigbee2Mqtt更新，现已支持[146个厂商的849种设备](https://www.zigbee2mqtt.io/information/supported_devices.html)

<!--truncate-->

:::tip[提示]
注意：更新前建议先进行[配置备份](/docs/ais_bramka_configuration_software#kopia-zapasowa-konfiguracji)。通过这种方式可以在更新前验证配置的正确性，提高顺利更新的概率。
:::

:::important[重要通知]
若更新后遇到问题，请参考[控制台更新指南](/docs/ais_bramka_update_manual)或[执行应用完全重置](/docs/ais_bramka_reset_ais_step_by_step)——特别是对于安装了额外自定义组件的用户。
:::

:::caution[重要更新须知!]
 **更新后的首次启动可能耗时长达20分钟。**

 ![wait](/img/en/blog/202007/wait.png) 在此期间将更新网关集成的库文件，并将数据库迁移至新格式。

 **请耐心等待更新完成。**
:::

## ![Biblioteka Spotify](/img/en/blog/202007/spoify_icon.png) Spotify音乐库

我们在内置的[Spotify集成](/docs/ais_app_spotify)中新增了Spotify音乐库功能。[Sebastian](https://github.com/sgrzys) 经过大量编码工作 🥵 才成功调用这个（有时并不完全一致的）[Spotify API](https://developer.spotify.com/documentation/web-api/) 并在应用中展示结果。现在通过快捷按钮即可浏览和播放：

- 平台推荐歌单
- 用户收藏歌单
- 喜爱艺人作品
- 喜爱专辑列表
- 收藏单曲列表

Sebastian还添加了分页功能，即使性能较弱的浏览器也能流畅加载Spotify返回的列表结果 🥳

:::caution[注意事项]
 我们需要获取更多Spotify权限，才能通过AI-Speaker浏览收藏的歌单、专辑、艺术家和曲目。
 **家庭助理不会对Spotify资料库进行任何修改操作（仅支持浏览和播放内容）。**
:::

如果您正在使用Spotify集成服务，本次更新后需要重新安装该集成，具体步骤如下：

1. 删除现有Spotify集成

![spotify auth](/img/en/blog/202007/spotify_auth_1.png)

2. 重新添加Spotify集成

![spotify auth](/img/en/blog/202007/spotify_auth_2.png)

3. 为AI-Speaker授予更多权限

![spotify auth](/img/en/blog/202007/spotify_auth_3.png)

## ![EXTA LIFE](/img/en/blog/202007/exta_life.png) EXTA LIFE集成

Exta Life与Home Assistant的集成由[dgtal1](https://github.com/dgtal1)开发，这位开发者非常友好地同意将该集成作为内置组件加入AIS网关。**感谢dgtal1** 🥰 **！**
这使得我们的用户可以直接通过应用程序轻松配置集成（无需额外安装自定义组件）。

该集成是数月编程开发的成果，欢迎访问[forumextalife.pl](https://www.forumextalife.pl/index.php/topic,311.0.html)了解项目详情

这再次证明了热情和开放精神的强大力量，任何企业的封闭解决方案都难以与之抗衡。
微软、谷歌等科技巨头已经深刻认识到这一点，希望其他公司也能早日领悟。

![EXTA LIFE](/img/en/frontend/extalife_1.png)

该集成仍在持续开发中，未来我们会将其作为子模块加入代码仓库，并贡献我们的改进建议。
我们还将完善文档，逐步说明配置流程。
至此，我们已经可以通过用户界面配置波兰市场主流设备：FIBARO、SUPLA、BleBox和Exta Life 🥳

![EXTA LIFE](/img/en/frontend/extalife_2.png)

## ![Restore from backup](/img/en/blog/202007/system_restore.png) 更便捷的备份配置恢复

此前在执行[应用程序完全重置](/docs/ais_bramka_reset_ais_step_by_step)或[设备恢复出厂设置](/docs/ais_bramka_reset_index)后，要恢复网关配置需要执行以下步骤：

- 启动网关并执行"初始配置":
  - 添加新账户
  - 选择地理位置
  - 添加设备和服务（或跳过此步骤）
- 进入"设置" -> "AIS家庭网关配置" -> "网关软件" -> "恢复设置"
- 重启网关并使用恢复的账户凭据登录

现在操作更简便了😊，因为我们在用户界面中添加了在执行"初始配置"前从备份恢复的功能。

![AIS恢复](/img/en/blog/202007/ais_restore.png)

即在系统配置开始阶段，创建首个用户的步骤中，我们新增了登录"AI-Speaker集成商门户"并从上传至该门户的备份文件恢复配置的功能。

相关文档详见[首次启动 - 所有者账户](/docs/ais_bramka_first_run_step_account)

## ![MQTT桥接](/img/en/blog/202007/mqtt_bridge.png) 通过MQTT桥接实现系统扩展

我们计划在应用中实现定义家庭助理实例间MQTT桥接的功能：

![MQTT桥接](/img/en/blog/202007/mosquitto_mqtt_bridg2.png)

论坛上我们逐步演示了如何通过MQTT桥接连接两个网关 -> [论坛说明](https://ai-speaker.discourse.group/t/skalowanie-systemu-do-sterowania-automatyka-domowa-most-mqtt-pomiedzy-bramkami/537)

![MQTT桥接](/img/en/blog/202007/mosquitto_mqtt_bridg.png)

以及大规模物联网实践 - 如何通过EMQX代理和MQTT网关桥接连接1000万台设备 -> [论坛说明](https://ai-speaker.discourse.group/t/10-milionow-urzadzen-skalowanie-systemu-do-sterowania-automatyka-domowa/538)

![MQTT桥接](/img/en/blog/202007/emqx_mqtt_bridge.jpeg)

## ![Zigbee](/img/en/blog/202004/honeybee.png) Zigbee2Mqtt升级至1.14.1版本

### [支持146家厂商的849款设备](https://www.zigbee2mqtt.io/information/supported_devices.html)

Zigbee更新与其他组件更新一样将自动完成。

![CC2531](/img/en/iot/CC2531_Zigbee2MQTT_USB.jpg)

## ![Home Assistant](/img/en/blog/202007/hass.png) 新版Home Assistant - 启动速度更快

最新稳定版[Home Assistant 0.111.4](https://www.home-assistant.io/blog/2020/06/10/release-111/)
本次更新除了新增功能和集成外，还包含针对Home Assistant服务器启动过程的优化。

![Home Assistant](/img/en/blog/202007/ha.png)

----

欢迎参与更新并[在论坛留言讨论 :)](https://ai-speaker.discourse.group/)
AI-Speaker 2020年7月
----