---
author: Jola AI-Speaker
authorURL: https://github.com/sviete
author_title: Asystentka
authorImageURL: https://avatars3.githubusercontent.com/u/43966761?s=460&v=4
title: Wersja systemu Bartek
tags: ["automatyzacje", "ais dom", "home assistant"]
---

<div class="IntroAisBlogMenu" >
<div>

![AIS 2020](/img/en/blog/202012/blueprint.png)

</div>
<h2>Schematy <br/>Automatyzacji</h2>
</div>

<div class="IntroAisBlogMenu" >
<div>

![AIS 2020](/img/en/blog/202012/mob_app.png)

</div>
<h2>Aplikacja Mobila</h2>
</div>

<div class="IntroAisBlogMenu" >
<div>

![AIS 2020](/img/en/blog/202012/christmas-tree.png)

</div>
<h2>2021 Wydania</h2>
</div>

<!--truncate-->

## 无忧升级指南

:::tip[配置备份]
### ![A](/img/en/blog/202009/alpha-a-circle.png) 配置备份

注意：升级前建议先执行[配置备份](/docs/ais_bramka_configuration_software#kopia-zapasowa-konfiguracji)。通过这种方式可以在升级前验证配置的正确性，提高升级成功率。
:::

:::important[网关控制台与日志]
### ![B](/img/en/blog/202009/alpha-b-circle.png)网关控制台与日志

若升级遇到问题，请参考[通过控制台升级](/docs/ais_bramka_update_manual)或[执行应用完全重置](/docs/ais_bramka_reset_ais_step_by_step)流程。特别是对于在网关上安装了非标准组件的用户。
:::

:::caution[耐心等待]
### ![C](/img/en/blog/202009/alpha-c-circle.png) 耐心等待。升级后首次启动耗时较长——请保持耐心。

**升级后的首次启动可能耗时长达20分钟。**
在此期间会更新网关上的集成库，并将数据库迁移至新格式。
**请耐心等待升级完成。**
:::

## ![](/img/en/blog/202012/blueprint.png) 自动化蓝图

本次版本将[Home Assistant更新至2020.12最新版](https://www.home-assistant.io/blog/2020/12/13/release-202012/)。Home Assistant 2020.12最重大的新特性是**Blueprints**——自动化蓝图。

自动化蓝图是预先配置好的自动化模板，用户可以轻松定制并添加到智能家居助手作为自动化规则。这些即用型自动化方案只需根据个人需求进行调整即可。

具体操作详见文档[自动化蓝图](/docs/ais_bramka_automation_blueprint)

![自动化列表界面](/img/en/bramka/blueprint1.png)

我们在应用中新增了几个示例自动化蓝图：

- [日落时自动开启照明](/docs/ais_bramka_automation#schemat-automatyzacji)的自动化

![照明控制](/img/en/bramka/blueprint4.png)

- 由[按键事件触发](/docs/ais_bramka_key_event_automation#schemat-automatyzacji)的自动化

![按键](/img/en/blog/202012/blueprint_button.png)

- 由[TAG标签扫描](/docs/ais_bramka_tag_automation#schemat-automatyzacji)触发的自动化

![标签按钮](/img/en/blog/202012/blueprint_tag.png)

- 由[日历事件](/docs/ais_bramka_calendar_event_automation#schemat-automatyzacji)触发的自动化

![日历按钮](/img/en/blog/202012/blueprint_calendar.png)

- 由[位置变更](/docs/ais_bramka_presence_detection#schemat-automatyzacji)触发的自动化

![区域按钮](/img/en/blog/202012/blueprint_zone.png)

我们使用自建的[选择器](https://www.home-assistant.io/docs/blueprint/selectors/)类型"text"来输入指令。

我们正在探索将该机制应用于意图领域——让用户能通过界面直接定义[语音指令](/docs/ais_app_assistent_add_command)（模板：语句→意图→动作）。这项功能有望在2021年实现 :)

## ![](/img/en/blog/202012/mob_app.png) 移动应用 1.8.1.LocalUrlFix

1. 若干修复与优化
最重要的修复涉及局域网内语音指令发送问题：当隧道关闭且连接参数中使用网关ID（而非本地URL）时存在的缺陷。感谢用户反馈，现该功能应能正常运作。

2. 增强通过移动应用音量键（vol+/vol-）控制网关（AIS扬声器）音量的功能

![应用音量控制](/img/en/blog/202012/mob_app_vol.png)

3. 新训练的唤醒词/热词

![嘿 Maya](/img/en/blog/202012/mob_app_hot_word.png)

该功能仍位于移动应用的实验性菜单中。更多讨论详见论坛帖[训练新唤醒词/热词](https://ai-speaker.discourse.group/t/trenujemy-nowe-wake-hot-word-y/1075)

![嘿 Maya](/img/en/blog/202012/hey_maya.png)

## ![](/img/en/blog/202012/christmas-tree.png) 祝大家2021年梦想成真！

**2021年起我们将实行月度发布机制**

每月第一个周三发布BETA版，最后一个周三发布STABLE稳定版

![发布日历](/img/en/blog/202012/calendar_releases.png)

-------

##### AI-Speaker 2020年12月版