---
title: "AIS SUPLA MQTT"
sidebar_label: AIS SUPLA MQTT
---

## 简介

[SUPLA](https://www.supla.org/pl/) 是波兰流行的家庭自动化系统。SUPLA拥有自研协议栈、基于ESP8266的专用设备固件，以及主要由[Zamel](https://zamel.com/pl-PL/)公司生产的硬件设备。[SUPLA软件是开源的](https://github.com/SUPLA)。

## 集成方案

通过SUPLA MQTT桥接器集成，可在AIS家庭网关运行的MQTT代理与SUPLA的MQTT代理之间建立连接。这使得SUPLA设备能自动接入家庭助理系统，并支持通过AIS进行语音控制。

## 添加集成

集成需登录SUPLA云平台以获取MQTT连接凭证。

请启动集成配置向导

![Integracja SUPLA](/img/en/frontend/integration_supla_1.png)

该向导将引导您逐步完成配置流程

![Integracja SUPLA](/img/en/frontend/integration_supla_2.png)

## SUPLA集成演示

完成集成后，可像其他设备一样通过语音控制SUPLA设备并用于自动化场景。在家庭助理系统中，所有设备类型（如灯泡、开关、吸尘器）均采用统一API，与设备制造商无关。

![Integracja SUPLA](/img/en/frontend/integration_supla_4.png)

## 技术说明与限制

:::caution[注意]
**当前集成方案处于开发测试阶段**

本集成仅支持SUPLA在其MQTT代理中开放的设备。

添加或移除SUPLA MQTT集成时，网关上的MQTT代理配置会被覆盖，服务将自动重启以应用连接配置变更。

当前版本仅支持连接单个SUPLA云服务器。
:::

:::tip[提示]
**支持手动配置MQTT桥接**

若您自行配置AIS家庭网关的MQTT代理且采用非标准配置，可不通过AIS配置向导，手动建立网关MQTT代理与SUPLA代理之间的桥接连接。
:::

可通过以下应用界面访问网关MQTT代理配置：

![Integracja SUPLA](/img/en/frontend/integration_supla_5.png)

![Integracja SUPLA](/img/en/frontend/integration_supla_6.png)

配置变更后需重启网关MQTT代理服务，可通过应用界面操作：

![SUPLA集成](/img/en/frontend/integration_supla_7.png)

或通过控制台命令：

```
pm2 restart mqtt
```

![SUPLA集成](/img/en/frontend/integration_supla_8.png)

若MQTT桥接出现故障，可通过以下命令查看日志：

```
pm2 logs mqtt
```

网关MQTT代理的手动配置说明详见：[MQTT代理配置](/docs/ais_app_integration_mqtt#konfiguracja-brokera-mqtt)

SUPLA MQTT配置器设置的参数：

``` text
# AIS Config file for mosquitto on gate
listener 1883 0.0.0.0
allow_anonymous true

# SUPLA MQTT bridge connection
connection bridge-dom-unikalny-identyfilator-bramki*
address host-i-port-od-supla*
topic supla/# in
topic homeassistant/# in
topic supla/+/devices/+/channels/+/execute_action out
topic supla/+/devices/+/channels/+/set/+ out
remote_username nazwa-użytkownika-z-supla*
remote_password hasło-z-supla*
bridge_cafile /data/data/com.termux/files/usr/etc/tls/cert.pem

```