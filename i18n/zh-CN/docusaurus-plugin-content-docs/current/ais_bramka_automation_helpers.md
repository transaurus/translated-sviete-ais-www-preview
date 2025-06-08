---
title: "Pomocnicy Automatyzacji"
sidebar_label: Pomocnicy Automatyzacji
---

## 简介

在创建高级自动化规则时，可能需要使用额外字段来存储状态或输入数据。这类元素我们称为"自动化助手"，可以在应用程序中进行定义。

## 进入自动化助手界面

在家庭助手应用中，点击左上角菜单图标打开菜单，然后点击配置。从家庭助手可配置元素列表中选择"助手"选项。

![自动化助手](/img/en/bramka/automation_helpers.png)

## 自动化助手列表界面

在"自动化助手"列表界面中，我们可以选择要编辑的条目（点击该条目），或通过点击右下角的"加号"按钮定义新元素。

![自动化助手](/img/en/bramka/automation_helpers2.png)

## 定义自动化助手

从列表中选择要创建的元素类型，然后进入其属性定义界面。

![自动化助手](/img/en/bramka/automation_helpers3.png)

定义完元素后，我们可以将其放置在界面卡片上，并在自动化规则中使用。

## 示例 - 简单闹钟

### 定义"日期和/或时间"类型的助手

![日期时间助手](/img/en/bramka/automation_helpers4.png)

按照上图所示定义属性后，点击"创建"按钮。

### 将助手添加到卡片

进入仪表盘界面，在选定视图上创建新卡片。可以是最简单的显示元素``input_datetime.budzik``的卡片：
![助手卡片](/img/en/bramka/automation_helpers5.png)

当然，我们可以通过手动添加图片（比如老板等待汇报的照片等）来"美化"卡片：

![助手卡片](/img/en/bramka/automation_helpers6.png)

卡片YAML代码：

``` yaml
type: entities
title: Budzik
header:
  image: >-
    https://www.wikihow.com/images/thumb/6/64/Deal-With-a-Moody-Boss-Step-10.jpg/aid236433-v4-728px-Deal-With-a-Moody-Boss-Step-10.jpg.webp
  type: picture
entities:
  - entity: input_datetime.budzik
```

![助手卡片](/img/en/bramka/automation_helpers13.png)

### 在自动化中使用助手

#### 定义新自动化规则：

![助手自动化](/img/en/bramka/automation_helpers7.png)

我们可以使用模板作为触发器 - 在模板中检查当前时间是否等于闹钟字段设置的时间：

![助手模板](/img/en/bramka/automation_helpers8.png)

#### 完整模板代码：

``` javascript
{{ states('sensor.time') ==
(state_attr('input_datetime.budzik', 'timestamp') | int
| timestamp_custom('%H:%M', True)) }}
```

:::tip[提示]
您可以在"开发者工具" -> "模板"中验证模板代码
:::

前往模板验证界面，在模板编辑器中粘贴如下代码：

``` javascript
{{ states('sensor.time') }}
```

即可查看系统中时间传感器的状态。

![自动化助手模板](/img/en/bramka/automation_helpers9.png)

``sensor.time``是家庭助理系统的内置组件，用于显示应用中的当前时间。

![自动化助手模板](/img/en/bramka/automation_helpers101.png)

若要查看闹钟元素的格式化当前状态，请粘贴以下代码：

``` javascript
{{ (state_attr('input_datetime.budzik', 'timestamp') | int | timestamp_custom('%H:%M', True)) }}
```

![自动化助手模板](/img/en/bramka/automation_helpers10.png)

完整代码用于检查当前时分是否与闹钟设定时间匹配：

``` javascript
{{ states('sensor.time') ==
(state_attr('input_datetime.budzik', 'timestamp') | int
| timestamp_custom('%H:%M', True)) }}
```

![自动化助手模板](/img/en/bramka/automation_helpers11.png)

当条件满足时（即sensor.time时间值等于input_datetime.budzik元素设定值），自动化流程将被触发。

#### 执行自动化动作

自动化动作可以是Jolka语音助手播报的唤醒文本，同时还可启动收音机或播放本地/在线音乐服务中的任意曲目。

![自动化助手模板](/img/en/bramka/automation_helpers12.png)

在Jolka播报文本与启动收音机之间设置延迟动作，是为了确保我们能听清唤醒提示后再播放音乐。
当然这仅是示例，您还可以根据需要实现开灯、渐进调节音量等复杂场景。