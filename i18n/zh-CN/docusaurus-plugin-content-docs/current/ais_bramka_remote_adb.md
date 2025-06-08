---
title: "Dostęp do konsoli bramki po ADB"
sidebar_label: ADB
---

Android调试桥(ADB)是另一个运行在控制台的实用工具，可实现与设备的通信。

:::tip[提示]
当无法通过SSH连接家庭助手时（例如因从网关卸载了该应用），这种通信方式尤为实用。
:::

## 在计算机上安装ADB

ADB是Android SDK的组成部分，三大操作系统(Windows/Mac/Linux)的安装指南详见：

https://developer.android.com/studio/releases/platform-tools.html

## 在网关上启用ADB调试

1. 将网关连接至电视或显示器

2. 退出家庭助手应用
[退出应用](/docs/ais_bramka_settings#ustawienia-aplikacji-asystent-domowy)

3. 进入Android设置
[Android系统设置](/docs/ais_bramka_settings#ustawienia-systemu-android)

4. 在Android设置中进入**关于设备**

![设置-关于设备](/img/en/bramka/adb_settings_1.png)

5. 连续点击**版本号**5次，直至出现"您已处于开发者模式"提示

![设置-版本号](/img/en/bramka/adb_settings_2.png)

6. 返回设置界面（使用遥控器返回键），选择新增的**开发者选项**

![设置-开发者选项](/img/en/bramka/adb_settings_3.png)

7. 在开发者选项中启用**USB调试**

![设置-USB调试](/img/en/bramka/adb_settings_4.png)

## 在局域网内连接网关

1. 在计算机终端启动ADB服务

```bash
$ adb start-server
```

2. 在计算机终端输入以下命令连接网关

```bash
$ adb connect <ip-bramki-w-lokalnej-sieci>
```

3. 在网关上授权来自计算机的连接请求

![设置-版本号](/img/en/bramka/adb_settings_5.png)

4. 在计算机终端输入以下命令连接网关控制台

```bash
$ adb shell
```

> 通过ADB连接后，您可执行网关应用安装、日志查看等维护操作

## 通过ADB执行的常用维护操作示例

### 切换至root用户

在终端执行以下命令连接网关：

```bash
adb connect <ip-bramki-w-lokalnej-sieci>
adb shell
```

执行后应显示如下状态：

```bash
p281:/ $
```

**$** 符号表示我们当前以普通用户身份登录设备控制台。要获取完整权限，需使用`su`命令切换至root用户，预期效果如下：

```bash
p281:/ $ su
p281:/ #
```

可通过`whoami`命令验证当前用户身份

```bash
p281:/ # whoami
p281:/ root
```

### 应用程序设置备份

家庭助手的所有设置均存储在`/data/data/pcom.termux/files/home/AIS`目录下。执行以下命令将其内容复制到`/sdcard`位置：

**cp -r /data/data/com.termux/files/home/AIS /sdcard/AIS**

```bash
p281:/ # cp -r /data/data/com.termux/files/home/AIS /sdcard/AIS
```

### 下载家庭助手OTA安卓服务器应用

应用程序可通过我们的OTA服务获取 https://www.ai-speaker.com/ota ，先在电脑浏览器地址栏输入完整应用地址下载：
https://www.ai-speaker.com/ota/android/AisPanelApp.apk 或访问 https://www.ai-speaker.com/ota/ 从表格中选择应用。

本示例将下载并安装设备上运行的服务器应用：

![OTA下载](/img/en/bramka/adb_download_apk_from_ota.png)

### 通过ADB安装安卓应用

当应用下载至电脑后，可通过**adb install**命令安装至设备，具体命令如下：

```bash
adb install -r -d AisPanelApp.apk
```

其中**-r**参数表示保留文件重新安装，**-d**参数允许降级安装。AisPanelApp.apk为下载的应用文件名，若执行命令时不在应用所在目录，需指定完整的文件路径。

### 通过ADB启动安卓应用

在设备上通过ADB启动应用只需输入命令：

```bash
adb shell am start -n pl.sviete.dom/pl.sviete.dom.WelcomeActivity
```