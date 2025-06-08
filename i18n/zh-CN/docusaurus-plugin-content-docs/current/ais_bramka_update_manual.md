---
title: "Aktualizacja z konsoli"
sidebar_label: Aktualizacja z konsoli
---

## 简介

该系统为开源系统，支持超过2480个组件。其中许多组件可被自动识别并自动安装相关依赖包。

以下流程对于希望观察更新过程进展的用户，以及遇到应用内更新问题的用户可能有所帮助。

![更新](/img/en/bramka/update_from_console.png)

通过控制台进行更新并不困难，其步骤与自动更新完全相同。具体步骤如下：

1. 更新Linux系统环境
2. 更新zigbee2mqtt应用
3. 更新自动化平台
4. 更新Android应用

## 更新脚本

### 登录控制台

运行脚本的方式与执行控制台命令相同。可通过[SSH远程访问](/docs/ais_bramka_remote_ssh)从局域网内其他客户端登录网关控制台，或直接通过"智能家居助手"网页应用的开发者工具登录。

:::tip
建议使用原生SSH客户端登录网关执行控制台更新脚本，这样可以确保在浏览器控制台操作时不会意外断开连接。
:::

![更新](/img/en/bramka/ais_console.png)

## 在控制台中运行更新脚本

更新命令取决于当前所处的更新频道。网关的更新频道可在[集成商门户](/docs/ais_dom_cloud_login)中选择。

### PROD更新频道的软件

对于**PROD**(稳定版)频道，需在控制台执行以下命令：

```bash
curl -L https://raw.githubusercontent.com/sviete/AIS-utils/master/releases/prod.sh -o prod.sh
chmod +x prod.sh
./prod.sh
```

### BETA更新频道的软件

对于**BETA**频道，需在控制台执行以下命令：

```bash
curl -L https://raw.githubusercontent.com/sviete/AIS-utils/master/releases/beta.sh -o beta.sh
chmod +x beta.sh
./beta.sh
```

### ALFA更新频道的软件

对于**ALFA**频道，需在控制台执行以下命令：

```bash
curl -L https://raw.githubusercontent.com/sviete/AIS-utils/master/releases/alfa.sh -o alfa.sh
chmod +x alfa.sh
./alfa.sh
```

### 系统组件更新脚本

更新脚本代码存放于github仓库，地址如下：

- PROD -> https://raw.githubusercontent.com/sviete/AIS-utils/master/releases/prod.sh
- BETA -> https://raw.githubusercontent.com/sviete/AIS-utils/master/releases/beta.sh
- ALFA -> https://raw.githubusercontent.com/sviete/AIS-utils/master/releases/alfa.sh

```bash
#!/data/data/com.termux/files/usr/bin/bash
# AIS
# Homepage: https://ai-speaker.com
################################################
# Install ais-dom on PROD chanel
# run it by executiong in AIS dom console:
# curl -L https://raw.githubusercontent.com/sviete/AIS-utils/master/releases/prod.sh -o prod.sh
# chmod +x prod.sh
# ./prod.sh
#
# ...

```

## 版本不兼容问题

:::caution[注意]
对于未保持实时更新的网关设备，可能会出现版本不兼容问题导致更新中断。
:::

由于系统架构复杂且迭代迅速，在更新过程中可能存在无法直接升级所有组件的特殊情况。我们无法对所有历史版本到最新版本的升级路径进行全面测试。为避免升级过程中或系统重启时出现故障，我们将禁止直接从过旧版本升级至最新版本。

![Aktualizacja](/img/en/bramka/update_from_console_to_old.png)

当您在屏幕上看到或通过扬声器听到上述提示时，请执行"应用程序完全重置"操作。具体流程详见文档[应用程序完全重置](/docs/ais_bramka_reset_ais_step_by_step)，该文档包含完整重置过程的演示视频。