---
author: Jola AI-Speaker
authorURL: https://github.com/sviete
authorImageURL: https://avatars3.githubusercontent.com/u/43966761?s=460&v=4
title: Wersja systemu 0.105.7 Dyski zdalne i wymienne
---

##  0.105.7 远程磁盘与可移动磁盘

![磁盘](/img/en/frontend/drives_all.png)

<!--truncate-->

:::tip[提示]
注意：更新前建议先执行[配置备份](/docs/ais_bramka_configuration_software#kopia-zapasowa-konfiguracji)。通过预先验证配置完整性，可显著降低升级故障风险。
:::

本次更新重构了软件包依赖关系（以解决重复安装依赖包的问题）。**升级过程可能持续40分钟** - 请耐心等待完成。系统将通过语音播报升级进度，您也可通过SSH连接网关并使用**pm2 logs**命令查看详细日志。

:::important[重要通知]
若升级后出现问题，请参考[控制台升级指南](/docs/ais_bramka_update_manual)或[应用完全重置教程](/docs/ais_bramka_reset_ais_step_by_step) - 特别是对于安装了非标准组件的用户。
:::

## 远程磁盘与可移动磁盘

本版本对可移动磁盘和远程磁盘功能进行了重大优化：
可移动磁盘指通过SD卡或USB接口连接的存储设备
远程磁盘指云存储服务或网络存储设备

![磁盘](/img/en/frontend/drives_all.png)

本版本起，这两类磁盘将自动挂载至用户目录的子文件夹：

- 可移动磁盘
- 远程磁盘

``` bash
$ cd ~/dom
ls
dysk-wewnętrzny  dyski-wymienne  dyski-zdalne  dyski-zewnętrzne
```

核心改进：

- 外置磁盘与远程磁盘现以可写权限挂载——这意味着您不仅能够浏览和播放远程/外置磁盘中的内容，还能将网关数据写入这些磁盘。了解此功能价值的用户（如需要存储摄像头拍摄的照片或视频）现在即可使用该功能。对Linux目录结构和命令行操作不熟悉的用户，建议等待相关功能在文档中得到详细说明并集成至应用程序后再使用。
- 我们采用[libfuse](https://pl.wikipedia.org/wiki/FUSE)和[rclone](https://rclone.org/)挂载远程磁盘，此举简化了代码结构并提升了远程磁盘内容浏览与播放速度。
- 已将rclone配置文件从~/dom/rclone.conf迁移至隐藏目录~/AIS/.dom/rclone.conf。这使得远程磁盘配置可随~/AIS目录的备份一同保存。
- "disks-zewnętrzne"目录是早期只读挂载USB/SD卡方案的遗留项。我们将保留该目录两个月（期间请将自动化脚本和服务中的路径从"disks-zewnętrzne"更新为"disks-wymienne"）。

:::caution[注意]
若需在网关上删除/修改/添加远程或外置磁盘内容，建议使用无重要数据的磁盘（新建Google Drive或Mega账户挂载很便捷）。此举可避免自动化脚本或命令错误导致数据丢失。
:::

## 坚不可摧的网关

我们已启动"坚不可摧的网关"项目。

注意到部分用户为集成新设备，会随意从网络复制代码至网关。随后却因系统更新失败/功能异常向我们问责。论坛数据显示，许多用户并不关心非标准组件的运行机制。我们也统计了测试版系统安装非标准组件引发问题的比例。

:::caution[警告]
再次郑重提醒：安装非标准组件需自行承担风险。这些组件未被Home Assistant官方收录有其原因。**这如同安装未知来源的应用——可能运行正常，也可能植入破坏系统的病毒**。
:::

### 安装非标准组件可能引发的后果：

- 影响系统稳定性。这些代码可能编写不当，存在循环操作导致设备卡死/重启。我们以某个自定义集成为例说明——该集成每小时能记录100万条（没错，一百万！）日志 https://ai-speaker.discourse.group/t/dlaczego-niestandardowe-komponenty-nie-sa-bezpieczne/288 令人震惊的是，这个组件被广泛使用。
- 影响自动更新。无人测试过这些代码及其依赖项（它们可能安装额外软件包）。这些组件可能安装非官方测试支持的软件版本，最终会阻塞官方更新。
- 法律风险。自定义组件可能未经制造商授权使用其API。请务必谨慎操作，**您需自行承担网关安装和使用所有非官方组件产生的责任**。

:::important[重要通知]
在DEV阶段我们不会阻止用户在网关上安装任意代码。但由于最终责任往往转嫁给我们，我们将采取措施增强设备对此类操作的防御能力。
:::

### "坚不可摧网关"项目计划：

1. 随当前0.105.7版本将数据库和日志迁移至设备存储
2. 在0.105.7版本引入安全模式。这是Home Assistant的新模式，当用户配置出现问题时仍可启动网页界面（此前配置错误会导致系统无法启动，必须通过控制台查看日志）
3. 0.106版本将更新网关服务。停用webview活动（带麦克风和应用框架的界面），仅保留Home Assistant作为后台服务。我们的网关默认运行"无显示器控制模式"——不启动带应用框架的界面。该框架本质是Chrome浏览器，会占用大量CPU和内存资源。此举将提升Home Assistant运行速度和稳定性
4. 后续版本将提供双启动机制。用户可通过SD卡（类似树莓派）或USB启动系统，运行纯净Linux系统+Docker+Home Assistant来验证稳定性

## 应用程序界面优化

我们的设计师朋友仔细审查了应用程序，并为我们提供了一些改进建议。
效果体现在优化后的网页应用界面上（首页背景和徽标设计）。
具体实现方法我们已在博客中详细说明，方便用户自定义视图和卡片样式：

- [视图背景定制](https://ai-speaker.discourse.group/t/wlasne-ladne-tlo-dla-widoku-w-aplikacji/265)
- [卡片样式设计](https://ai-speaker.discourse.group/t/stylizacja-karty-w-aplikacji/273)

我们还对移动应用的视觉呈现进行了多项优化。

![平板界面](/img/en/blog/202002/tablet.png)

## 新版二进制包

以下组件已更新至新版本：

- libmosquitto 1.6.8 arm [可升级自: 1.6.7-1]
- libwebsockets 3.2.99.3 arm [可升级自: 3.2.99.1-1]
- mosquitto 1.6.8 arm [可升级自: 1.6.7-1]
- rclone 1.51.0 arm [可升级自: 1.49.5]
- ttyd 1.6.0 arm [可升级自: 1.5.2-2]
- 新增libfuse二进制包

网页应用中控制台的响应速度应有显著提升。

## Home Assistant

最新稳定版Home Assistant <a href="https://www.home-assistant.io/blog/2020/02/05/release-105/" target="_blank">0.105.5</a>

新版区域编辑器获得了我们团队的高度认可。

![区域编辑器界面](/img/en/bramka/presence_detection_13.png)

----

欢迎升级体验并[参与论坛讨论 :)](https://ai-speaker.discourse.group/)
AI-Speaker 2020年2月
----