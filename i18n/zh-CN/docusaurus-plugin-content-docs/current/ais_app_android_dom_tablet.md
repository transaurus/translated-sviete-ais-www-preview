---
title: "AIS dom Panel"
sidebar_label: AIS dom Panel
---

## 触控面板

该应用提供"触控面板/智能面板"功能，用于控制家庭自动化系统和多媒体设备。

![智能玻璃设置](/img/en/frontend/app_smart_glass_go_to_settings.png)

## 安装

:::info[信息]
在AIS dom网关上，该应用已预装、预配置并支持自动更新。
:::

此外，AIS dom应用可安装在手机或平板上。该应用免费（无广告、内购等）发布于[Google Play](https://play.google.com/store/apps/details?id=pl.sviete.dom)，名为AIS dom。您可扫描下方二维码跳转至Google Play安装：

<center>

![Google Play](/img/en/frontend/barcode_go_to_apk_in_google_play.png)

![Google Play](/img/main/google-play-badge.png)

</center>

应用源代码发布于我们的[公开代码仓库](https://github.com/sviete/AIS-dom)
签名版本同时发布在[系统组件服务站点](https://powiedz.co/ota/)

## 向导配置

首次启动时将出现配置向导，逐步引导完成简易设置流程

![移动端](/img/en/frontend/ais_dom_new_wizard_0_mob_apk.png)

控制面板功能可在应用设置中启用：

![移动端](/img/en/frontend/panel_special_functions.png)

## 视频门禁

应用内置SIP(VOIP)客户端，可兼容支持SIP协议的视频门禁系统。

![移动端](/img/en/frontend/video_doorbell.png)

从应用内视频门禁画面界面，可进入SIP连接设置及摄像头图像设置。

### SIP连接设置

SIP设置中可配置连接参数、调整视频画面及麦克风/扬声器参数。

![移动端](/img/en/frontend/video_doorbell_settings.png)

## NFC标签扫描

若您的平板内置NFC读卡器，可向网关传输存储在NFC标签中的指令或已扫描NFC标签的标识符。

### NFC标签指令

无需语音输入或通过家庭助手聊天窗口输入指令，只需将存储了文本指令的NFC标签贴近平板，即可向网关发送指令。

推荐使用免费应用[NFC Tools](https://play.google.com/store/apps/details?id=com.wakdev.wdnfc&hl=pl)来向NFC标签写入文本。该应用操作直观：启动后首先在"读取"标签页检查NFC标签是否解锁可写。若标签可写入，则切换至"写入"标签页，点击**添加记录**，选择**文本**类型后输入需要网关执行的指令文本（例如``打开Eska Rock电台``），最后点击**确认**完成写入。

![AIS Dom](/img/en/frontend/nfc_tools_1.png)

完成指令文本写入后退出NFC Tools应用。

此时扫描该NFC标签将直接把存储的指令文本发送至网关。

![AIS Dom](/img/en/frontend/nfc_ais_1.png)

这将触发与指令关联的自动化操作

![AIS Dom](/img/en/frontend/nfc_ais_2.png)

通过这种方式可执行任意网关操作——触发自动化场景、控制设备、查询传感器状态、播放音频等。

### NFC标识扫描

若扫描的NFC标签不含文本记录，则仅向网关发送该标签的原始标识符。此时网关将生成**tag_scanned**类型事件，并在事件数据(**event_data**)中传递标签标识符**tag_id**。该功能可将现有NFC标签用于触发网关自动化流程。

具体应用案例详见[NFC标签触发自动化](ais_bramka_tag_automation)说明文档。

## 音频播放器

### 远程控制网关播放器

可通过应用通知栏远程控制网关播放器：
![Mob](/img/en/frontend/panel_remote_controll_audio.png)

### 媒体流重定向

AIS dom应用内置多媒体播放器，可[与网关集成](ais_app_player#dodatkowe-odtwarzacze-ais)，实现将网关媒体内容流转发至远程客户端（控制面板）：

![Smart glass ustawienia](/img/en/frontend/redirect_media_to_client_gate.png)

## 手势控制

长按应用底部工具栏右侧图标可切换至手势控制模式。

![手势控制](/img/en/frontend/remote_gesture_mode.png)

### 定义手势

我们可以在应用设置中定义手势。

从设置菜单中选择"定义手势"选项

![定义手势](/img/en/remote/remote_gesture_mode_2.png)

点击"添加"按钮进入新手势定义界面

![定义手势](/img/en/remote/remote_gesture_mode_3.png)

在屏幕上绘制手势并保存手势与对应指令

![定义手势](/img/en/remote/remote_gesture_mode_4.png)

## 更改助手语音

本应用使用Android系统内置的文本转语音(TTS)引擎。客户端应用(控制面板应用)中的助手语音可通过Android系统设置进行更改。

![手势控制](/img/en/frontend/tts3.png)

要更改语音，请选择系统**设置** > **语言与输入法** > **文字转语音(TTS)**，然后点击"齿轮"图标配置TTS引擎：

![手势控制](/img/en/frontend/tts1.png)

接着选择**安装语音数据**。从可用选项中选择语言和语音：

![手势控制](/img/en/frontend/tts2.png)

## 激活词监听

![智能眼镜设置](/img/en/frontend/app_smart_glass_go_to_settings_5.png)

:::caution[注意]
此功能处于实验阶段，可能无法正常工作 - 例如无法准确检测每个说出的关键词，或将相似词语误识别为关键词。
:::

启用此选项后，"控制面板"将启动监听指定激活词的麦克风服务。这个激活词用于触发命令录制和处理，也称为"关键词"或"触发词"。您还可以调整激活词监听灵敏度。我们使用高精度且轻量级的Porcupine引擎进行激活词检测。

>  **注意：** 监听灵敏度参数。较高的灵敏度值会降低漏检率**但会增加误报频率**。如需了解该功能的工作原理，建议访问解决方案提供商网站：https://picovoice.ai/

我们对家庭助理的运行逻辑进行了调整——当指令来自启用了激活词监听功能的设备时，系统会采取更字面化的解析策略，减少对用户意图的推测。这一改进旨在最大限度降低误触发监听时执行冗余指令的概率。不过该解决方案仍处于早期阶段，因此建议在可控环境下使用该服务（例如夜间关闭），以避免音频播放器等家居设备因误识别而意外启动。