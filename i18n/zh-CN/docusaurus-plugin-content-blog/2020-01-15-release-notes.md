---
author: Jola AI-Speaker
authorURL: https://github.com/sviete
authorImageURL: https://avatars3.githubusercontent.com/u/43966761?s=460&v=4
title: Wersja systemu 0.103 Zigbee
---

## 2020年1月15日系统版本0.103.8，Zigbee支持！

![](/img/en/blog/202001/zigbee2mqtt_logo.png)

此版本新增了**无需使用厂商网关即可便捷操作Zigbee设备**的功能。

<!--truncate-->

该解决方案基于[Zigbee2MQTT](https://www.zigbee2mqtt.io/)项目，并与我们的软件深度集成，您可轻松将Zigbee设备接入运行家庭助理系统的智能家居整体架构中。

只需将[预先刷写固件](https://www.zigbee2mqtt.io/getting_started/flashing_the_cc2531)的CC2531设备插入USB端口，家庭助理将自动[识别该USB设备](/docs/ais_app_integration_usb#zigbee-usb-sniffer)，语音提示Zigbee服务启动后，应用界面会自动出现新选项。

![Zigbee2MQTT](/img/en/blog/202001/zigbee2mqtt_new_menu.png)

更多细节请参阅[Zigbee集成文档](/docs/ais_app_integration_zigbee)

您可在Zigbee2MQTT项目页面查看[**约500款设备（来自100家厂商）**](https://www.zigbee2mqtt.io/information/supported_devices)的支持列表。

## AI-Speaker社区论坛！

应用户需求，我们新增了文章评论功能，若用户愿意参与讨论并互助，或将发展成正式论坛。我们将很快邀请所有人注册账号并参与讨论，您可先了解我们初步拟定的社区准则：https://ai-speaker.discourse.group/t/witamy-na-spolecznosciowym-forum-ai-speaker/28

我们希望协助建设这个平台并交由社区自治——积极参与内容发布的用户将自动晋升为版主/管理员。

如果您有基于家庭助理的实践项目并愿意分享，我们将不胜感激 🥰
欢迎所有愿意展示项目的用户前往**项目专区**发布：https://ai-speaker.discourse.group/c/projekty 优质内容越多，这个平台就越有活力。

![Discourse](/img/en/blog/202001/discourse_manifest.png)

## 端口标准化

网关上的服务将继续沿用原有端口，同时新增标准化（广为人知的）端口支持。具体运作机制我们已在[论坛详细说明](https://ai-speaker.discourse.group/t/dlaczego-porty-uslug-dzialajacych-na-bramce-sa-niestandardowe/57)

Nazwa      | Protokół | Porty | Komenda/URL                                               | Opis
----       | ----     | ------- | -------                                                | -----------
 Aplikacja | http     | **80** / `8180`  | [http://ais-dom.local](http://ais-dom.local) | serwer http
 FTP       | ftp      | **21** / `1024`  | [ftp://ais-dom.local](ftp://ais-dom.local)   | serwer ftp
 SSH       | ssh      | **22** / `8022`  | ```ssh ais-dom```         | serwer ssh
 MQTT      | mqtt     | **1883**  | ```mosquitto_sub -h ais-dom.local -t '#'```     | serwer mqtt

## 配置备份

在网关软件配置中新增了[网关配置备份与恢复](/docs/ais_bramka_configuration_software#kopia-zapasowa-konfiguracji)功能。此处可验证网关设置有效性、创建备份并上传至集成商门户。由于配置可能包含服务访问密码和令牌，建议使用密码加密备份文件。加密后的备份仅能通过输入密码进行查看/恢复。

W tym miejscu możesz, sprawdzić poprawność ustawień bramki, wykonać jej kopię i przesłać ją do portalu integratora. Ponieważ konfiguracja może zawierać hasła i tokeny dostępu do usług, zalecamy zaszyfrować ją hasłem. Gdy kopia jest zabezpieczona hasłem, to można ją otworzyć/przywrócić tylko po podaniu hasła.

![网关软件](/img/en/bramka/config_ais_dom_section1_2.png)

## 独立音频面板

音频视图已迁移至应用的独立面板。

![音频面板](/img/en/blog/202001/audio_new_tab.png)

从本版本起，我们将仅提供/锁定一个视图界面用于展示示例卡片。

![默认视图](/img/en/blog/202001/default_view.png)

## USB设备识别

网关内置后台USB服务，用于监测USB设备连接状态变化（插拔事件）。该服务通过Linux系统的inotify机制监听事件，并将其转换为家庭助理可识别的格式。当检测到新设备时，家庭助理将通过语音播报设备类型。若设备受支持，系统将自动执行后续操作，包括：

- 挂载存储设备
- 启用音频卡
- 启动Zigbee服务

详见[USB设备识别文档](/docs/ais_app_integration_usb)

![USB HID设备](/img/en/bramka/usb_integration_zigbee.png)

## 添加FTP远程存储

为响应论坛提案[局域网网络磁盘集成](https://ai-speaker.discourse.group/t/integracja-z-dyskiem-sieciowym-w-sieci-lokalnej/94)，我们新增FTP支持，并技术性说明网关预装的Rclone远程存储解决方案原理，详见[网络磁盘-Rclone](https://ai-speaker.discourse.group/t/dyski-sieciowe-rclone/97)

![FTP配置1](/img/en/blog/202001/rclone_ftp.png)
![FTP配置2](/img/en/blog/202001/rclone_ftp2.png)

## 应用内PIN码认证

对于Wear OS系统，最便捷的方式是通过一次性PIN码完成与网关的配置。

操作流程非常简单：只需在**加密隧道**选项中选择**生成PIN码**

![自动化设置](/img/en/frontend/ais_dom_wizard_4_wear_apk.png)

随后将生成的代码在两分钟内输入Wear应用即可完成配对

![自动化流程](/img/en/frontend/ais_dom_wizard_5_wear_apk.png)

完整说明详见文档 [AIS dom Wear OS](/docs/ais_app_android_dom_wear)

## 遥控器导航功能扩展

我们在**家居**菜单中新增了**场景**分组，该分组包含系统中所有预定义场景，可通过遥控器直接触发。

同时**设备**分组现包含以下子类目：

- 开关
- 照明
- 传感器
- 温控器
- 窗帘
- 吸尘器
- 门锁
- 摄像头
- 风扇

## TAURON - 电网返送电量数据获取

我们更新了由[Piotr Machowski](https://github.com/PiotrMachowski/Home-Assistant-custom-components-Tauron-AMIplus)开发的TAURON集成，新增电网返送电量数据获取功能。

该功能可获取6类传感器数据：

- 年度用电量
- 月度用电量
- 日用电量
- 年度返送电网电量
- 月度返送电网电量
- 日返送电网电量

结合发电数据，这些指标能清晰显示电力盈余情况——特别适用于存在电力过剩时（例如冬季利用余电供暖替代燃气）的能源调配决策。

![TAURON集成界面](/img/en/frontend/integration_tauron_4.1.png)

## Home Assistant

最新稳定版 [Home Assistant 0.103.0](https://www.home-assistant.io/blog/2019/12/11/release-103/)

最值得关注的改进是支持通过YAML格式在应用中定义/编辑自动化规则。每个触发器、条件或动作都可以YAML形式编辑，这使得在自动化编辑器中能定义复杂逻辑，并快速复制自动化规则片段。

![智能助手](/img/en/blog/202001/automatuon_yaml_editor.png)

----

欢迎升级并[参与论坛讨论 :)](https://ai-speaker.discourse.group/)

AI-Speaker 2020年1月
----