---
title: "Dostęp do bramki po FTP"
sidebar_label: FTP
---

家庭助手默认启用了FTP服务器，使您可以远程管理网关上的文件。

FTP服务运行在标准端口**21**和端口**1024**上

[ftp://ais-dom.local](ftp://ais-dom.local)

## 从Windows系统登录

Windows系统"出厂"不支持mDNS，因此要连接到网关需要知道其IP地址[查看网关IP地址](/docs/ais_bramka_remote_index#sprawdzenie-adresu-ip-w-aplikacji)

我们推荐使用功能完整的FTP客户端，因为Windows文件管理器内置的FTP客户端功能有限。
我们测试过可以推荐的免费客户端是[WinScp](https://winscp.net/eng/download.php)

安装WinScp后创建新会话并设置：

- 文件协议：FTP
- 主机名：网关IP
- 端口号：21或1024
- 匿名登录：勾选

可以保存设置或直接点击登录按钮连接：

![启动FTP客户端](/img/en/bramka/ftp_windows_1.png)

要进入网关配置编辑，使用WinScp连接网关后，右侧窗口会出现新的网关连接会话 - 默认目录：/storage/emulated/0
双击路径名称旁更改目录并输入：
/data/data/com.termux/files/home/AIS

![启动FTP客户端](/img/en/bramka/ftp_windows_2.png)

现在可以在默认编辑器中编辑配置：

![启动FTP客户端](/img/en/bramka/ftp_windows_3.png)

## 从Linux系统和Apple系统登录

网关应自动出现在系统文件管理器的network:///中

![启动FTP客户端](/img/en/bramka/ftp_connection_1.png)

当然您也可以使用任何FTP客户端通过网关IP在端口**1024**上匿名连接网关FTP服务器

![启动FTP客户端](/img/en/bramka/ftp_connection_2.png)

## 浏览文件

在[ftp://ais-dom.local:1024/sdcard/dom](ftp://ais-dom.local:1024/sdcard/dom)位置您可以添加音频文件，这些文件随后会在家庭助手系统的"内部存储"位置可见并可供播放

![启动FTP客户端](/img/en/bramka/ftp_connection_3.png)

## 家庭助手系统配置

在路径 [ftp://ais-dom.local:1024/data/data/com.termux/files/home/AIS](ftp://ais-dom.local:1024/data/data/pcom.termux/files/home/AIS) 下存放着家庭助理系统的配置文件

![启动FTP客户端](/img/en/bramka/ftp_connection_4.png)