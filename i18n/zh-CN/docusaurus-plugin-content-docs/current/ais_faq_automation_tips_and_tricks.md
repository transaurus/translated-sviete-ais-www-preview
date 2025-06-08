---
title: "Automatyzacje wskazówki i porady"
sidebar_label: Automatyzacje wskazówki i porady
---

在家庭助理中，几乎所有的功能都可以进行配置。遗憾的是，并非所有选项都能通过用户界面直接设置，但我们正在持续改进这方面的工作。
这里我们将通过实际生活场景案例，指导您如何创建自动化规则定义。

## 如何创建仅在工作日（周一到周五）生效的条件？

请参阅[家庭助理自动化入门指南](/docs/ais_bramka_automation)了解系统自动化配置基础。
添加带有时间类型条件及相应触发器和动作的自动化规则。

![MQTT通信](/img/en/faq/automation_tips_1.png)

查阅Home Assistant关于条件定义的官方文档[condition](https://www.home-assistant.io/docs/scripts/conditions/)

访问[设备控制台](/docs/ais_bramka_remote_ssh)
在**~/AIS/automations.yaml**文件中编辑自动化配置

![MQTT通信](/img/en/faq/automation_tips_2.png)

手动修改配置后，请前往服务器控制台检查配置有效性并重新加载自动化定义。

![MQTT通信](/img/en/faq/automation_tips_3.png)