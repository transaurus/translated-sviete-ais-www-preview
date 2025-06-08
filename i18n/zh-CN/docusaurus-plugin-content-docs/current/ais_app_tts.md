---
title: "AIS Lokalny TTS"
sidebar_label: AIS Lokalny TTS
---

## AIS 本地文本转语音(TTS)

系统具备将文本转换为语音的功能。

通过该功能，"Jolka"可与用户对话——回答提问并确认指令执行状态。

![TTS](/img/en/frontend/ais_tts_app.png)

## 文本转语音服务

高阶用户可在[自定义自动化及指令定义](/docs/ais_app_ai_integration#automatyzacje-uruchamiane-komendą)中调用该功能。

文本转语音通过``ais_ai_service.say_it``服务实现，可在自动化中调用该服务并传入任意文本及其他参数：

![TTS](/img/en/frontend/ais_tts_service_say_it.png)

## 语音状态监测

系统还提供``ais_speech_status``事件来反馈TTS机制状态：

![TTS](/img/en/frontend/ais_tts_service_speach_status.png)

通过TTS状态监测，可精准获知Jolka（Marya、Allison等）语音启停时机。该特性可用于实现多语言逐条播报自动化——在连续播报动作间插入等待``ais_speech_status``状态变为``DONE``的触发器

![AIS TTS](/img/en/frontend/ais_tts_speech_status.png)

实现该功能的示例自动化代码如下：

``` yaml
alias: Komunikat powitalny w 3 językach
description: ''
trigger:
  - platform: event
    event_type: ais_key_event
    event_data:
      code: 1
condition: []
action:
  - service: ais_ai_service.say_it
    data:
      text: Witamy w parku rozrywki (komunikat po polsku)
      language: pl_PL
      voice: Jola
  - wait_for_trigger:
      - platform: event
        event_type: ais_speech_status
        event_data:
          status: DONE
  - service: ais_ai_service.say_it
    data:
      language: en_US
      voice: Allison
      text: Welcome to the amusement park (announcement in English)
  - wait_for_trigger:
      - platform: event
        event_type: ais_speech_status
        event_data:
          status: DONE
  - service: ais_ai_service.say_it
    data:
      language: uk_UA
      voice: Mariya
      text: Ласкаво просимо до парку розваг (анонс українською мовою)
mode: single

```

自动化执行过程如图所示——可见系统仅在收到前一条TTS播报完成信号后才会触发下一条播报：

![AIS TTS](/img/en/frontend/ais_tts_speech_trace.png)

还可构建以下自动化场景：在语音播报时调低音乐音量/开启灯光，或将TTS状态写入「助手」类型实体，最终在用户界面可视化呈现语音状态。

我们在论坛展示了具体案例：[AI-Speaker论坛](https://ai-speaker.discourse.group/)