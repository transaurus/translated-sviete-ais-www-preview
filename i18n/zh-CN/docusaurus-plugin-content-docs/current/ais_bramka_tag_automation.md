---
title: "Automatyzacja wyzwalana skanem"
sidebar_label: Automatyzacja wyzwalana skanem
---

## 简介

无需通过语音指令或聊天窗口输入命令，只需将已解锁的手机贴近NFC标签，即可向网关发送待执行指令。  
您也可以通过手机摄像头扫描二维码，将其发送至网关以触发自动化流程。

二维码与NFC标签扫描功能已内置在我们的移动应用"AIS dom - 扫描"中。

![AIS scan](/img/en/bramka/ais_scan_tags.png)

### 支持的扫描类型

我们致力于支持所有标签扫描，目前提供四种处理方式：

#### 1. AIS网关标识扫描

扫描AIS网关标识后，系统将自动配置连接参数并建立与网关的通信。

![AIS scan](/img/en/bramka/nfc_ais_scan.png)

#### 2. 含文本数据的NFC标签

若扫描标签包含纯文本记录（``text/plain``），系统会将扫描内容视为文本指令发送至网关。  
通过此方式，您可在标签上存储[家庭助理支持的任何指令](/docs/ais_app_assistent_commands/)，从而控制系统设备、播放音频或触发自动化流程。

![NFC text](/img/en/bramka/nfc_text_data.png)

#### 3. 含ais/event数据标识的标签

系统可识别URI资源标识符``ais/event``

![NFC event](/img/en/bramka/nfc_ais_data.png)

扫描含ais/event数据标识的NFC标签时，网关将触发**tag_scanned**事件，并通过**event_data**字段传递记录在``ais/event``类型中的内容。  
该机制支持创建以NFC标签扫描为触发条件的自动化规则，下文将详述两个应用案例。

#### 4. 其他类型

您还可扫描银行卡、智能手表、音响等带有NFC标签的设备/物品。  
若能成功读取标识符，系统会将其视作ais/event处理：触发**tag_scanned**事件，并通过**event_data**字段传递扫描标签的**tag_id**标识符。

:::info
推荐使用免费应用[NFC Tools](https://play.google.com/store/apps/details?id=com.wakdev.wdnfc&hl=pl)来向NFC标签写入文本。该应用操作直观：启动后，在首个标签页可读取NFC标签并检查是否解锁写入权限。若标签可写入，则切换至**写入**标签页，选择**添加记录**，然后选择**文本**类型，输入需要网关执行的指令文本（例如``播放Eska Rock电台``），最后点击**确认**。
:::

## 示例1 - 语音播报扫描到的标识符

创建名为``扫描NFC标签标识符``的自动化：

![NFC](/img/en/bramka/nfc_auto_example1.png)

选择触发器类型为``tag_scanned``事件：

![NFC](/img/en/bramka/nfc_auto_example2.png)

执行动作为语音播报服务，播报内容为扫描到的标识符信息：

``` yaml
service: ais_ai_service.say_it
data_template:
  text: Zeskanowano kod NFC {{ trigger.event.data.tag_id }}

```

![NFC](/img/en/bramka/nfc_auto_example3.png)

## 示例2 - 扫描指定NFC标识符后关闭灯光

创建名为``扫描银行卡后开启客厅灯``的自动化：

![NFC](/img/en/bramka/nfc_auto_example4.png)

触发器设置为``tag_scanned``事件，并指定目标``tag_id``标识符：

![NFC](/img/en/bramka/nfc_auto_example5.png)

执行动作为切换客厅灯光状态：

![NFC](/img/en/bramka/nfc_auto_example6.png)

## 功能演示视频

<iframe width="560" height="315"  src="https://www.youtube.com/embed/nzRBeRZZX7Q" frameBorder="0" allowFullScreen></iframe>

## 自动化蓝图

通过现成的[自动化蓝图](ais_bramka_automation_blueprint)可快速创建基于TAG扫描触发的自动化。

只需两步：

1. 选择预定义蓝图**扫描TAG后执行指令**

![添加新自动化](/img/en/bramka/blueprint_tag_0.png)

2. 填写并保存模板配置：

![添加新自动化](/img/en/bramka/blueprint_tag.png)