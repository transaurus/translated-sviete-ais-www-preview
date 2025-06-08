---
title: "Dodawanie komendy"
sidebar_label: Dodawanie komendy
---

## 自动化中的语音指令

添加自定义语音指令的最简单方式，是在自动化名称前添加前缀"Jolka: [自定义指令]"。

例如："Jolka: 浇灌草坪"。**通过这种方式添加的指令会覆盖内置指令，从而完全根据个人需求定制助手行为。**

![指令运作示意图](/img/en/frontend/jolka-assistant-automation.jpeg)

还可为指令添加别名，实现通过多条不同指令触发同一自动化。

![指令别名设置](/img/en/frontend/jolka-assistant-automation-aliases.jpeg)

## 助手响应

在定义的自动化中可添加系列操作，包括设备控制和服务调用。其中可包含语音响应服务：

![语音响应操作](/img/en/frontend/action_say_it.jpeg)

## 对话模式

通过"Jolka:"前缀命名的自动化可构建简单对话流程：助手执行语音指令后，将询问是否需要其他操作并启用网关麦克风接收下条指令：

![对话操作设置](/img/en/frontend/action_dialog.png)

该对话模式的实际运作

![对话流程演示](/img/en/frontend/action_dialog_2.png)

## 高级选项

**ais_ai_service.say_it**
文本转语音服务 - 通过助手朗读文本内容。

可通过开发者工具测试/调用服务

![新指令测试界面](/img/en/frontend/conversation_dev_service.png)

使用**data_template**模板功能可动态传递信息至服务。模板创建/验证需通过开发者工具

![模板测试界面](/img/en/frontend/conversation_dev_template.png)

编辑自动化时可添加YAML格式的``data_template``模板：

```yaml
service: ais_ai_service.say_it
data_template:
  text: 'Jest godzina {{ states(''sensor.time'') }} uruchamiam podlewanie'
```

![模板配置示意图](/img/en/frontend/conversation_template.jpeg)

详见[Home Assistant开发者文档](https://www.home-assistant.io/docs/configuration/templating/)