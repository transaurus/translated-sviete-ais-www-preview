---
author: Jola AI-Speaker
authorURL: https://github.com/sviete
authorImageURL: https://avatars3.githubusercontent.com/u/43966761?s=460&v=4
title: Wersja systemu 0.106.7 Migracja serwera na bramce
---

# 0.106.7 服务器迁移

经过一年半的测试，我们决定对系统架构进行重大调整，并改变更新安装方式。

![服务器](/img/en/blog/202003/new_server.png)

<!--truncate-->

此次变更的主要原因是需要完全掌控网关设备的软件更新。我们最初设想所有应用都通过Google Play签名并分发，但无法确保Google Play的更新时间——无人知晓其推送算法何时会将更新推送到设备。因此我们决定改为自主签名并直接更新网关应用。手机/平板/手表端的应用更新时效性要求较低，这些仍将通过Google Play进行更新。

:::important[重要通知]
本次迁移将比常规更新更复杂，因为需要卸载旧应用并安装新签名版本（使用我们的密钥签名）。我们在论坛上提供了详细的逐步操作指南。请预留约1小时时间，按指南从容完成整个迁移过程：

[论坛操作指南链接](https://ai-speaker.discourse.group/t/wip-reczna-akualizacja-serwsiu-ais-dom-na-bramce/299)。
:::

![服务器](/img/en/blog/202003/new_server.png)

这显然是"一次性操作"，待2.x.x版本的服务器应用安装完成后，后续更新将如往常般自动进行。

:::tip[温馨提示]
暂不迁移也不会影响使用——您仍会收到家庭助理应用的常规更新，现有功能均保持正常，仅无法使用麦克风启用、视频播放等新服务。

若迁移过程中遇到问题也无需担心，请通过[info@ai-speaker.com](mailto:info@ai-speaker.com)联系我们的客服，我们将全力协助——最坏情况下可寄回网关由我们代为更新（完全免费服务，请放心:)）。
:::

## 新版文档站点

既然您看到这里，想必已注意到我们全新的文档站点。我们认为版本化文档体系过于复杂，决定从此采用更简洁的方案——文档仅维护当前最新版本。

基于GitHub的旧版站点仍会保留（因存在大量外部链接），但将不再更新。

**新站点的文档索引需要数日时间完成——搜索引擎将逐步恢复正常运作。**

## API接口

我们注意到越来越多用户对网关的创新应用场景。希望这份API文档能帮助开发者实现高级自动化（例如开门自动启动麦克风）以及与其他系统（如Fibaro网关）的集成。

查阅[API文档](/docs/ais_bramka_api_index)

![服务模块](/img/en/frontend/services_2.png)

## 升级前须知

:::tip[重要提示]
请注意：建议升级前先执行[配置备份](/docs/ais_bramka_configuration_software#kopia-zapasowa-konfiguracji)。通过预检配置可确保升级流程顺利。
:::

:::important[注意事项]
若升级后出现异常，请参考[控制台升级指南](/docs/ais_bramka_update_manual)或[应用重置教程](/docs/ais_bramka_reset_ais_step_by_step)——尤其是安装了非标准组件的用户需特别注意。
:::

## Home Assistant

最新稳定版Home Assistant <a href="https://www.home-assistant.io/blog/2020/02/26/release-106/" target="_blank">0.106.6</a>

----

欢迎参与升级讨论[前往论坛 :)](https://ai-speaker.discourse.group/)
AI-Speaker 2020年3月
----