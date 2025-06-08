---
author: Jola AI-Speaker
authorURL: https://github.com/sviete
authorImageURL: https://avatars3.githubusercontent.com/u/43966761?s=460&v=4
title: Wersja systemu 0.96.10 System Wear OS, uproszczenia w aplikacji
---

## 2019年8月8日发布的系统版本0.96.10

### Wear OS

我们的<a href="https://play.google.com/store/apps/details?id=pl.sviete.dom" target="_blank">免费客户端应用AIS dom</a>（可远程控制网关并发送语音指令的应用）现已适配Wear OS系统。

现在您可以通过佩戴Wear OS系统的智能手表或其他设备，向网关发送语音指令来播放音乐或控制智能家居设备。观看下方视频了解实际演示 :)

<iframe width="560" height="315"  src="https://www.youtube.com/embed/_PY8FsPDQzA" frameBorder="0" allowFullScreen></iframe>

<!--truncate-->

### 网页应用中的高级模式

为迎接1.0版本，我们正在简化家庭助理（Home Assistant）的默认用户界面。自0.96版本起，我们将对终端用户隐藏高级配置选项和控制台，这些功能仅对管理员可见。

![管理员菜单](/img/en/blog/new_menu_for_admins.png)

系统默认将首个用户设为管理员，该用户可在配置界面添加其他成员账户，并指定其所属组别（管理员组或普通用户组）。

![用户组别](/img/en/blog/user_group.png)

### 自动化规则状态与人员状态信息

我们在首页新增了两个信息卡片：人员状态卡片和已定义自动化规则卡片。这些信息也可通过遥控器（无需显示器）查看。

现在可通过新增语音指令启用自动化规则："启动+自动化名称" 或 "自动化"+自动化名称
[语音指令手册](/docs/ais_app_assistent_commands#uruchamianie-automatyzacji)

![人员与自动化](/img/en/blog/persons_and_automations.png)

### 其他重要更新

- 改进设备配对模式。进入配对模式只需快速按压设备按钮3至7次（原需精确按压4次）或长按4秒。配对模式将持续4分钟（原为3分钟）。WiFi管理器（设备AP及参数设置应用服务器）默认启用信道1（原为信道13）。
- 记忆语音助手选择，支持网关（扬声器）与移动客户端应用独立设置语音类型
- 最新版Home Assistant <a href="https://www.home-assistant.io/blog/2019/07/17/release-96/" target="_blank">0.96</a>
- 应用内集成搜索功能。通过应用内向导可添加的设备和服务日益增多，新增的搜索框便于筛选待添加的集成。

![集成搜索](/img/en/blog/search_integration.png)

- 网页应用支持网络设置分组

![网络设置](/img/en/blog/network_settings.png)