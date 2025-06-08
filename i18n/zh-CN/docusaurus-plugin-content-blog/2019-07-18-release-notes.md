---
author: Celina AI-Speaker
authorURL: https://github.com/sviete
authorFBID: 1186570423
title: Wersja systemu 0.95.7  Wykrywanie obecności, mapa, automatyzacje i optymalizacja
---

## 系统版本 0.95.7（2019年7月18日发布）

### 存在检测

存在检测功能旨在判断家中（或其他定义区域）是否有人以及具体是谁，这是自动化规则的宝贵数据源。了解家庭成员的位置状态可开启丰富的自动化场景，例如：

- 当孩子到达学校时发送通知
- 离开办公室时自动开启家中空调
- 夜间检测到车辆进入大门区域时，自动开启大门并点亮30分钟户外照明

![存在检测](/img/en/bramka/presence_detection_14.png)

<!--truncate-->

### 自动化基础指南

家庭助理提供广泛的自动化配置选项。在开始创建实用家居自动化规则前，理解基础概念至关重要。本指南将通过"日落自动开灯"的简单案例，逐步讲解自动化规则的基本配置流程与核心功能。

![存在检测](/img/en/bramka/automation8.png)

### 代码优化

我们对语音识别进度显示界面(RecognitionProgressView)进行了代码优化。优化后设备CPU负载显著降低，处理器温度同步下降（具体数据参见下方图表）。在新增的FAQ章节中，我们以CPU温度传感器为例详细说明了如何为系统添加新传感器。

![CPU温度](/img/en/blog/cpu_temp_after_optimalization.png)

### 遥控器操作界面

通过遥控器操作时（不使用手机应用），设备会显示语音指令识别进度界面，实时反馈系统理解的指令内容及执行状态。该界面在通过HDMI连接显示器/TV时可见，会显示网关当前IP地址、连接类型(WiFi/以太网)。自0.95.6版本起，界面新增了实时日期时间显示。下方为界面设计示意图。

![后台界面](/img/en/bramka/ais_dom_splash_screen.png)

### 拼读功能

我们希望产品对视力障碍用户和老年群体同样友好。为此我们新增了拼读功能——例如助手可以逐字母拼读设备唯一标识符。
该功能可通过遥控器调用：选中设备ID项后按下"OK"键即可触发拼读。
您还可以要求助手拼读系统内任意元素的状态，只需说出"拼读"加上元素名称，例如：

```text
Przeliteruj unikalny identyfikator bramki
```

文档中完整列出了[家庭助手支持的内置语音指令](/docs/ais_app_assistent_commands)

### 其他重要更新

- 设备启动时新增音乐前奏及语音播报系统状态，优化了三大核心应用模块
- YouTube搜索结果分页显示，展示查询结果总数（上限100万条，YouTube限制），每页10条结果，支持通过遥控器/应用进行前后页导航
- 改进网络设备扫描机制，支持通过MAC地址识别设备
- 集成最新版Home Assistant <a href="https://www.home-assistant.io/blog/2019/06/26/release-95/" target="_blank">0.95</a>