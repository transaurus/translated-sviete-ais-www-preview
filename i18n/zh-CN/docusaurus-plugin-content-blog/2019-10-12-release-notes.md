---
author: Jola AI-Speaker
authorURL: https://github.com/sviete
authorImageURL: https://avatars3.githubusercontent.com/u/43966761?s=460&v=4
title: Wersja systemu 0.99 Automatyczne Aktualizacje, SUPLA, TAURON eLicznik
---

## 系统版本 0.99（2019年10月12日）

## 自动更新功能

我们在网关设置中新增了启用自动更新的选项。开启后，系统将每日检查并自动安装家庭助理（Asystent domowy）组件的可用更新。

<div>
  <video width="100%" height="100%" playsInline autoPlay muted loop>
    <source src="/video/autoupdate.webm" type="video/webm"/>
  </video>
</div>

<!--truncate-->

> 注意：部分更新需要设备重启，此操作也将自动完成。

当然，如果您更倾向于手动控制更新时机，可保持自动更新关闭状态，继续按原有方式在合适时间手动启动家庭助理更新。更新能提供最新功能和安全补丁，确保系统稳定运行，因此我们强烈建议定期执行更新。

## SUPLA平台集成

我们发布了与SUPLA OpenAPI集成的首个版本（当前仅支持百叶窗和开关，功能尚未完整）。该实现基于[Michał Węgrzynek](https://github.com/mwegrzynek)开发的[PySupla](https://github.com/mwegrzynek/pysupla)包及其为Home Assistant编写的集成组件。

[配置说明](/docs/ais_app_supla)

<div>
  <video width="100%" height="100%" playsInline autoPlay muted loop>
    <source src="/video/supla.webm" type="video/webm" />
  </video>
</div>

此集成面向希望通过家庭助理语音控制SUPLA设备的用户。我们与SUPLA项目及Zamel公司无任何关联——仅因认可其出色的硬件产品而开发此功能。

## 其他重要变更

- 为[Hacs项目提交了小修复](https://github.com/custom-components/hacs/pull/636)，使Hacs能在包括家庭助理在内的更多平台上运行
- 更新了apt仓库中600多个Linux软件包至最新版本，包括：

```bash
apt 1.4.9-16 arm [upgradable from: 1.4.9-15]
bash 5.0.11 arm [upgradable from: 5.0.9]
busybox 1.30.1-9 arm [upgradable from: 1.30.1-8]
ca-certificates 20190828 all [upgradable from: 20190515]
curl 7.66.0-1 arm [upgradable from: 7.65.3-6]
libcrypt 0.2-2 arm [upgradable from: 0.2-2]
libcurl 7.66.0-1 arm [upgradable from: 7.65.3-6]
libgcrypt 1.8.5 arm [upgradable from: 1.8.4-1]
libmosquitto 1.6.7 arm [upgradable from: 1.6.4]
libwebsockets 3.2.99.1 arm [upgradable from: 3.1.0]
mosquitto 1.6.7 arm [upgradable from: 1.6.4]
nodejs 12.11.1 arm [upgradable from: 12.4.0-2]
openssh 8.0p1-6 arm [upgradable from: 8.0p1-3]
openssl 1.1.1d-1 arm [upgradable from: 1.1.1c-2]
python 3.7.4-1 arm [upgradable from: 3.7.3-1]
rclone 1.49.5 arm [upgradable from: 1.48.0-1]
ttyd 1.5.2-1 arm [upgradable from: 1.5.2]
```

- 新增C/C++语言支持，集成[clang 8.0.1-4](https://clang.llvm.org/)包
- 最新稳定版Home Assistant <a href="https://www.home-assistant.io/blog/2019/09/18/release-99/" target="_blank">0.99</a> 包含多项功能增强与改进

----

欢迎立即升级体验。

2019年10月 家庭助理团队