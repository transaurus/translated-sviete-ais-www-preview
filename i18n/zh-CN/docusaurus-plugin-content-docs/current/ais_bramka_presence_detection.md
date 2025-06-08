---
title: "Konfigurowanie wykrywania obecności"
sidebar_label: Wykrywanie obecności
---

## 简介

存在检测功能旨在确定谁在家中（或其他定义区域），这是自动化的重要数据来源。了解家庭成员是否在家或具体位置，能实现丰富的自动化场景，例如：

- 当孩子到达学校时发送通知
- 下班离开办公区域时自动开启家中空调
- 夜间检测到车辆进入前院区域时，自动开启大门并点亮外围照明30分钟

![存在检测](/img/en/bramka/presence_detection_14.png)

## 存在检测

家庭助理系统支持多种存在检测方式。我们推荐的最简便方法是启用AIS dom应用的位置上报功能——手机登录网关后，可轻松将手机与成员绑定，直接向家庭网关传输位置变更数据。

![AIS dom GPS定位](/img/en/bramka/presence_detection_00.png)

另一款提供精确定位数据的应用是OwnTracks，同时支持Android和iOS系统。该应用与AIS dom同样免费开源，能将检测到的位置变化直接推送至家庭助理系统。您可通过系统配置中的集成功能进行设置，具体步骤详见[OwnTracks集成文档](/docs/ais_app_owntracks)。

## 人员管理

添加人员后可关联多个位置上报设备。当使用多个追踪设备时，系统会根据设备类型确定优先级：

- 固定设备（路由器或蓝牙定位器）
- 移动设备（GPS）

居家时优先采用固定设备定位，其次使用GPS数据；外出时则优先采用GPS定位，其次参考固定设备数据。

### 添加人员

添加新成员需进入配置界面选择**人员管理**选项。

![添加人员](/img/en/bramka/presence_detection_10.png)

点击屏幕右下角橙色"+"按钮打开人员添加表单，按以下示例关联位置上报设备。

![添加人员](/img/en/bramka/presence_detection_9.png)

### 设置人员照片

在添加或编辑人员时，您可上传其照片，该照片将显示在应用程序和地图中。

![添加人员照片](/img/en/bramka/presence_detection_8.png)

地图和应用卡片中的人员信息现在将附带照片显示。

![添加人员](/img/en/bramka/presence_detection_11.png)

## 区域设置

区域功能允许为地图上的特定范围命名。这些命名区域可用于标识被追踪用户的当前位置，或作为自动化触发条件（进入/离开区域）。区域配置可在集成页面的系统设置中完成。

### 添加区域

请前往配置菜单选择**区域**选项以创建新区域。

![添加区域](/img/en/bramka/presence_detection_12.png)

参照下方示例填写区域表单，添加您需要的特定区域。

![添加区域](/img/en/bramka/presence_detection_13.png)

## 基于位置的自动化

当人员进入或离开某区域时，可触发区域及地理围栏相关的自动化规则。创建基于位置的自动化时，请选择**区域**作为触发器类型，并指定需要监测位置的人员。

![添加自动化规则](/img/en/bramka/presence_detection_15.png)

下一步选择目标区域并设置事件类型（进入区域或离开区域）。

![添加自动化规则](/img/en/bramka/presence_detection_16.png)

## 自动化蓝图

通过现成的[自动化蓝图](ais_bramka_automation_blueprint)，可轻松创建基于位置变化的自动化规则。

只需：

1. 选择预定义的**离开区域通知**蓝图

![添加新自动化规则](/img/en/bramka/blueprint_zone_0.png)

2. 填写并保存定义好的模板：

![添加新自动化规则](/img/en/bramka/blueprint_zone.png)