---
title: "Pełny reset aplikacji"
sidebar_label: Wykonanie pełnego resetu aplikacji
---

## 执行应用程序完全重置

应用程序完全重置是指删除网关上**家庭助理**应用的所有设置和代码，并用默认的最新代码和设置覆盖它们。
**应用程序完全重置是解决设备问题的安全简便方法**

:::tip[提示]
如果您正在尝试修改系统设置、创建自定义集成、更改网关代码、覆盖配置时遇到问题，
此处描述的**应用程序完全重置**是推荐的安全解决方案。
:::

若您未定义过自定义集成和配置，此方法可能是快速更新系统的最便捷途径。

从用户角度而言，该操作非常简单：只需进入网关上的`家庭助理服务`设置，选择应用菜单中的选项（如下方视频所示）。
整个过程快速高效，重启约耗时4分钟（需10 Mbps网络带宽）。
由于无需像常规更新那样分析、下载和更新所有系统安装包，因此速度显著提升。

![家庭助理服务设置](/img/en/bramka/settings_ais_service.png)

![家庭助理服务设置](/img/en/bramka/settings_ais_service_app_reset.png)

:::caution[注意]
**注意！** 此类重置/更新后将获得一个全新的家庭助理系统（含默认设置），部分设备可能需要重新与网关集成。

若您事先备份过有效配置，重置后可通过[配置备份](/docs/ais_bramka_configuration_software#kopia-zapasowa-konfiguracji)功能恢复。
:::

## 家庭助理重置为默认设置时的内部过程

技术层面该流程包含两个步骤：

1. 清除所有当前用户代码和配置
2. 下载包含家庭助理最新代码和配置的启动包

第一步与清除Android应用数据无异。因此除了通过家庭助理设置启动重置外，您也可以直接清除应用数据，重启后系统将自动安装最新代码。

![第一步](/img/en/bramka/settings_ais_service_app_reset_1.jpeg)

## 完整重置操作视频演示

<iframe width="560" height="315"  src="https://www.youtube.com/embed/3FO9hBl1V90" frameBorder="0" allowFullScreen></iframe>