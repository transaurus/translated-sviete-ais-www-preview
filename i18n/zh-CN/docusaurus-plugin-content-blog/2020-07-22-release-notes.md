---
author: Jola AI-Speaker
authorURL: https://github.com/sviete
author_title: Asystentka
authorImageURL: https://avatars3.githubusercontent.com/u/43966761?s=460&v=4
title: Wersja systemu 0.112.6
tags: ["location", "demo", "home assistant", "wizard"]
---

# 0.112.6 定位，定位，还是定位...

- ![Location](/img/en/blog/202007/gps.png) 位置上报功能
- ![Kreator](/img/en/blog/202007/magic-wand.png) 增强版初始化配置向导
- ![Komendy](/img/en/blog/202007/mobile-request.png) 向移动应用发送指令
- ![Demo](/img/en/blog/202007/eye.png) 应用演示版
- ![Home Assistant](/img/en/blog/202007/hass.png) 新版Home Assistant

<!--truncate-->

:::tip[温馨提示]
更新前强烈建议先进行[配置备份](/docs/ais_bramka_configuration_software#kopia-zapasowa-konfiguracji)。通过预先验证配置完整性可显著提升升级成功率。
:::

:::important[重要通知]
若升级后遇到问题，请参考[控制台更新指南](/docs/ais_bramka_update_manual)或[应用完全重置步骤](/docs/ais_bramka_reset_ais_step_by_step)——特别是安装了非标准组件的用户需特别注意。
:::

:::caution[升级重要提示!]
 **升级后首次启动可能耗时长达20分钟**

 ![wait](/img/en/blog/202007/wait.png) 在此期间将更新网关集成库并迁移数据库至新格式

 **请耐心等待升级完成**
:::

## ![Location](/img/en/blog/202007/gps.png) 位置上报功能

家庭助理可接收来自不同设备/应用的位置更新数据，基于人员区域变化触发自动化场景。

为简化配置流程，我们新增了从AIS dom移动应用直接向网关发送位置数据的功能。

:::tip[该功能需AIS dom应用1.3.0及以上版本]
是否上报位置数据取决于您是否授予应用位置权限并启用了位置上报服务。
:::

启用位置上报仅需四步：

1. 将移动应用升级至1.3.0或更高版本
![Location](/img/en/blog/202007/mob_app_version.png)

2. 启用"位置上报"服务
![Location](/img/en/blog/202007/mob_app_location_1.png)

3. 授予AIS应用设备位置访问权限
![Location](/img/en/blog/202007/mob_app_location_2.png)

4. 通知栏将显示**GPS**标识——表示位置数据正在上报至网关
![Location](/img/en/blog/202007/mob_app_location_3.png)

最终在网页应用的地图上，我们将看到手机当前位置的标记：
![Location](/img/en/blog/202007/location_in_web_app1.png)

只需点击当前位置标记，即可快速创建基于当前坐标的地理围栏：
![Location](/img/en/blog/202007/location_in_web_app2.png)

![Location](/img/en/blog/202007/location_in_web_app3.png)

完成地理围栏设置后，即可创建基于位置触发的自动化场景。
具体操作详见文档《[基于位置的自动化](/docs/ais_bramka_presence_detection)》

还可在界面中添加地图卡片
![Location](/img/en/blog/202007/location_in_web_app6.png)

并显示设备移动轨迹记录：
![Location](/img/en/blog/202007/location_in_web_app5.png)

## ![Kreator](/img/en/blog/202007/magic-wand.png) 初始配置向导升级

我们优化了初始化配置向导界面，操作更简单直观

### 网页端改进：

- 新增独立界面用于从AI-Speaker下载配置
![Konto właściciela](/img/en/bramka/onboarding_step_1_1.png)

- 更突出显示需要联网操作的步骤
![Konto właściciela](/img/en/bramka/onboarding_step_2_0.png)

- 在最终配置步骤新增移动端应用提示
![Konto właściciela](/img/en/blog/202007/wizard_mob_app.png)

完整初始化流程详见文档《[首次运行指南](/docs/ais_bramka_first_run_step_account)》

### 移动端改进：

- 新增地理位置权限授权界面

<img src="/img/en/frontend/ais_dom_new_wizard_1_1_mob_apk.png" alt="AIS Dom"/>

- 增加连接DEMO网关功能

<img src="/img/en/frontend/ais_dom_new_wizard_3_mob_apk.png" alt="AIS Dom"/>

完整移动端配置流程详见文档《AIS dom应用：向导配置指南》

## ![Komendy](/img/en/blog/202007/mobile-request.png) 向移动端发送指令

网关现提供``ais_ai_service.mob_request``服务，可通过该服务向**AIS dom**移动应用发送远程指令（查询/请求）。
借助自动化功能，您可以从网关远程激活移动设备麦克风或查询设备当前位置。

:::info
**该功能灵感来自社区论坛（感谢用户创意！），我们觉得非常实用便进行了开发实现**

后续将通过案例演示具体应用场景，并完善API文档说明。
:::

![Notify](/img/en/blog/202007/mic_on_service.png)

:::warning[注意]
只有当移动设备上启用了相应权限（麦克风和/或位置服务）时，才能从已登录的网关向移动设备发送远程执行命令。

我们会在通知中显示此类远程命令的执行状态，确保设备所有者完全知情。
:::

## ![Demo](/img/en/blog/202007/eye.png) 应用演示版

我们正在开发[家庭助理演示版](https://demo.ai-speaker.com/)，用于展示家庭助理系统的核心功能。

演示版的目的是呈现家庭助理的解决方案能力，并针对用户反馈的问题提供示例实现方案。

![DEMO](/img/en/blog/202007/demo.png)

## ![Home Assistant](/img/en/blog/202007/hass.png) 新版Home Assistant

最新稳定版[Home Assistant 0.112.5](https://www.home-assistant.io/blog/2020/07/01/release-112/)
一如既往带来精彩新功能和可通过应用直接配置的集成组件 🥳

![Home Assistant](/img/en/blog/202007/ha_0.112.png)

----

欢迎升级并[参与论坛讨论 :)](https://ai-speaker.discourse.group/)
AI-Speaker 2020年7月
----