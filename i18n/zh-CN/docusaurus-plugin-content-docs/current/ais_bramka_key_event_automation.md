---
title: "Automatyzacja wyzwalana przyciskiem"
sidebar_label: Automatyzacja wyzwalana przyciskiem
---

## 简介

网关支持USB HID类设备（人机交互设备），主要用于与用户进行交互。当键盘或其它USB HID控制器接入网关时，按键动作会作为事件传递给家庭助理系统。这类事件可触发自动化场景，下文将通过实例进行说明。

![AIS按钮](/img/en/bramka/ais_remote_key_events.jpg)

### 识别"按键按下"事件

当USB控制器正确连接并被系统识别后，家庭助理会播报"已添加设备..."提示音。

在[无显示器控制模式](ais_bramka_first_run#sterowanie-bez-monitora)下，控制器按键代码仅作为**ais_key_event**类型事件发送至家庭助理，系统不会处理这些信号。而在[显示器控制模式](ais_bramka_first_run#sterowanie-na-monitorze)下，控制器按键代码既会作为**ais_key_event**事件发送至家庭助理，也会被系统处理。

要查询当前按键的对应代码，只需检查实体状态：**binary_sensor.ais_remote_button**会显示最近触发的按键代码。

![AIS按钮](/img/en/bramka/ais_remote_key_events_1.png)

为方便使用，可将该实体添加为应用卡片：

![AIS按钮](/img/en/bramka/ais_remote_key_events_2.png)

卡片代码如下：

``` yaml
type: button
tap_action:
  action: none
entity: binary_sensor.ais_remote_button
show_state: true
hold_action:
  action: none
show_name: true
icon: 'hass:keyboard-settings'
name: Kod przycisku kontrolera HID

```

通过该卡片可直观查看HID控制器各按键对应的代码。

![AIS按钮](/img/en/bramka/ais_remote_key_events_0.png)

确定触发自动化所需的按键代码后，即可开始配置自动化场景。

### 添加自动化规则

1. 命名自动化规则（例如"控制器按键启动收音机"）

![AIS按钮](/img/en/bramka/ais_remote_key_events_3.png)

2. 设置触发器 - ais_key_event事件

![AIS按钮](/img/en/bramka/ais_remote_key_events_4.png)

3. 定义执行动作

![AIS按钮](/img/en/bramka/ais_remote_key_events_5.png)

### 自动化规则代码

YAML格式的自动化规则代码：

``` yaml
alias: Włączenie radia Zet po naciśnięciu przycisku  z kodem 15 na kontrolerze
description: ''
trigger:
  - platform: event
    event_type: ais_key_event
    event_data:
      code: '15'
condition: []
action:
  - service: ais_ai_service.process
    data:
      text: Włącz radio ZET
  - device_id: ''
    domain: ''
    entity_id: ''
mode: single
```

在自动化编辑界面切换至YAML模式后，可直接粘贴该代码

![AIS按钮](/img/en/bramka/ais_remote_key_events_6.png)

## 自动化方案模板

通过按钮按下事件触发的自动化，可以基于现成的[自动化方案模板](ais_bramka_automation_blueprint)轻松创建。

只需：

1. 选择预定义的方案模板**按下按钮执行命令**

![添加新自动化](/img/en/bramka/blueprint_button_0.png)

2. 填写并保存定义好的模板：

![添加新自动化](/img/en/bramka/blueprint_button.png)