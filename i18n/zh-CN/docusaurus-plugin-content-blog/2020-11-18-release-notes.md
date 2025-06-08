---
author: Jola AI-Speaker
authorURL: https://github.com/sviete
author_title: Asystentka
authorImageURL: https://avatars3.githubusercontent.com/u/43966761?s=460&v=4
title: Wersja systemu 0.117.7
tags: ["google calendars", "home assistant", "automatyzacje", "zigbee2mqtt", "tasmota"]
---

# 0.117.7 自动化升级

- ![AIS](/img/en/blog/202010/mechanical-arm.png) **自动化功能**
- ![AIS Kalendarze](/img/en/blog/202011/ais_calendar.png) AIS日历系统
- ![Zigbee](/img/en/blog/202007/zigbee.png) Zigbee2Mqtt 1.16.1
- ![Tasmota](/img/en/blog/202005/tasmota_small.png) Tasmota v9.1.0 Imogen
- ![Home Assistant](/img/en/blog/202007/hass.png) Home Assistant 0.117.6

<!--truncate-->

## 无忧升级指南

:::tip[备份须知]
### ![A](/img/en/blog/202009/alpha-a-circle.png) 配置备份

重要提示：升级前建议先执行[配置备份](/docs/ais_bramka_configuration_software#kopia-zapasowa-konfiguracji)。这能帮助您在升级前验证配置完整性，大幅降低升级风险。
:::

:::important[控制台与日志]
### ![B](/img/en/blog/202009/alpha-b-circle.png)网关控制台与日志

若遇升级问题，请参考[控制台手动升级指南](/docs/ais_bramka_update_manual)或[应用完全重置步骤](/docs/ais_bramka_reset_ais_step_by_step)。
特别提醒：安装非标准组件的用户需重点关注此步骤。
:::

:::caution[耐心等待]
### ![C](/img/en/blog/202009/alpha-c-circle.png) 首次启动耗时较长，请保持耐心

**升级后首次启动可能耗时长达20分钟**
此时系统正在更新集成库并将数据库迁移至新格式
**请耐心等待升级完成**
:::

## 注意！两阶段升级流程

本次升级将分两个阶段进行：

### 第一阶段：AIS HA组件与Android更新

a) 下载更新包
![](/img/en/blog/202011/update1.png)

b) 安装更新
![](/img/en/blog/202011/update2.png)

c) 重启设备
![](/img/en/blog/202011/update3.png)

网关重启后，AIS HA组件版本将升级至>0.117，此时才会显示第二阶段升级选项→Zigbee更新。

![](/img/en/blog/202011/update4.png)

### 第二阶段：Zigbee组件更新

此阶段非常快速，约1-2分钟（下载20MB并解压）后设备将自动重启并显示当前状态：

![](/img/en/blog/202011/update5.png)

## ![](/img/en/blog/202010/mechanical-arm.png) 通过事件实现自动化

此版本我们介绍了触发自动化的新方式，新增了三种自动化触发示例：

- 日历事件触发
- 移动应用扫描二维码触发  
- 网关连接控制器按钮触发

### 日历事件触发自动化

您可以将日历作为外部事件调度器/指令源，替代在自动化中硬编码的方式。

![AIS scan](/img/en/frontend/ais_calendars_10.png)

我们通过示例演示如何创建自动化，将日历传入事件作为指令执行：[日历事件触发自动化](/docs/ais_bramka_calendar_event_automation)

### 扫码触发自动化

通过手机摄像头扫描二维码并发送至网关来触发自动化，其原理类似于NFC标签：

![AIS scan](/img/en/bramka/ais_scan_tags.png)

详见文档：[扫码触发自动化](/docs/ais_bramka_tag_automation)

### 按钮触发自动化

在无显示器控制模式下，遥控器/键盘等网关连接控制器的按键事件会作为触发信号传递给家庭助理系统。具体实现参见示例：[按钮触发自动化](/docs/ais_bramka_key_event_automation)

