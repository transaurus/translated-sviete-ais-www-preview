---
title: "Konfiguracja wybranego pulpitu"
sidebar_label: Konfiguracja pulpitu
---

## 启用配置模式

要启用选定主屏幕的配置，需在应用界面右上角选择**"用户界面配置"**选项。

![用户界面配置](/img/en/frontend/lovelace-ui-conf1.png)

### 添加新视图

您可以自行创建和修改视图（应用中的标签页），例如添加**"客厅"**、**"浴室"**、**"卧室"**等视图，并在其中通过[卡片](/docs/ais_app_cards)放置对应房间的设备。

![用户界面配置](/img/en/frontend/lovelace-ui-conf2.png)

## 技术信息

更多技术细节及界面演示可访问Home Assistant平台项目页面[Lovelace UI](https://www.home-assistant.io/lovelace/) https://www.home-assistant.io/lovelace/

### 用户界面配置备份

在用户界面配置模式下，可选择每页右上角的**"手动配置编辑器"**选项。

![用户界面配置备份](/img/en/frontend/lovelace-ui-conf-raw.png)

这将显示配置的文本版本

![用户界面配置备份](/img/en/frontend/lovelace-ui-conf-raw-save.png)

可将文本版本保存为备份文件进行实验性修改。若出现异常，始终可通过在此处粘贴原始配置文本来恢复。

### 重置主屏幕

若主屏幕配置出现异常，可在"手动配置"模式下删除整个主屏幕定义后保存更改以完全重置。

![用户界面重置](/img/en/frontend/lovelace_reset_dashboard.png)