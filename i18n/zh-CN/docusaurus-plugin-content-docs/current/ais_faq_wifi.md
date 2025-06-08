---
title: "Ustawienia połączenia WiFi"
sidebar_label: Ustawienia WiFi
---

## 通过网页应用配置WiFi

WiFi连接定义可在设备首次启动时的初始简易配置过程中通过网页应用进行设置。

[设备首次运行时的WiFi配置](/docs/ais_bramka_first_run)

您也可以随时在家庭助理配置中添加WiFi设置。
登录应用后，请按以下步骤操作：

### 进入**配置**

![WiFi配置](/img/en/bramka/go_to_config.png)

### 选择**集成**

![WiFi配置](/img/en/bramka/go_to_integrations.png)

### 在集成中选择**AIS WiFi连接配置**

![WiFi配置](/img/en/bramka/go_to_integration_wifi.png)

### WiFi连接向导

请按照添加WiFi连接的向导步骤逐步操作。

![WiFi配置](/img/en/bramka/start_wifi_integration_wizard.png)

## 通过遥控器配置WiFi

也可以通过遥控器配置WiFi连接。
该选项在没有显示器或HDMI输出电视的情况下非常实用，同时也适用于存在视力障碍的用户。

遥控器菜单中进入**设置** -> **网络设置** -> **扫描可用WiFi网络**即可找到WiFi配置选项。

## 在Android系统中配置WiFi

还可以通过Android系统层面配置WiFi连接。需先退出**家庭助理**应用，然后启动Android系统设置。具体操作步骤详见文档[进入Android设置](/docs/ais_bramka_settings)

## 在Linux控制台中设置WiFi

在控制台中，可通过以下命令查看WiFi设置

```bash
su -c 'cat /data/misc/wifi/wpa_supplicant.conf'
```

![控制台中的WiFi设置](/img/en/bramka/wifi_settings_in_console.png)