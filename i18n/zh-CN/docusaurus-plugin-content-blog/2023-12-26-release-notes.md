---
author: Jola AI-Speaker
authorURL: https://github.com/sviete
author_title: Asystentka
authorImageURL: https://avatars3.githubusercontent.com/u/43966761?s=460&v=4
title: Wersja systemu Home Assistant Supervised
tags: ["home assistant", "zigbee2mqtt"]
---

import BrowserWindow from '@site/src/components/BrowserWindow';

## 尊敬的各位用户，

我们很高兴地宣布一项将积极影响我们平台的重大变革。经过审慎分析和听取用户反馈后，我们决定将操作系统从Android Termux迁移至Linux，并随之将Home Assistant Core升级为Home Assistant Supervised。

![D](/img/en/blog/202312/linux.jpeg)

<!--truncate-->

## 为何做出这一改变？

### 1. 原生集成于Home Assistant的语音助手

2023年Home Assistant团队着力开发了原生集成的语音助手功能。随着该功能趋于完善，我们基于Android系统STT和TTS服务的解决方案已不再是语音助手的必要组件。
![yolca](/img/en/blog/202312/yolca.jpeg)
我们决定全力支持并发展Home Assistant官方提供的解决方案。
在博客文章中我们详细介绍了如何自定义唤醒词"Hey Yolca"：
[自定义唤醒词"Hey Yolca"——开启麦克风的专属口令](https://ai-speaker.discourse.group/t/hey-yolca-wake-word-wlasne-wyrazenie-wlaczajace-mikrofon/3668)
这是关于Home Assistant内置语音助手系列教程的首篇文章。

### 2. Docker容器与Home Assistant插件

Docker容器是轻量级、可移植且自包含的软件单元，能在隔离环境中打包、交付和运行应用程序。
在Android平台上，容器以应用程序形式存在，但事实上Home Assistant本就运行于Docker容器而非Android环境。
迁移至Linux系统后，我们将获得完整的Home Assistant插件生态支持。

![docker](/img/en/blog/202312/docker.jpeg)

### 3. 更便捷的系统更新

转向Linux系统将简化Home Assistant的更新流程。
当Home Assistant运行于Docker容器时，系统更新仅需升级对应容器即可，各类插件同样以容器化方式更新。
这种机制显著提升了更新效率，因为应用程序已打包所有必要依赖和配置，确保在不同环境间无缝迁移。这意味着在一个系统上正常运行的组件，无需调整即可适配其他环境。

![docker2](/img/en/blog/202312/docker2.jpeg)

### 4. Linux软件包

与传统的桌面或服务器Linux发行版相比，Termux环境下可用的软件包数量相对有限。Termux是专为Android系统设计的终端模拟环境，由于Android平台的特定需求和限制，其软件生态规模受到制约。

近年来Termux生态已显著扩展，可用软件包数量持续增长。目前该平台已涵盖文本编辑器、编程语言、开发工具、服务器软件及网络工具等主流应用，但其软件库规模仍无法与拥有数万软件包的传统Linux发行版相提并论。

![debian](/img/en/blog/202312/debian.jpeg)

基于Debian的Linux系统则能提供近乎完整的Linux软件生态，这意味着我们可以在网关上安装更多实用工具。

### 5. 适配器与串口支持

Android系统主要面向智能手机和平板等移动设备设计，默认并不原生支持串行端口(serial port)功能。

大多数适配器厂商(Zigbee/Z-Wave/Thread/LoRa等)不提供USB驱动支持，而是要求通过串口通信。这种通信方式在物联网网关、工业控制系统等专业领域更为常见，而Android设备主要面向USB/蓝牙/Wi-Fi等标准通信接口。

![debian](/img/en/blog/202312/serial.jpeg)

我们曾通过编译Linux内核或使用支持USB通信的适配器等变通方案来突破这些限制，效果参差不齐。现在迁移到Linux系统后，我们将能全面支持各类适配器。

### 感谢各位的理解与支持。本次升级旨在提升系统标准，为您带来更优质的Home Assistant使用体验。

## 如何开始升级？

升级迁移指南详见我们的论坛：

- [DEV1, DEV2, DEV3](https://ai-speaker.discourse.group/t/home-assistant-supervised-na-dev1-dev2-i-dev-bt/3562/1)

- [DEV3 i PRO1](https://ai-speaker.discourse.group/t/home-assistant-supervised-na-dev3-i-pro1/3550/1)

您只需准备SD卡或U盘，下载我们预装配置好的Linux系统镜像，将其烧录至存储介质后即可在新系统上启动网关设备。

![Aktualizacja](/img/en/blog/202312/linux1.png)

## 预装SD卡

对于希望直接购买预装Home Assistant系统的用户，我们商店提供新产品——[128GB SD卡 - HOME ASSISTANT SUPERVISED](https://get-iot.com/index.php?id_product=33&id_product_attribute=42&rewrite=sdcard-128gb-home-assistant-supervised&controller=product&id_lang=2#/32-wersja_bramki-dev3):

[![SD卡](/img/en/blog/202312/sd-card.png)](https://get-iot.com/index.php?id_product=33&id_product_attribute=42&rewrite=sdcard-128gb-home-assistant-supervised&controller=product&id_lang=2#/32-wersja_bramki-dev3)

## AIS网关设备

新销售的AIS网关现已预装Linux系统和Home Assistant Supervised——[AIS DOM DEV-3 物联网&音频网关 - 开发者版](https://get-iot.com/index.php?id_product=27&rewrite=ais-dom-dev-3-bramka-lotaudio-wersja-deweloperska&controller=product&id_lang=2)

[![SD卡](/img/en/blog/202312/dev3.png)](https://get-iot.com/index.php?id_product=27&rewrite=ais-dom-dev-3-bramka-lotaudio-wersja-deweloperska&controller=product&id_lang=2)

-------------------------------------------------------------------------------------

## AIS Android版本，ALFA频道的新动态

我们仍将在ALFA频道发布Android版本。但基于前述原因：系统更新困难、缺乏完整Linux软件包支持、Android系统对串口设备的兼容性限制（如Zigbee等适配器）、以及Android容器化支持缺失，我们强烈建议用户迁移至Linux系统运行Home Assistant Supervised。

![系统更新](/img/en/blog/202312/android.jpeg)

### Python环境

Home Assistant服务端基于Python 3开发运行。我们为网关提供最新稳定版Python，确保与Home Assistant完全兼容。

<BrowserWindow url="http://ais-dom.local">
<center>
![](/img/en/blog/202312/python.png)
</center>
</BrowserWindow>

### MQTT服务

Mosquitto是支持MQTT 5.0/3.1.1/3.1协议的轻量级消息代理，适用于从低功耗AIS网关、单板计算机到完整服务器的全场景部署。

<BrowserWindow url="http://ais-dom.local">
<center>
![](/img/en/blog/202312/mqtt.png)
</center>
</BrowserWindow>

### Clang编译器

Clang是用于编译C/C++/Objective-C等语言的工具链。在网关上，我们使用与Python发行版构建相同的Clang编译器来构建Python扩展模块。用户也可直接编译运行自行开发的C/C++程序。

<BrowserWindow url="http://ais-dom.local">
<center>
![](/img/en/blog/202312/clang.png)
</center>
</BrowserWindow>

### FFmpeg组件

FFmpeg为Home Assistant平台提供音视频流处理能力。

<BrowserWindow url="http://ais-dom.local">
<center>
![](/img/en/blog/202312/ffmpeg.png)
</center>
</BrowserWindow>

### Coder

此版本我们提供了开发者平台``Coder``。通过它，您可以轻松开发自定义程序或直接在AIS网关上编辑系统配置。

<BrowserWindow url="http://ais-dom.local">
<center>
![](/img/en/blog/202312/code.png)
</center>
</BrowserWindow>

### Tmux

我们现在的默认终端是Tmux。Tmux允许我们重新连接到丢失的ssh会话，或帮助管理长时间运行的脚本。此外，我们还可以利用窗口分割功能，在屏幕上同时管理多个程序。

<BrowserWindow url="http://ais-dom.local">
<center>
![](/img/en/blog/202312/tmux.png)
</center>
</BrowserWindow>

### ![](/img/en/blog/202102/honeybee.png) Zigbee2Mqtt

将Zigbee2Mqtt更新至最新版本1.32.1。
最新版本支持[来自380多家制造商的3000多台设备](https://www.zigbee2mqtt.io/supported-devices/)：

[![](/img/en/blog/202306/zigbee2mqtt.png)](https://www.zigbee2mqtt.io/supported-devices/)

详情请参阅Zigbee2Mqtt文档：https://www.zigbee2mqtt.io/

关于Zigbee2Mqtt各版本的新特性，可以在Github上的项目页面阅读：

- [1.32.1](https://github.com/Koenkk/zigbee2mqtt/releases/tag/1.32.1)

### ![](/img/en/blog/202101/hass.png) 家庭助理

最新版本的家庭助理2023.7.2，即我们基于Home Assistant Core的``ais-dom``软件包。
最新版本中[提供了3489个集成](https://www.home-assistant.io/integrations/)：

[![](/img/en/blog/202306/ha.png)](https://www.home-assistant.io/integrations/)

关于Home Assistant各版本的新特性，可以在Home Assistant博客上阅读：

- 2023.7 [![](https://www.home-assistant.io/images/blog/2023-07/social.png)](https://www.home-assistant.io/blog/2023/07/07/release-20237/)
- 2023.8 [![](https://www.home-assistant.io/images/blog/2023-08/social.png)](https://www.home-assistant.io/blog/2023/08/02/release-20238/)
- 2023.9 [![](https://www.home-assistant.io/images/blog/2023-09/social.png)](https://www.home-assistant.io/blog/2023/09/06/release-20239/)
- 2023.10 [![](https://www.home-assistant.io/images/blog/2023-10/social.png)](https://www.home-assistant.io/blog/2023/10/04/release-202310/)

--------

##### AI-Speaker 2023年12月