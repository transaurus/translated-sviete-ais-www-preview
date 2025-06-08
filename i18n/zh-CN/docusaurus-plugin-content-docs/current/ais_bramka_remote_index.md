---
title: "Dostęp do bramki w lokalnej sieci"
sidebar_label: Wprowadzenie
---

在局域网中，您可以通过常用工具（http(s)、ftp、ssh）连接网关。这样即可在网页浏览器中使用网关应用程序，并将网关作为远程服务器进行控制。

:::important[重要信息]
 连接网关的关键在于确认**网关是通过.local后缀的本地主机名可见，还是仅通过IP地址可见？** 网关的本地主机名出厂设置为**ais-dom**。网关会以该主机名(**ais-dom**)在局域网中广播自身。随后网关通过多播DNS机制（Zeroconf/Avahi/Bonjour）在局域网中发布服务（HTTP、FTP、SSH、MQTT）。这是所谓的零配置服务——无需任何配置即可实现局域网设备间的连接。
:::

苹果公司的系统原生通过Bonjour服务支持mDNS，Linux系统则由Avahi提供支持（所有主流发行版均默认安装）。若要在Windows获得相同功能，需安装[Windows版Bonjour](https://support.apple.com/kb/dl999?locale=pl_PL)。

>**本文档所有示例均假设网关可通过主机名ais-dom.local访问。若您的局域网环境不同，请将示例中的ais-dom.local替换为本地IP地址进行连接**。

## 在应用程序中查看IP地址

在"家庭助理"应用中，选择菜单项**配置**→**AIS dom网关配置**。在**WiFi网络**章节可查看本地IP地址。

![网络设置](/img/en/bramka/ais_bramka_ip_address.png)

您也可通过菜单选择[实用链接](/docs/ais_bramka_services)查看网络服务地址。

## 向助手查询IP地址

您还可以通过语音指令查询系统各组件的状态，例如说出：

```text
Jaki jest adres IP
```

或

```text
Jaka jest lokalna nazwa hosta
```