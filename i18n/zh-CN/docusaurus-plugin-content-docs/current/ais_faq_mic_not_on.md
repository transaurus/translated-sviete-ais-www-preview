---
title: "Czy macie stale włączony mikrofon?"
sidebar_label: Czy macie stale włączony mikrofon?
---

## 麦克风是否始终开启？

**我们没有启用**，在我们的解决方案中，用户必须在发出语音指令前物理开启麦克风。

## 可以使用哪些麦克风发出指令？

目前开箱即用状态下，我们支持近距离（即近场）语音控制功能，具体使用哪种麦克风发出语音指令对我们而言没有限制。

我们支持以下几种方式：

- 网页应用内置麦克风
- 安装了我们免费应用的Android手机麦克风（应用可在Google Play获取）
- 搭载Wear OS系统并安装我们免费应用的智能手表麦克风（应用可在Google Play获取）
- 我们专用射频遥控器内置麦克风

我们确保上述麦克风的功能可靠性。
您家中的USB麦克风很可能也能正常工作，但我们无法对此作出保证。

## 为什么麦克风不保持常开状态？

麦克风持续开启会带来若干尚未完全解决的问题：

- 隐私争议
要实现唤醒词（即指令前缀词）识别，必须持续录音并将语音实时转换为文字进行分析。这极易引发窃听谈话的质疑。目前所有提供此类解决方案的厂商都面临这个问题。

- 麦克风阵列
仅开启麦克风还不够，需要专业设备（麦克风阵列）才能实现远场语音指令的定向拾取，并过滤室内的音乐和其他环境噪声。这类解决方案目前成本较高且效果不稳定。

- 处理器负载
持续录音和语音转文本会额外消耗设备处理器资源（约30%负载），导致电力消耗增加。我们致力于保持设备环保节能，当前持续运行的网关月耗电量不超过2千瓦时（约合每月1元电费）。

## 如何添加远场控制和常开麦克风功能？

本产品完全开源，提供公开源代码，具有root权限和USB接口——我们不限制用户自行添加此类功能。

可尝试使用索尼PlayStation Eye摄像头作为麦克风方案，该设备配备4麦克风阵列（详见https://en.wikipedia.org/wiki/PlayStation_Eye#Microphone），网购价格约15兹罗提。

训练唤醒词检测（wake word detection、keyword spotting、trigger word detection、hotword detection）本身可采用现成的开源方案，例如以下项目：
https://github.com/Picovoice/Porcupine 
https://github.com/MycroftAI/mycroft-precise