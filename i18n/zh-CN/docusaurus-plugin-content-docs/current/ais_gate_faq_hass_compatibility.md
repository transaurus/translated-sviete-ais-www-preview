---
title: "Kompatybilność z Home Assistant"
sidebar_label: Kompatybilność z Home Assistant
---

## Home Assistant++

家庭助理系统（Home Assistant）是该平台的核心组件之一。我们在此基础上开发了大量定制代码、服务和配置，使您能够直接通过语音指令和射频遥控器操控设备。

**我们会定期获取Home Assistant的最新稳定版本，在设备上进行测试，并通过语音助手通知您可用的更新。您只需一键点击即可下载安装（也可启用自动更新功能），确保始终获得最新功能和安全补丁，保障系统运行的稳定性和安全性。**

## 家庭助理系统发布计划

![发布日历](/img/en/faq/release_calendar.png)

我们的家庭助理系统发布计划与Home Assistant的发布周期同步。当Home Assistant发布新版本时，我们会将其代码与我们的定制代码合并（merge）并发布到beta测试通道。经过数周设备测试和代码优化后，稳定版本才会正式发布。在此期间Home Assistant又会推出新版，我们再次将其合并至beta通道，如此循环。

如图所示，这种发布策略使我们始终比Home Assistant官方版本"滞后一个版本"。这是有意为之的设计——我们的目标是打造一个无需热修复的、高度稳定的生产环境版本。

若您希望更快体验新功能，且不介意可能出现的偶发错误，可随时切换至beta通道获取最新的Home Assistant版本。