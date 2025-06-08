---
author: Jola AI-Speaker
authorURL: https://github.com/sviete
authorImageURL: https://avatars3.githubusercontent.com/u/43966761?s=460&v=4
title: Wersja systemu 0.107.8
---

# 0.107.8版本：Fibaro集成、仪表盘、自动化助手、日志与数据库

![服务器](/img/en/blog/202004/fibaro.png)

<!--truncate-->

:::tip[提示]
注意：建议在升级前执行[配置备份](/docs/ais_bramka_configuration_software#kopia-zapasowa-konfiguracji)。通过这种方式，您可以在开始升级前验证配置的正确性，提高顺利升级的概率。
:::

:::important[重要信息]
若升级后遇到问题，请查阅[通过控制台升级](/docs/ais_bramka_update_manual)或[执行应用完全重置](/docs/ais_bramka_reset_ais_step_by_step)的流程——这对于在网关上安装了额外非标准组件的用户尤为重要。
:::

# Fibaro集成配置器

本版本新增了与Fibaro HC网关集成的图形化配置器。整个Fibaro通信配置仅需填写访问凭据——在应用中提交表单即可完成。

> 🥳 特别感谢用户**Mariusz先生**远程提供网关设备，使我们得以实现该集成功能 🥰

![Fibaro配置](/img/en/frontend/fibaro_config.png)

该集成基于[Klaudiusz Staniek](https://github.com/kstaniek)开发的API，后由用户[pbalogh77](https://forum.fibaro.com/topic/32395-home-assistant-integrates-fibaro-hclhc2/)将其引入Home Assistant并在Fibaro论坛发布。

Fibaro集成项目在Home Assistant中已持续开发数年。我们通过添加配置器，让用户无需编辑文件即可实现集成，并通过语音控制Fibaro设备，如同操作所有接入AIS家庭网关的其他设备。

> 我们与Fibaro无任何商业关联——既无合作协议，也不持有其硬件设备。因此该集成未被列入AIS家庭网关的内置官方支持列表。

Fibaro用户可在我们的论坛分享使用经验。该主题帖详细解释了[Fibaro集成的工作原理与功能边界](https://ai-speaker.discourse.group/t/ais-pytan-kilka-laika/209/10)

# 仪表盘

您可以创建多种界面配置，并将其保存为"仪表盘"。

此功能支持根据用户偏好及展示设备的特性来自定义仪表盘布局。

![仪表盘](/img/en/blog/202004/pulpit.png)

这意味着您可以拥有多种仪表盘配置：主界面（自动生成）用于桌面浏览器展示、连接至网关的电视上显示图表数据的仪表盘、专为孩子设计的独立界面、挂在墙上的平板专用界面、手机专属界面，以及为妻子定制的色彩更丰富的主题仪表盘🥰等等。

![仪表盘](/img/en/blog/202004/dashboardy.png)

更多详情请参阅文档[导航仪表盘](/docs/ais_app_dashboards)

# 自动化助手

创建高级自动化时，常需要额外字段来存储状态或输入数据。此前这些字段需在系统配置的YAML文件中定义🥺，现在通过应用即可轻松实现🥳。所有用户（不仅是专家）都能直接管理这些附加实体，添加新字段后无需重启系统。太棒了;)

![自动化助手](/img/en/bramka/automation_helpers3.png)

我们在文档中通过[简单闹钟示例](/docs/ais_bramka_automation_helpers)演示了其工作原理

![助手卡片](/img/en/bramka/automation_helpers13.png)

# 日志与数据库

要启用家庭助理系统的日志记录，只需选择外接磁盘中用于存储系统活动记录文件的路径，还可指定日志记录的详细级别。

详见文档[系统日志文件存储](/docs/ais_bramka_configuration_logs_and_db#zapis-logów-systemu-do-pliku)

![日志存储配置](/img/en/bramka/bramka_ais_dom_config_logs.png)

如需访问系统事件历史记录，可将事件存储在外接磁盘或远程数据库中。具体方法参见文档[事件数据库存储](/docs/ais_bramka_configuration_logs_and_db#zapis-zdarzeń-do-bazy-danych)

![事件存储配置](/img/en/bramka/bramka_ais_dom_config_db.png)

## 家庭助理

最新稳定版Home Assistant <a href="https://www.home-assistant.io/blog/2020/03/18/release-107/" target="_blank">0.107.7</a>

除上述亮点功能外，用户界面编辑区域也进行了优化改进——亲自体验后我们给出👍 👍 👍推荐

----

欢迎升级并[参与论坛讨论 :)](https://ai-speaker.discourse.group/)
AI-Speaker 2020年4月
----