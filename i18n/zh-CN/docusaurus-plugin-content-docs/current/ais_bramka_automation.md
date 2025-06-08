---
title: "Definiowanie Automatyzacji"
sidebar_label: Definiowanie Automatyzacji
---

## 简介

设备连接并配置完成后，现在可以添加第一个自动化规则。本指南将演示如何创建一个简单的自动化规则，在日落时开启照明。

## 进入自动化设置

在家庭助手应用中，点击左上角菜单图标打开菜单，然后点击配置。

![自动化列表界面](/img/en/bramka/automation1.png)

## 自动化列表界面

现在点击"自动化"。这是系统内管理所有自动化规则的列表界面。

![进入自动化设置](/img/en/bramka/automation2.png)

## 定义自动化规则

点击右下角的橙色按钮创建新自动化。将显示自动化配置界面。

![添加新自动化](/img/en/bramka/automation3.png)

### 设置自动化名称

首先设置名称。输入"在日落时开启入口照明"。

![设置自动化名称](/img/en/bramka/automation4.png)

### 自动化触发器

第二步是确定触发条件。本例中我们使用"日落"事件作为触发器。可以添加时间偏移量，例如在日落前15分钟开启照明（因为日落后天色已暗）。

在触发器部分点击下拉列表，将触发器类型改为"太阳"。然后选择"日落"。由于我们希望自动化在实际日落前15分钟触发，因此添加-0:15的时间偏移量。

![添加新自动化](/img/en/bramka/automation5.png)

### 自动化动作

定义完触发器后，向下滚动到"动作"部分（可跳过可选的"条件"部分）。

请确保操作类型设置为**设备**，并从**外部灯具**列表中选择您的设备——当然，根据您对设备的命名，实际选项可能有所不同。接着在**操作**字段中选择**开启外部灯具**。

![Dodanie nowej automatyzacji](/img/en/bramka/automation6.png)

:::tip[小技巧]
您可以在同一自动化规则中添加`延迟`操作，随后再添加`关闭`操作，从而实现集中控制。
:::

![Dodanie nowej automatyzacji](/img/en/bramka/automation_6_1.png)

点击右下角的橙色按钮保存自动化规则定义。

### 编辑与管理

**恭喜！您已成功添加第一条自动化规则 :)**

您可以返回自动化列表界面，在此管理并编辑系统中的所有自动化规则。

![Dodanie nowej automatyzacji](/img/en/bramka/automation8.png)

在此界面您还可以手动触发新创建的自动化规则进行测试

![Dodanie nowej automatyzacji](/img/en/bramka/automation9.png)

## 自动化方案

上述自动化规则可通过现成的[自动化方案](ais_bramka_automation_blueprint)快速创建。

只需：

1. 选择预设方案**日落照明**

![Dodanie nowej automatyzacji](/img/en/bramka/blueprint_light_0.png)

2. 完善并保存定义好的模板：

![Dodanie nowej automatyzacji](/img/en/bramka/blueprint_light.png)