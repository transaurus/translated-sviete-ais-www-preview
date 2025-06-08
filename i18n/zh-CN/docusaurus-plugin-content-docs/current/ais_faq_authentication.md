---
title: "Jak działa logowanie do aplikacji."
sidebar_label: Jak działa logowanie do aplikacji
---

## 如何登录智能家居助手？

为在网关接入互联网时提供最高安全性，同时兼顾纯局域网环境下的便捷认证，我们提供了多种认证机制。

此外，为简化应用使用流程，我们支持在浏览器/客户端中保存登录凭据。

对安全性有极高要求的用户，我们提供多因素认证（Multi-factor authentication）模块。

文档中已概述[应用访问安全机制](/docs/ais_bramka_remote_www_index)，下文将通过实例进行说明。

### 网关在局域网环境下的登录

当网关仅运行于局域网时，默认提供三种认证方式可选：

- 可信网络简易登录（从用户列表选择即可登录，无需输入密码）
- 用户名密码登录
- API密码登录
这三种认证方式的配置界面如下：

这三种认证方式的配置界面如下：

```yaml
homeassistant:
  auth_providers:
    - type: trusted_networks
    - type: homeassistant
    - type: legacy_api_password
```

#### **"可信网络"**登录机制

在应用中启用第一种**trusted_networks**（可信网络）认证方式时，界面显示如下：

![局域网登录](/img/en/faq/auth_trusted_networks.png)

#### **"用户名密码"**登录机制

启用第二种**homeassistant**（用户名密码登录）认证方式时，界面显示如下：

![局域网登录](/img/en/faq/auth_homeassistant.png)

#### **"API密码"**登录机制

启用第三种**legacy_api_password**（API密码）认证方式时，界面显示如下：

![局域网登录](/img/en/faq/auth_legacy_api_password.png)

### 网关开启互联网访问时的登录

当启用互联网访问功能时，**出于安全考虑将自动禁用简易登录方式**。

![启用互联网访问](/img/en/faq/access_form_internet.png)

系统会自动应用文档中描述的[禁用简易登录](/docs/ais_bramka_remote_www_index)配置方案

```yaml
homeassistant:
  auth_providers:
    - type: homeassistant
```

上述配置意味着我们只能通过用户名和密码登录，无法再选择简易认证方式。

![启用互联网访问](/img/en/faq/auth_access_form_internet_on.png)

## 为什么首次登录后无需重复登录？

首次登录时会询问是否记住登录凭证。

![记住登录凭证](/img/en/faq/remember_auth.png)

记住登录凭证意味着将信息保存在当前使用的浏览器/客户端中。只要凭证未被清除且使用同一浏览器，系统将不再要求重新输入登录信息。

## 如何在客户端清除已保存的登录凭证？

只需执行注销操作：进入用户配置文件页面，点击**注销**按钮

![注销](/img/en/faq/logaut.png)

## 如何添加其他用户？

进入**配置**菜单，选择**用户**选项。

![添加用户](/img/en/faq/add_user.png)

点击右下角加号按钮创建新用户，填写用户信息表单后点击**创建**按钮。

![保存用户](/img/en/faq/add_user_save.png)

## 如何增强安全防护？

当网关暴露在互联网时，存在外部攻击者通过网关地址尝试入侵的风险。

网关运行着全屋智能系统，通常还包括安防警报和自动门锁控制。因此对外开放网关访问时需保持高度警惕。

我们充分意识到这些风险并采取以下防护措施：

1. 启用互联网访问时强制要求用户名密码认证——禁用简易登录方式

2. 所有用户密码均以[加盐加密](https://pl.wikipedia.org/wiki/S%C3%B3l_(kryptografia))形式存储，即使攻击者获取存储文件也无法解密原始密码。

同时强烈建议启用多因素认证模块（Multi-factor authentication）。

多因素认证模块在输入密码（即已知信息）后，还会要求输入一个具有时效性的一次性验证码（该验证码会发送至您的手机，即只有您能获取的凭证）。

要启用此安全功能，请进入**用户资料**页面，在**多因素认证模块**区域选择**启用**选项，随后按指引操作即可。

![多因素认证](/img/en/faq/auth_mfa_2.png)

启用多因素认证后，除了输入用户名和密码登录外，还需提供手机接收的一次性验证码。

![多因素认证](/img/en/faq/auth_mfa_mob.png)

## 如何自定义偏好的登录方式？

只需覆盖我们的默认配置，根据自身需求移除或添加认证提供程序即可。

以下是分步操作指南：

1. 进入控制台

![控制台](/img/en/faq/go_to_console.png)

2. 在控制台中进入认证配置编辑界面

```bash
$ cd AIS
$ nano configuration.yaml  
```

3. 覆盖系统默认配置

我们已在文档中说明[家庭助手高级配置](/docs/ais_gate_faq_config_yaml)的工作原理

若希望始终采用用户名密码登录（即使网关未开启互联网访问），请使用以下配置：

```yaml
homeassistant:
  auth_providers:
    - type: homeassistant
```

![编辑配置](/img/en/faq/edit_configuration.png)

4. 确认配置修改无误后重启系统

> 配置文件configuration.yaml对空格数量敏感，修改后请务必验证配置有效性。进入**配置**菜单选择**服务器控制**，点击**检查配置**按钮进行验证。

![配置检查](/img/en/faq/reload_config.png)

完成上述配置修改并重启系统后，无论网关是否开启互联网访问，都将强制采用用户名密码登录方式。

## 如何添加自定义登录方式？

欢迎查阅[Home Assistant系统开发者文档](https://developers.home-assistant.io/docs/auth_index.html)。

如果您掌握Python编程，可以为自己的本地安装环境添加专属认证方式。

我们始终欢迎系统优化建议。若您认为自己的解决方案具有普适价值，可提交给全球数万用户共同使用。当您的代码通过Home Assistant核心开发团队及社区审核后，该功能将被纳入Home Assistant主分支，并随下一版智能家居助手同步发布。