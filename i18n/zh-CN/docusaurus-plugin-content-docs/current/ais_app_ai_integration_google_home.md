---
title: "AIS Google Home"
sidebar_label: AIS Google Home
---

## 简介

AIS Google Home 是将家庭助手与Google助理开发者平台集成的解决方案。该集成通过官方 [Google Assistant SDK](https://developers.google.com/assistant) 实现，允许用户通过家庭助手与Google助理进行对话。

![AIS Google Home配置](/img/en/bramka/ais_google_home_1.png)

## 集成配置

要配置AIS Google Home，请进入配置界面后打开集成面板。点击右下角带有"+"图标的橙色按钮，从可用集成列表中选择 **AIS Google Home**。

![Google Home配置](/img/en/bramka/ais_google_home_0.png)

### 从Google获取OAuth2 JSON文件

AIS Google Home集成需要在Google平台配置项目并注册设备，以使Google助理能响应特定设备的指令。

以下将逐步演示如何在Google平台完成设备注册。

:::caution[注意]
**Google端集成说明**

Google助理API正在持续更新中，因此Google端的集成流程可能会发生变化。如果当前描述已过时，请遵循Google官方最新文档：[Integrate with the Google Assistant](https://developers.google.com/assistant/sdk/guides/service/python/embed/config-dev-project-and-account)。
:::

1. 登录Google助理扩展功能平台 https://console.actions.google.com/

2. 创建新项目

![Google Home配置](/img/en/bramka/ais_google_home_3.png)

继续操作需接受服务条款

![Google Home配置](/img/en/bramka/ais_google_home_3_1.png)

3. 输入项目名称，将语言设置为波兰语，地区设为波兰，然后点击 **Create project**

![Google Home配置](/img/en/bramka/ais_google_home_4.png)

4. 选择 **Device registration** 选项

![Google Home配置](/img/en/bramka/ais_google_home_5.png)

5. 点击 **REGISTER MODEL**

![Google Home配置](/img/en/bramka/ais_google_home_6.png)

7. 填写产品名称、制造商信息，并选择设备类型为 **Speaker**

![Google Home配置](/img/en/bramka/ais_google_home_7.png)

8. 下载OAuth2.0凭证文件并保存到本地（后续步骤需要使用）

![Google Home配置](/img/en/bramka/ais_google_home_8.png)

9. 勾选所有特性（All traits）并保存配置

![Google Home配置](/img/en/bramka/ais_google_home_9.png)

### 启用Google助手API

下一步需要在Google平台启用Google助手API，具体操作如下：

1. 在新浏览器标签页中访问[Google API控制台](https://console.developers.google.com/apis/api/embeddedassistant.googleapis.com/overview)

继续操作前需同意服务条款

![Google Home配置](/img/en/bramka/ais_google_home_9_1.png)

2. 为项目启用**Google Assistant API**

确保已选择我们的**AI-Speaker**项目

![Google Home配置](/img/en/bramka/ais_google_home_9_2.png)

搜索并启用项目的**Google Assistant API**

![Google Home配置](/img/en/bramka/ais_google_home_10.png)

3. 进入**凭据**页面选择**配置同意屏幕**

![Google Home配置](/img/en/bramka/ais_google_home_11.png)

4. 填写**应用名称**，选择**帮助邮箱**，点击底部**保存**按钮

![Google Home配置](/img/en/bramka/ais_google_home_12.png)

### 设备OAuth2凭证配置

返回家庭助手集成界面，将Google下载的**JSON OAuth2**文件完整内容粘贴至**设备OAuth2凭证**字段

![Google Home配置](/img/en/bramka/ais_google_home_13.png)

点击**SUBMIT**进入下一步

点击**认证链接**
![Google Home配置](/img/en/bramka/ais_google_home_14.png)

登录Google账户

![Google Home配置](/img/en/bramka/ais_google_home_15.png)

授予AI-Speaker访问权限

![Google Home配置](/img/en/bramka/ais_google_home_16.png)

复制授权码

![Google Home配置](/img/en/bramka/ais_google_home_17.png)

返回家庭助手应用，将代码粘贴至**代码**字段

![Google Home配置](/img/en/bramka/ais_google_home_18.png)

成功添加新集成
![Google Home配置](/img/en/bramka/ais_google_home_19.png)

## Google助手功能实现

### 通过家庭助手调用Google助手

若需将指令直接发送至Google助手，只需在指令前添加"Google"关键词

![Google Home配置](/img/en/bramka/ais_google_home_22.png)

### 通过家庭助手API调用Google助手

AIS Google Home与其他集成服务类似，可通过网关基于设备状态或用户位置等信息，实现向Google助手发送指令的自动化操作

![Google Home配置](/img/en/bramka/ais_google_home_23.png)

## 故障排查

:::caution[注意]
Google助手设备开发接口仍处于持续演进阶段。开发Google Home集成的程序员清楚知道并非所有功能都已完善。**若遇到异常，请按以下补充步骤检查**
:::

### Google Home语言设置

常见问题之一是Google助手的交互语言。若需设置为波兰语，目前仍需在Google Home移动应用中同时设置波兰语和英语两种语言，如下图所示：

![Google Home配置](/img/en/bramka/ais_google_home_20.png)
![Google Home配置](/img/en/bramka/ais_google_home_21.png)

### "请登录"类提示

若收到"请登录您的账户"提示，请确认集成配置中使用的Google账户已启用Google助手功能。可通过手机/平板启动Google助手，选择网关集成时授权的同一账户进行验证

该问题通常发生在企业或教育类Google账户，因为这些账户的管理员可能限制了Google助手的使用权限

![Google Home配置](/img/en/bramka/ais_google_home_24.png)

若Google助手在其他设备（使用集成配置的同一账户）上运行正常，如下图所示：

![Google Home配置](/img/en/bramka/ais_google_home_25.png)

即可通过家庭助手调用Google助手功能

### 无文本响应

Google Home接口不保证对所有请求返回文本响应。Google助手基于音频反馈机制（即向扬声器输出音频），而非家庭助手采用的文本转语音（TTS）方案

更多信息请参考示例项目 [Google SDK 在 Github 上的讨论](https://github.com/googlesamples/assistant-sdk-nodejs/issues/13)