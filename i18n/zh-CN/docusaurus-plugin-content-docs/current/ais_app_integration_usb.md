---
title: "USB rozpoznawanie urządzeń"
sidebar_label: Urządzenia USB
---

## 引言

我们在网关上提供了一项后台运行的USB服务，其核心功能是监测USB设备的状态变化（连接与断开）。该服务通过Linux系统的inotify机制监听事件，并将其转换为家庭助理可识别的格式。当检测到新设备接入时，家庭助理将通过语音播报设备类型。若该设备受支持，系统将自动执行相关操作，例如：

- 挂载存储设备  
- 启用音频设备  
- 启动Zigbee通信服务

## USB存储设备

当U盘、SD卡或支持MTP协议的设备（如相机或手机）接入AIS dom网关时，网关将以USB主机模式进行管理。此模式下，网关会为USB端口VBUS线路提供5V电压，外部存储设备将被识别为可访问的磁盘。家庭助理会通过"外部磁盘已连接"的语音提示确认设备识别，用户可立即浏览存储内容或播放音频文件。

![音频面板](/img/en/bramka/usb_integration_drive.png)

## USB音频设备

网关音频模块支持三种内置音频传输接口：

- AV接口  
- HDMI接口  
- 光纤接口

```
cat /proc/asound/cards
0 [AMLM8AUDIO     ]: AML-M8AUDIO - AML-M8AUDIO
                     AML-M8AUDIO
```

此外，任何符合USB音频设备规范且工作在配件模式的设备均可作为音频传输接口。当兼容设备接入时，家庭助理将通过语音提示设备状态，并自动将其设为默认音频输出设备。

![音频面板](/img/en/bramka/usb_integration_audio.png)

```
$ cat /proc/asound/cards
 0 [AMLM8AUDIO     ]: AML-M8AUDIO - AML-M8AUDIO
                      AML-M8AUDIO
 1 [AUDIO          ]: USB-Audio - USB  AUDIO
                      USB  AUDIO at usb-xhci-hcd.0.auto-1.2, full speed
```

高级用户可通过控制台配置音频设备，该功能面向需要自定义音频设置的用户，详细教程将在家庭助理项目论坛发布。

```
$ su -c "tinymix -D 0"
Mixer name: 'AML-M8AUDIO'
Number of controls: 10
ctl	type	num	name                                     value
0	INT	2	DAC Digital Playback Volume              251 251
1	ENUM	1	DAC Extra Digital Gain                   0dB
2	BOOL	1	Audio i2s mute                           Off
3	ENUM	1	Output Swap                             
4	BOOL	1	Audio spdif mute                         Off
5	BOOL	1	Ext Spk Switch                           Off
6	ENUM	1	Lineout right N switch                   LORN_SEL_DACR_INV
7	ENUM	1	Lineout right P switch                   LORP_SEL_DACR
8	ENUM	1	Lineout left N switch                    LOLN_SEL_DACL_INV
9	ENUM	1	Lineout left P switch                    LOLP_SEL_DACL
```

## USB HID配件

USB人机交互设备(HID)主要用于系统控制，典型设备包括：

- AI-Speaker射频遥控器  
- 键盘  
- 鼠标  
- 游戏手柄  
- 条码扫描器

USB HID（人机接口设备）的定义规定了HID设备与支持此类设备的主机进行通信的标准方式。
若设备符合USB HID标准，则应当被家庭助理自动识别并添加，系统将通过语音提示告知用户：

![HID USB](/img/en/bramka/usb_integration_hid.png)

## Zigbee USB嗅探器

当Zigbee USB CC2531设备插入网关USB端口后，家庭助理将通过语音通知用户，同时启动Zigbee通信服务及设备配置应用：

![USB Zigbee](/img/en/bramka/usb_integration_zigbee.png)

具体操作详见[Zigbee2MQTT](/docs/ais_app_integration_zigbee)功能说明

## libusb库

网关内置[libusb](https://libusb.info/) C语言库，该库为USB设备提供通用访问接口。
该库支持运行在网关上的应用程序与USB硬件通信，兼容从USB 1.0到3.1（最新版）的所有协议版本。