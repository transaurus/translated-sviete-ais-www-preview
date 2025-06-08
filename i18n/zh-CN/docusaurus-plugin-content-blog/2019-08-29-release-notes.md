---
author: Celina AI-Speaker
authorURL: https://github.com/sviete
authorFBID: 1186570423
title: Wersja systemu 0.97.5 Obsługa wywołań zwrotnych HTTP, kolejne uproszczenia w aplikacji
---

## 2019年8月29日发布的系统版本0.97.5

### 提升视障用户应用可访问性

我们在Android应用中为按钮添加了标签，以支持TalkBack等辅助功能。网页端也进行了类似优化，旨在让家庭助理的用户界面实现全面无障碍化。

<!--truncate-->

### 应用界面简化

为迎接1.0版本，我们正在简化家庭助理应用的默认用户界面。从0.97版起，网关配置、实用链接和文档将拥有独立页面。

#### 网关配置

通过**AIS dom网关设置**菜单项可访问网关配置界面，用于管理物联网音频网关。该配置包含4个功能模块，详见新文档页面[网关配置](/docs/ais_bramka_configuration)

![AIS dom网关设置](/img/en/frontend/ais_dom_gate_settings_voice.png)

#### 实用链接

网关运行的各项服务链接已整合为菜单新选项[实用链接](/docs/ais_bramka_services)

![AIS dom实用链接](/img/en/frontend/ais_dom_links.png)

#### 文档

菜单新增**文档**选项可直接跳转至官方用户文档站点。

![AIS dom文档](/img/en/frontend/ais_dom_docs.png)

### HTTP回调支持

新增HTTP回调功能，用于接收外部事件通知。所有配置为回调触发的服务都会生成唯一公开URL，支持从任意位置向家庭助理发送数据。

该功能支持从互联网向网关推送通知。

例如可通过移动应用向网关发送位置信息——详见[存在检测](/docs/ais_bramka_presence_detection)功能说明

![AIS dom网页钩子](/img/en/frontend/integration_owntracks.png)

接收dialogflow服务的通知

![AIS dom网页钩子](/img/en/frontend/integration_dialogflow.png)

及/或IFTTT服务的通知

![AIS dom网页钩子](/img/en/frontend/integration_ifttt.png)

回调通知管理功能可在[网关远程访问配置](/docs/ais_bramka_configuration#konfiguracja-zdalnego-dostępu-do-bramki)中设置
![AIS dom webhooks](/img/en/frontend/ais_dom_webhooks.png)

### 新增二进制软件包仓库

我们已在自有服务器上建立新的二进制软件包仓库（不再从Github获取安装包）。所有软件包均已更新至最新版本，并针对最低Android API 24（此前支持Android 5的API 21）进行了编译优化。

> 我们不会自动切换至新仓库，常规安装过程中也不会自动推送这些新二进制包。标准更新后需额外执行"应用完全重置"流程。**建议您切换至新仓库以优化/加速设备运行流程。**

切换至新二进制软件包仓库步骤：

1. 执行标准自动更新
2. 执行"应用完全重置" - 该流程说明详见文档[应用完全重置](/docs/ais_bramka_reset_ais_step_by_step)，内含完整重置过程的演示视频。

### 其他重要变更

- 新增单声道音频切换功能（播放时合并音频通道）
该选项可通过应用及遥控器启用。适用于以下场景：网关仅连接单个扬声器但音频含多声道；或使用耳机时用户单侧听力更佳。

- 浏览器仅在其支持语音输入（webkitSpeechRecognition）且连接加密时显示麦克风图标

http:

![AIS dom webhooks](/img/en/blog/no_mic_http.png)

https:

![AIS dom webhooks](/img/en/blog/yes_mic_https.png)

- 应用内新增版本更新通知

![AIS dom update notification](/img/en/blog/update_notification.png)

- 首次启动时可在向导第二步（注册账户后，房屋位置检测前）连接WiFi

[首次启动 -> 房屋定位 -> WiFi配置](/docs/ais_bramka_first_run#lokalizacja-twojego-domu)

- 支持SSH密码认证登录

[局域网访问 -> SSH](/docs/ais_bramka_remote_ssh)

- 优化麦克风功能。当麦克风被锁定时，系统将自动重置USB设备，无需物理插拔。

![AIS dom webhooks](/img/en/blog/repo_update.png)

- 最新稳定版 Home Assistant <a href="https://www.home-assistant.io/blog/2019/08/07/release-97/" target="_blank">0.97</a>