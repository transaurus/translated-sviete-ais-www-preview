---
title: "Integracja Asystentka Jolka"
sidebar_label: Asystentka Jolka
---

## 内置语音助手

该系统包含一个可将语音指令转换为意图并执行关联操作的组件，我们称之为内置语音助手。

![ai](/img/en/frontend/jolka-assistant-integration.png)

您可以通过以下方式与助手交互：

- 在支持语音输入的网页应用中点击麦克风图标
- 通过安装了我们免费应用的Android手机麦克风（应用可在[Google Play](https://play.google.com/store/apps/details?id=pl.sviete.dom)获取）
- 使用带麦克风的专用[遥控器](/docs/ais_remote_index)启动语音服务
- 在应用文本框中直接输入指令

![ai](/img/en/frontend/ais_integration_ai_1.png)

## 可用指令集

此处是助手可[本地解析的指令列表](/docs/ais_app_assistent_commands)（无需连接外部服务）。例如当询问"厨房温度是多少"时，助手能"理解"这是要查询名为"厨房温度"的传感器状态。

当助手无法本地解析指令时，会尝试通过外部服务或互联网搜索获取信息。回答"某某是谁"、"查找关于...的信息"类问题时，助手会调用"Google知识图谱"数据库，该数据库主要聚合维基百科内容以提供简洁答案。我们也会直接查询维基百科及Google等互联网服务。

![ai](/img/en/frontend/ais_integration_ai_2.png)

若集成[Google Home](/docs/ais_app_ai_integration_google_home)，只需在指令前添加"Google"即可直接调用Google助手，例如"Google，今天天气如何"或"Google讲个笑话"等。

## 语音触发自动化

在自动化名称前添加"Jolka: [自动化名称]"前缀即可语音触发。

例如："Jolka: 浇灌草坪":

![指令演示](/img/en/frontend/jolka-assistant-automation.jpeg)

说出[自动化名称]后，助手将自动执行对应名称的自动化流程。

此外，系统中定义的每个自动化任务均可通过语音命令触发。只需说出：

```text
'Jolka {nazwa automatyzacji}'
```

或

```text
'Uruchom {nazwa automatyzacji}'
```

或

```text
'Automatyzacja {nazwa automatyzacji}'
```

通过这种方式，可以轻松为系统中集成的几乎所有设备添加语音控制功能。例如，若需语音启动扫地机器人，只需创建一个名为**吸尘**（或开始吸尘）的自动化任务，该任务将执行**vacuum.start**动作。定义完成后，说出**"启动吸尘"**即可通过语音控制扫地机器人 💪

## 关于语音命令的更多信息

内置命令详情参阅：[内置命令](ais_app_assistent_commands)，自定义新命令方法参见：[添加命令](ais_app_assistent_add_command)。