---
title: "AIS Narodowy Bank Polski"
sidebar_label: AIS NBP
---

## 简介

AIS NBP 是家庭助手与 api.nbp.pl 服务的集成，该服务支持从波兰国家银行获取货币汇率和黄金价格数据。

![AIS NBP](/img/en/frontend/ais_nbp1.png)

## 添加集成

要配置 AIS NBP，请进入配置界面后选择集成面板。点击右下角带有"加号"图标的橙色按钮打开可用集成列表，从中选择 **AIS NBP** 集成。

![AIS NBP配置](/img/en/frontend/ais_nbp2.png)

确认添加集成：

![AIS NBP配置](/img/en/frontend/ais_nbp3.png)

选择需要跟踪的货币后点击**确认**：

![AIS NBP配置](/img/en/frontend/ais_nbp4.png)

## 集成实体

该集成会添加多个传感器（数量取决于选择的跟踪货币数量），这些传感器会自动定期更新以反映NBP的最新汇率。

![AIS NBP配置](/img/en/frontend/ais_nbp5.png)

实体可被添加到界面中，从而以自定义方式展示其状态。

## 语音指令

查询NBP实体状态的语音指令与系统其他实体相同：

![AIS NBP配置](/img/en/frontend/ais_nbp6.png)

## 自动化

我们还可以创建以NBP传感器状态为触发条件的自动化规则。例如当黄金价格或特定货币汇率达到预期水平时，系统将发送交易时机提醒通知。

![AIS NBP配置](/img/en/frontend/ais_nbp7.png)

## 删除集成

删除集成需进入配置界面的集成面板，选择删除选项：

![AIS NBP配置](/img/en/frontend/ais_nbp8.png)

## 补充信息

AIS NBP集成最初作为模板案例发布于[家庭助手论坛](https://ai-speaker.discourse.group/t/wlasna-integracja-7-przyklad-nowej-integracji/1029)，用于演示如何为家庭助手开发新集成。

![AIS NBP配置](/img/en/frontend/ais_nbp9.png)