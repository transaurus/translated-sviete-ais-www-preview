---
title: "Broker MQTT"
sidebar_label: Broker MQTT
---

## 简介

我们在网关上内置了MQTT代理服务，开箱即用，设备启动后即可自动运行。

MQTT（MQ遥测传输协议）是一种机器对机器通信协议，属于物联网TCP/IP协议的补充。它采用极轻量级的发布/订阅消息传输模式。搭载我们软件的设备通过MQTT协议与本地网络中的网关通信，因此无需用户配置即可被网关自动识别。

![WEB控制台](/img/en/bramka/mqtt_broker.png)

## 从家庭助理系统连接MQTT代理

运行在网关上的家庭助理（服务端）应用默认会连接同网关上的MQTT代理服务。在配置器中指定代理服务器/网关的本地IP地址即可完成MQTT集成：

![添加服务](/img/en/bramka/mqtt_integration_1.png)

![添加服务](/img/en/bramka/mqtt_integration_2.png)

高级用户可根据需要将家庭助理应用连接至其他MQTT代理服务器。

-----------------------------------------------------

## 技术信息

### MQTT进程

网关进程由[PM2进程管理器](http://pm2.keymetrics.io/)控制。PM2负责在系统启动时运行MQTT代理服务，并持续监控其运行状态。

查看MQTT进程状态需在控制台输入：

```
pm2 show mqtt
```

![MQTT代理](/img/en/bramka/pm2_mqtt.png)

### MQTT代理配置

:::caution[注意]
**注意！** 基础配置采用默认设置即可，无需修改。仅当开发者或高级用户需要添加桥接、认证等功能时才需调整MQTT代理配置。若配置更改后出现问题，建议[执行应用完全重置](/docs/ais_bramka_reset_ais_step_by_step)
:::

网关搭载的MQTT代理服务采用[mosquitto](https://mosquitto.org/)，其配置文件位于标准路径：
``/data/data/com.termux/files/usr/etc/mosquitto/mosquitto.conf``

![MQTT](/img/en/integrations/mqtt_edit_mosquito_config.png)

可通过应用直接编辑MQTT代理配置文件。在MQTT集成配置界面右上角选择**编辑mosquitto.conf**选项即可。

![Integracja SUPLA](/img/en/frontend/integration_supla_6.png)

通过这种方式，我们可以轻松添加与其他MQTT代理的桥接连接。

### 标准设置

设备出厂时，网关内置的MQTT代理默认配置如下：

``` text
# AIS Config file for mosquitto on gate
listener 1883 0.0.0.0
allow_anonymous true

```

添加SUPLA MQTT集成后，设置会自动更改为：

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
bridge_cafile /data/data/pl.sviete.dom/files/usr/etc/tls/cert.pem

```

### 仅限本地访问

MQTT代理允许无认证访问。因此网关上的MQTT代理仅限局域网内访问。