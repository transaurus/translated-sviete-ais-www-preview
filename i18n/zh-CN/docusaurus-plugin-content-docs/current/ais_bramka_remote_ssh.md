---
title: "Dostęp do konsoli bramki po SSH"
sidebar_label: SSH
---

家庭助理通过广受欢迎的openssh软件包提供SSH连接功能。

由于网关上的Linux环境是单用户系统，因此无论输入何种用户名，您都将以家庭助理系统中唯一的可用用户身份登录。

## 通过SSH客户端访问控制台

要通过SSH连接到运行在网关上的远程SSH服务器，需在本地计算机打开终端并输入命令"ssh 网关IP地址"，其中网关IP地址替换为您网关的实际IP（例如192.168.1.5）。

```bash
$ ssh <IP-BRAMKI>
```

首次连接时，系统会提示将主机加入已知主机列表——输入"yes"并按回车，随后输入用户密码即可。

:::tip[提示]
默认密码为`dom`，可通过passwd命令修改（与所有Linux系统操作相同）。
:::

## 通过外部客户端访问控制台

### 密码认证方式

如需使用密码连接，需先通过passwd命令设置密码（与所有Linux系统操作相同）

```bash
$ passwd
```

![SSH密钥下载](/img/en/bramka/ssh_passwd.png)

### 授权密钥认证方式

> 家庭助理系统支持通过授权密钥进行SSH登录。已生成并授权的密钥可通过本地实例访问：[http://ais-dom.local/local/id_rsa_ais](https://ais-dom.local/local/id_rsa_ais)

也可通过**实用链接**菜单下载

![SSH密钥下载](/img/en/bramka/ssh_download_key.png)

### 通过密码连接网关控制台

只需启动ssh客户端并输入网关主机名（或IP地址）

```bash
$ ssh ais-dom.local
```

随后输入先前通过passwd命令设置的密码。

### 通过授权密钥连接网关控制台

#### 从Linux和Apple系统连接

获取授权SSH密钥后，可通过以下步骤连接网关控制台：

- 修改密钥文件权限

```bash
$ chmod 400 id_rsa_ais
```

- 使用指定端口和密钥路径启动ssh连接

```bash
$ ssh ais-dom.local -i id_rsa_ais
```

![SSH连接](/img/en/bramka/ssh_console.png)

#### 从Windows系统连接网关控制台

我们推荐使用免费程序[PuTTY](https://www.putty.org/)

安装程序后需要：

##### 将网关下载的访问密钥转换为PuTTY格式

PuTTY使用自有格式存储密钥。要转换密钥为PuTTY格式，我们将使用默认随PuTTY安装的PuTTY Key Generator程序。
在PuTTY Key Generator中点击"Load"按钮：

![SSH连接](/img/en/bramka/ssh_putty_1.png)

加载/导入从网关下载的访问密钥文件：**id_rsa_ais**

![SSH连接](/img/en/bramka/ssh_putty_2.png)

成功导入后

![SSH连接](/img/en/bramka/ssh_putty_3.png)

将文件另存为PuTTY格式的私钥**id_rsa_ais.ppk**

![SSH连接](/img/en/bramka/ssh_putty_4.png)

![SSH连接](/img/en/bramka/ssh_putty_5.png)

![SSH连接](/img/en/bramka/ssh_putty_6.png)

##### 通过PuTTY程序SSH连接网关

运行PuTTY程序并定义与网关的新SSH连接：

- 输入网关IP地址
- 输入端口**8022**
- 选择连接类型为**SSH**

![SSH连接](/img/en/bramka/ssh_putty_7.png)

然后指定通过PuTTY Key Generator转换的私钥**id_rsa_ais.ppk**的路径

![SSH连接](/img/en/bramka/ssh_putty_8.png)

为连接命名并保存，以便下次连接时无需重复上述配置。