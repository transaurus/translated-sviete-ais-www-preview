---
title: "Przywracanie ustawień fabrycznych urządzenia"
sidebar_label: Wprowadzenie
---

该设备运行于特别定制的Android系统版本（自定义构建）。此Android版本预装了**"家庭助手"**系统及所有配套应用程序。

恢复出厂设置是通过删除设备上存储的所有信息将系统还原至初始/出厂状态。此操作将彻底清除设备购买后安装的所有数据、设置和应用程序。

:::danger[警告]
**除非AIS技术支持要求，否则切勿执行此操作**

执行恢复出厂设置将改变网关唯一标识符 -> [Secure Android ID](https://developer.android.com/reference/android/provider/Settings.Secure#ANDROID_ID)

在DEV3设备上执行恢复出厂设置可能导致root账户访问权限丢失 -> [论坛说明](https://ai-speaker.discourse.group/t/dev3-dostep-do-konta-root-po-wykonaniu-factory-reset/2066)
:::

:::caution[注意]
恢复设备至出厂设置的目的是解决无法通过其他方式处理的严重设备问题。
:::

> 系统正处于密集开发阶段（平均每3周发布新版本），因此出厂版本可能与当前版本存在差异——**首次启动和重新安装所有组件所需时间可能远超平常**，且可能需要额外操作步骤。

:::tip[提示]
若您正在调试系统设置、创建自定义集成、修改网关代码或覆盖配置时遇到异常，建议采用[执行应用程序完全重置](/docs/ais_bramka_reset_ais_step_by_step)方案。该操作通过删除网关所有家庭助手应用设置及代码，并替换为**默认最新代码和设置**，是解决系统问题的安全推荐方案。
:::

### 恢复出厂设置需在AI-Speaker技术支持下进行

:::danger[警告]
设备恢复出厂设置是将系统版本回退至...出厂状态（设备购买时的系统版本）。

如需获取《设备恢复出厂设置操作指南》，请邮件联系：[info@ai-speaker.com](mailto:info@ai-speaker.com)
:::