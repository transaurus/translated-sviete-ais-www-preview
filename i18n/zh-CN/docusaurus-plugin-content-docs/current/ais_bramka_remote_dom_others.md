---
title: "Inne metody na dostęp zdalny"
sidebar_label: Inne metody na dostęp zdalny
---

:::caution[警告]
当为您的网关添加互联网访问权限时，**请务必注意安全性**。需正确配置家庭助理的登录认证以保障访问安全，具体方法参见：[应用程序访问安全设置](#zabezpieczenie-dostępu-do-aplikacji)。
:::

## 路由器端口转发

通过路由器端口转发是将网关暴露到互联网的方法之一。对于应用程序而言，需要将网关的8123端口转发至路由器的空闲端口。由于路由器本身可通过互联网访问，因此调用其公网地址及映射端口即可访问家庭助理应用。具体操作步骤因路由器型号而异，请参考对应设备的说明书进行配置。

## TOR网络

可通过Tor Onion网络定义对网关的互联网访问。
Tor Onion服务允许通过标准端口远程访问运行在您本地网络中的家庭助理应用。

通过Tor访问设备是最安全的方式，因其提供强加密且网关不会暴露在常规互联网中。但此方法效率较低，因Tor网络通常延迟较高。

### 安装必要组件

在控制台执行以下命令安装TOR：

```bash
$ apt install tor
```

### Onion服务配置

需修改TOR默认配置文件$PREFIX/etc/tor/torrc
执行此命令以在网关上启用SSH和HTTP的Onion服务：

```bash
$ echo "SOCKSPort 127.0.0.1:9050
HiddenServiceDir /data/data/com.termux/files/home/.tor/hidden_dom
HiddenServicePort 22 127.0.0.1:8022
HiddenServicePort 80 127.0.0.1:8180" > $PREFIX/etc/tor/torrc
```

随后创建用于存储隐藏服务信息的目录：

```bash
$ mkdir -p ~/.tor/hidden_dom
```

在控制台输入以下命令启动Tor服务：

```bash
$ tor
```

等待服务启动完成，当出现以下日志时表示启动成功：

```bash
 Bootstrapped 100%: Done
```

使用Ctrl+c组合键关闭服务

### Onion主机名

在控制台执行以下命令查看网关的Onion网络唯一主机名：

```bash
$ cat ~/.tor/hidden_dom/hostname
```

输出结果应类似如下格式：

```bash
$ ytdv3tvdeh8u6koz.onion
```

### 服务连接

> 请注意：`TOR`服务需在客户端/服务器两端同时运行，否则会出现连接错误。

- SSH。
连接SSH服务可以使用torsocks程序

在控制台执行以下命令安装torsocks：

```bash
$ apt install torsocks
```

要通过TOR网络连接到网关控制台，请在客户端控制台输入命令：

```bash
$ torsocks ssh ytdv3tvdeh8u6koz.onion -i id_rsa_ais
```

- HTTP。
使用支持Tor Onion网络的专用浏览器连接应用，可从以下地址下载：https://www.torproject.org/projects/torbrowser.html.en
在浏览器地址栏输入您在Onion网络中的唯一主机名

### 将tor服务添加到进程管理器

要使TOR在每次网关重启后自动运行，请在控制台执行以下命令将其添加到PM2进程管理器：

```bash
$ pm2 start tor --name tor && pm2 save
```

## Serveo

---

另一种无需配置路由器且无需安装额外软件包的互联网访问网关方案，是利用**SSH远程端口转发服务**。下文将通过具体示例详细说明该方法。

### 从互联网访问应用

要在互联网上公开应用，请在网关控制台执行命令：

```bash
$ ssh -R 80:localhost:8180 serveo.net
```

-R选项指示SSH客户端请求从服务器转发端口，并将代理请求发送到指定主机和端口（您的网关）。serveo.net的子域名将被分配用于HTTP流量转发。

控制台将返回类似以下响应信息：

```bash
Hi there
Forwarding HTTP traffic from https://alias.serveo.net
Press g to start a GUI session and ctrl-c to quit.
```

现在要通过互联网连接您的网关，在浏览器输入：

https://**别名**.serveo.net

> 上述案例中**别名**为自动生成/分配。每个实例具有唯一别名，您实际获得的将不同。

您也可以指定自定义别名（若可用将被分配）。例如要使用**bramka**别名，请在控制台输入：

```bash
$ ssh -R bramka:80:localhost:8180 serveo.net
```

### 从互联网访问网关控制台

参照应用转发方式，您也可以转发SSH连接，在控制台输入：

```bash
$ ssh -R bramka:22:localhost:8022 serveo.net
```

控制台将返回类似以下响应信息：

```bash
Hi there
Forwarding SSH traffic from alias "bramka"
Press g to start a GUI session and ctrl-c to quit.
```

现在要在局域网外通过SSH连接网关，只需在控制台输入：

```bash
$ ssh -o ProxyCommand="ssh -W bramka:22 serveo.net" bramka -i id_rsa_ais
```

### 保存SSH远程端口转发配置

- autossh

为确保远程端口转发能自动重连，我们将使用autossh替代ssh。在终端中安装以下软件包：

```bash
 $ apt install autossh
 ```

若需网关每次重启后自动启用远程访问，可通过PM2进程管理器实现。

> 注意：下例中的**bramka**仅为示例别名，实际定义进程时需替换为您自定义的别名

- 在PM2中定义应用访问进程

```bash
$ pm2 start autossh --name ext-http \
    -- -M 0 -o ServerAliveInterval=60 -R bramka:80:localhost:8180 serveo.net
```

- 在PM2中定义终端访问进程

```bash
$ pm2 start autossh --name ext-ssh \
    -- -M 0 -o ServerAliveInterval=60 -R bramka:22:localhost:8022 serveo.net
```

- 保存已定义进程

```bash
$ pm2 save
```

## 应用访问安全加固

当网关仅在局域网运行时，我们提供三种认证方式：

- 用户名密码登录
- 可信网络快捷登录（从用户列表选择即可免密登录）
- API密钥登录

认证配置界面如下：

```yaml
homeassistant:
  auth_providers:
    - type: trusted_networks
    - type: homeassistant
    - type: legacy_api_password
```

应用中的实际显示效果：

![局域网登录界面](/img/en/frontend/frontend_local_login.png)

### 禁用快捷登录

此类简易认证方式不适用于互联网访问场景。当启用互联网访问时，系统会自动切换至以下认证配置：

```yaml
homeassistant:
  auth_providers:
    - type: homeassistant
```

启用互联网访问后，应用登录将强制要求凭证：

![互联网登录界面](/img/en/frontend/frontend_internet_login.png)

### 启用多因素认证模块

多因素认证模块在输入密码（已知凭证）后，会要求输入通过手机接收的时效性一次性验证码（独有凭证）。启用该功能需进入"用户设置"，并按照**多因素认证模块**区域的指引操作：

![一次性密码设置](/img/en/bramka/totp_settings.png)