---
title: "Dostęp do bramki z Internetu"
sidebar_label: Wprowadzenie
---

您可以通过互联网配置对本地网关的远程访问。这样您不仅能在本地网络中，还能在任何有互联网连接的地方（包括语音控制）操作家庭自动化系统。

最简单的远程访问方式是使用内置的加密隧道服务。

这是**我们目前向所有网关用户免费提供的服务：<span class="mdi mdi-dev-to"></span> <span class="mdi mdi-professional-hexagon"></span>**

![远程访问二维码](/img/en/bramka/http_remote_access_qr.png)

## 优势

该解决方案的优势：

- 无需配置路由器
- 不修改DNS设置和防火墙规则  
- 无需公网IP地址

## 工作原理

每个设备都有唯一的随机生成标识符（首次启动时生成且终身不变）。启用远程访问后，我们会在您的设备与Cloudflare网络之间建立[Cloudflare隧道](https://www.cloudflare.com/products/tunnel/)。我们的paczka.pro服务器会基于设备标识符生成唯一公开访问URL。所有通过该网关标识符的请求都将由Cloudflare转发至本地运行的网关服务器。

## 安全措施

:::caution[重要提示]
为增强安全性，启用远程访问时将自动禁用简易登录功能（无需输入密码选择用户）。

强烈建议启用多因素认证模块。详见Home Assistant文档[多因素认证](https://www.home-assistant.io/docs/authentication/multi-factor-auth/)
:::

## 启用远程访问

启用隧道功能需在应用中进行以下操作：左菜单选择**配置**→首选项**AIS dom网关设置**→进入远程访问设置页面。

![网关配置](/img/en/bramka/http_remote_access_step_1.png)

选择**远程访问**选项并启用加密隧道

![远程访问](/img/en/bramka/http_remote_access_step_3.png)

![远程访问](/img/en/bramka/http_remote_access_step_4.png)

## 唯一访问地址

启用远程访问后，您的网关将通过以下唯一地址提供服务：

https://您的网关标识符.paczka.pro

该地址较为复杂，但您无需手动输入——直接用手机扫描二维码即可。

## <span class="mdi mdi-professional-hexagon"></span> PRO版网关

PRO版网关还可提供WireGuard®订阅服务——这是一种采用尖端加密技术的快速现代VPN网络：https://www.wireguard.com/

更多服务详情及条款请参阅[远程服务政策](/docs/ais_dom_cloud_services_terms)