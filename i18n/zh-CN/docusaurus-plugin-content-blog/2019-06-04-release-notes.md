---
author: Celina AI-Speaker
authorURL: https://github.com/sviete
authorFBID: 1186570423
title: Wersja systemu 0.93.6  Łatwiejsza nawigacja i konfiguracja
---

## 2019年6月4日发布的系统版本0.93.6

### 触控屏幕导航功能优化

在触控屏设备上新增了通过滑动手势（swipe）在应用不同标签页间切换的导航功能。

<iframe width="560" height="315"  src="https://www.youtube.com/embed/KfmvwHS6Noo" frameBorder="0" allowFullScreen></iframe>

<!--truncate-->

### 简易配置向导启动

首次启动"家庭助理"时，系统会引导完成基础配置流程。第一步是创建管理员账户——该账户拥有系统所有功能的完全访问权限，并可添加其他用户账户。在初始化阶段（或后续在配置中完成），可添加设备和需要集成的服务。该功能将持续完善——下个版本将新增地图定位选择、时区设置等系统基础配置功能。最终目标是实现所有组件均可通过应用界面配置，无需手动编辑参数文件。

<iframe width="560" height="315"  src="https://www.youtube.com/embed/CiysJlfZK70" frameBorder="0" allowFullScreen></iframe>

### 更便捷的完整重置功能

在开发版中，我们鼓励用户充分实验网关功能——自由添加设备、调整设置、配置界面等。若实验效果不尽如人意，现在可通过应用界面便捷地执行完整重置操作（无需启动控制台输入命令），将"家庭助理"恢复至默认版本。

<iframe width="560" height="315"  src="https://www.youtube.com/embed/3FO9hBl1V90" frameBorder="0" allowFullScreen></iframe>

### 其他重要更新

- 语音反馈现支持支持语音合成的浏览器及移动客户端，无论本地网络或远程连接均可使用
- 通过遥控器可获取选中项目的扩展信息（如播放音频内容时按上方向键显示当前播放内容详情）
- 支持Spotify专辑、艺术家频道及播放列表的完整播放
- 新增Spotify随机播放开关功能
- 移动客户端及网关端应用采用简化新菜单
- 默认关闭本地网络的HTTPS网关访问服务
- 集成最新版Home Assistant
<a href="https://www.home-assistant.io/blog/2019/05/16/release-93/" target="_blank">0.93</a>