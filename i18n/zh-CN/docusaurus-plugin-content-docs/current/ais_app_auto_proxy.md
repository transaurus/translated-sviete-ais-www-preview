---
title: "AIS Auto Proxy"
sidebar_label: AIS Auto Proxy
---

## 简介

AIS Auto Proxy 是一项集成服务，允许局域网内的其他应用程序与家庭助手用户界面进行集成。其工作原理基于 [Ingress](https://kubernetes.io/docs/concepts/services-networking/ingress/) 机制，该机制广泛应用于容器化应用程序中。

AIS Auto Proxy 目前应用于 Zigbee2Mqtt 场景：

![zigbee](/img/en/bramka/app_zigbee2mqtt_proxy.png)

以及运行 AIS dom 固件的设备：

![RF 433](/img/en/iot/iot_ais_dom_device_config_0.png)

通过该服务，运行在不同IP地址或网关其他端口的应用程序可被嵌入家庭助手应用，并可通过加密隧道实现远程访问。

## 将本地应用程序添加至家庭助手

假设您有一个运行在局域网的应用程序，并希望通过家庭助手实现远程访问。例如某款运行在AIS dom固件设备上的Web应用程序。

![proxy1](/img/en/integrations/ais_proxy_1.png)

### 1. 验证应用程序是否支持iframe嵌入

添加"网页"类型卡片，确认当处于局域网时应用程序页面能否正常显示：
![AIS Proxy](/img/en/integrations/ais_proxy2.png)

此步骤可验证网关对该页面的可访问性，确保网关与其他应用程序在局域网内互通。

### 2. 添加长期访问令牌

长期访问令牌允许通过API与家庭助手进行交互，每个令牌自创建起有效期为10年。需通过用户个人资料页面添加令牌。

![AIS Proxy](/img/en/integrations/ais_proxy3.png)

### 3. 通过ais_proxy添加应用程序访问

其原理类似于iframe但通过代理实现，URL地址格式如下：

```
/api/ais_auto_proxy/<token>/<ip-twojej-aplikacji>/<port-twojej-aplikacji>/

```

在局域网内的显示效果与常规iframe相同：

![AIS Proxy](/img/en/integrations/ais_proxy4.png)

关键改进在于实现了应用程序的远程访问能力（通过[加密隧道](ais_bramka_remote_www_index)连接时）：

![AIS Proxy](/img/en/integrations/ais_proxy5.png)