![AIS button](/img/en/bramka/ais_remote_key_events.jpg)

## ![](/img/en/blog/202011/ais_calendar.png) AIS日历集成

我们新增了AIS日历集成功能。

当前系统通过官方Google Calendar API实现与Google日历的数据同步，支持家庭助理与Google日历间的事件交互。

:::caution[注意]
**该集成正在接受Google方面的审核**。我们已提交全部所需材料，但Google审核通过的时间尚未确定。
我们正与Google云信任与安全团队保持沟通，持续说明该集成的运行机制及用户价值。
:::

但这并不意味着AIS日历集成的未来尚不确定，可能会从家庭助理中消失。
日历作为触发自动化的方式，有望成为家庭助理中更简单的任务调度方法（如控制供暖等）。因此，如果我们未获得Google授权或集成无法正常运行，我们将在集成商门户中启用CalDAV日历。

**总结而言——AIS日历集成将始终存在于家庭助理系统中，并会随着每个版本迭代变得越来越易用和强大。**

![AIS scan](/img/en/frontend/ais_calendars_3.png)

## ![](/img/en/blog/202007/zigbee.png) Zigbee2Mqtt 1.16.1

包含错误修复、功能改进以及对新设备的支持。完整版本说明详见项目页面 [Zigbee2Mqtt](https://github.com/Koenkk/zigbee2mqtt/releases/tag/1.16.0)

![](/img/en/blog/202011/z2m.png)

## ![](/img/en/blog/202005/tasmota_small.png) Tasmota v9.1.0 Imogen

完整的变更列表、新特性与修复详见项目页面 [Tasmota](https://github.com/arendst/Tasmota/releases/tag/v9.1.0)

我们的编译版本发布于此 [AIS-Tasmota](https://github.com/sviete/AIS-Tasmota/tree/firmware)

我们正致力于简化搭载AIS Tasmota固件的新设备接入流程，使其如同固件升级一样便捷。
在集成商门户中可查看已关联至网关的、运行我们定制Tasmota固件的设备：

![Home Assistant](/img/en/blog/202011/iot.png)

具体实现细节将随应用程序和文档的后续更新逐步说明。
当前IoT设备添加流程保持不变。新的IoT设备接入流程目前如下图所示：

![流程图](https://www.websequencediagrams.com/cgi-bin/cdraw?lz=dGl0bGUgUHJ6ZXDFgnl3IGF1dG9yeXphY2ppIHByenkgZG9kYXdhbml1IG5vd2VnbyB1cnrEhWR6ZW5pYSBJT1QgZG8gYnJva2VyYSB3IEFJUwoKVXNlciAtPiBNb2I6IERvZGFqADcFAC8LZQpNb2IgLT4gSU9UOiBQYXJhbWV0cnkgcG_FgsSFYwBXBldpRmkgaSBNUVRUCklPVCAtPiBBSVM6IE1hbSB0YWtpZSBwADAJY3p5IGplc3QgT0s_CkFJUwBTCcWBxIVjeiBzacSZIHoARwUgegA5BW1pADYJYW1pCm5vdGUgcmlnaHQgb2YAgTQGQ3pla2FtIMW8ZWJ5IHphcHl0YcSHIEFJUwBpBUlPVABQBgCBLAh5xYJvAIFPCACBIwVDAA4YAIEZCQCCHAVUYWsAgW8Jb24AOglVc2VyOiBTdWtjZXMgbWFsegCCMhIK&s=default)

## ![](/img/en/blog/202007/hass.png) Home Assistant 0.117.6

最新稳定版Home Assistant 0.117.6如约而至，本次更新包含大量修复和新功能。
完整更新内容请查阅项目发布页：[Home Assistant 0.117.6](https://www.home-assistant.io/blog/2020/10/28/release-117/)

![Home Assistant](/img/en/blog/202011/ha_social.png)

----

欢迎升级并[参与论坛讨论 :)](https://ai-speaker.discourse.group/)

##### AI-Speaker 2020年9月