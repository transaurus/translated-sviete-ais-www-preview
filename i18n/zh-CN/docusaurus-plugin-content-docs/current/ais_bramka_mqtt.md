---
title: "Broker MQTT działający na bramce"
sidebar_label: MQTT
---

家庭助理系统内置了MQTT代理服务器。我们选用当前最流行的[Mosquitto](https://mosquitto.org/)作为代理，该服务在网关上由进程管理器[PM2](http://pm2.keymetrics.io/)监管运行。Mosquitto支持所有版本的MQTT协议（经OASIS标准化并由ISO批准），包括最新版本。[MQTT协议](https://pl.wikipedia.org/wiki/MQTT)特别适用于机器对机器通信、物联网(IoT)、移动设备等需要节省带宽和能耗的场景，因此被选作设备与物联网网关通信的核心协议。

## MQTT代理地址

MQTT代理运行在标准端口1883（由[IANA](https://www.iana.org/)保留）。由于在局域网内运行，我们不对设备进行强制认证。

## 家庭助理系统中的MQTT设备发现

网关启动时会向MQTT代理中注册的**dom**组设备发布指令dom/cmnd/**SetOption19** 1，表示要求设备被家庭助理系统自动发现。

随后设备添加流程按以下三个步骤完成。

![MQTT通信流程](/img/en/bramka/gate_mqtt_1.png)

### 发送配置信息

设备向MQTT代理发布主题为**homeassistant/#**的消息，消息内容包含设备配置描述

```json
{  
   "name":"Gniazdo",
   "command_topic":"cmnd/dom_4BA155/POWER",
   "state_topic":"stat/dom_4BA155/RESULT",
   "payload_off":"OFF",
   "payload_on":"ON"
}
```

![MQTT通信流程](/img/en/bramka/gate_mqtt_2.png)

### 接收配置信息

家庭助理系统订阅**homeassistant/#**主题，从MQTT代理接收设备发送的配置消息

![MQTT通信流程](/img/en/bramka/gate_mqtt_3.png)

### 将设备添加至家庭助理系统

家庭助理系统在收到配置消息后，会将设备添加至应用面板

![MQTT通信流程](/img/en/bramka/gate_mqtt_4.png)

## 网关与设备通信

网关与设备的通信通过向特定主题发送消息实现，这些主题由设备和网关共同订阅。

![MQTT通信流程](/img/en/bramka/gate_mqtt_5.png)

### 设备订阅主题

设备订阅以下3个主题：

```yaml
  cmnd/dom_%06X/#
  cmnd/DOM_%06X/#
  cmnd/dom/#
```

![MQTT通信流程](/img/en/bramka/gate_mqtt_7.png)

### 家庭助手订阅的主题

家庭助手系统订阅主题 **stat/dom_%06X/+**

![MQTT通信](/img/en/bramka/gate_mqtt_8.png)

## 家庭助手与设备的通信

与设备的通信遵循以下流程：

![MQTT通信](/img/en/bramka/gate_mqtt_9.png)

### 从网关向设备发布命令

![MQTT通信](/img/en/bramka/gate_mqtt_10.png)

### 设备接收命令

![MQTT通信](/img/en/bramka/gate_mqtt_11.png)

### 执行确认

设备执行命令后会发布状态消息。

![MQTT通信](/img/en/bramka/gate_mqtt_12.png)

### 家庭助手系统中设备状态的变更

系统接收到设备的状态消息后立即更新其状态，并在应用程序中实时反映：

![MQTT通信](/img/en/bramka/gate_mqtt_13.png)