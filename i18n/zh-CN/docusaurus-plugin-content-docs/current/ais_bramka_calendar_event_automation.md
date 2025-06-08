---
title: "Automatyzacja wyzwalana zdarzeniem z kalendarza"
sidebar_label: Automatyzacja wyzwalana zdarzeniem z kalendarza
---

## 简介

日历可作为外部事件/命令调度器使用，无需将这些命令硬编码到自动化中。

![AIS scan](/img/en/frontend/ais_calendars_10.png)

以下示例将展示如何创建自动化，将日历事件当作命令执行。通过这种方式可控制设备、触发自动化、发送通知或播放音乐等。

### 日历功能

日历在系统中以带属性的二进制传感器实体形式存在。点击侧边栏**开发者工具**进入**状态**选项卡，搜索`calendar.`前缀实体即可查看。

![AIS scan](/img/en/frontend/ais_calendars_8.png)

当日历事件激活时，传感器状态值为**on**，其属性中会显示活跃事件的详细信息。

## 示例 - 将日历事件作为命令执行的自动化

### 自动化命名

添加名为`日历事件`的自动化：

![Calendar](/img/en/frontend/calendar_automation_1.png)

### 触发器设置

选择日历事件传感器的状态变为`on`作为触发条件：

![Calendar](/img/en/frontend/calendar_automation_2.png)

### 执行动作

动作为调用执行命令的服务，命令内容即日历事件消息：

``` yaml
service: ais_ai_service.process
data_template:
  text: '{{ state_attr(''calendar.tomek_sviete_pl'', ''message'') }}'

```

![Calendar](/img/en/frontend/calendar_automation_3.png)

### 自动化代码

可直接复用的YAML格式自动化代码（需将日历名称替换为您自己的）：

``` yaml
alias: Wydarzenie z kalendarza
description: wykonuje wiadomość z kalendarza jako komendę
trigger:
  - platform: state
    entity_id: calendar.tomek_sviete_pl
    to: 'on'
condition: []
action:
  - service: ais_ai_service.process
    data_template:
      text: '{{ state_attr(''calendar.tomek_sviete_pl'', ''message'') }}'
mode: single

```

![Calendar](/img/en/frontend/calendar_automation_4.png)

### 自动化运行机制

Google日历中添加的事件：

![Calendar](/img/en/frontend/calendar_automation_5.png)

会显示在家庭助理日历中：

![Calendar](/img/en/frontend/calendar_automation_6.png)

最新事件会体现在日历实体的状态中：

![Calendar](/img/en/frontend/calendar_automation_7.png)

当日历实体的状态为``on``时，日历中的消息会作为命令被执行（与语音命令或在Jolka聊天框中输入的命令执行方式相同）。
最终Jolka会执行该命令——在本例中即朗读指定文本：

![Calendar](/img/en/frontend/calendar_automation_8.png)

## 自动化方案模板

我们可以基于现成的[自动化方案模板](ais_bramka_automation_blueprint)轻松创建由日历事件触发的自动化流程。

只需完成以下步骤：

1. 选择预定义的**将日历事件作为命令执行**模板

![添加新自动化流程](/img/en/bramka/blueprint_calendar_0.png)

2. 填写并保存定义好的模板：

![添加新自动化流程](/img/en/bramka/blueprint_calendar.png)