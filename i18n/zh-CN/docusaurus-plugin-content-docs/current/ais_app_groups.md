---
title: "Grupy"
sidebar_label: Grupy
---

视图包含按系统元素分组的集合，我们称之为群组。

## 卡片视图

应用中的群组可以以卡片形式展示，例如天气群组：

![智能家居助手应用](/img/en/frontend/frontend-group.png)

## 特殊群组

我们的组件会自动创建包含子元素的特殊群组。系统中这类群组包括：

### 所有开关

![智能家居助手应用](/img/en/frontend/frontend-group-all-switches.png)

### 所有灯光

![智能家居助手应用](/img/en/frontend/frontend-group-all-lights.png)

### 所有传感器

![智能家居助手应用](/img/en/frontend/frontend-group-all-sensors.png)

## 创建自定义群组

>**您可自主创建定制化群组** 以适配个性化系统界面需求。

群组配置需在系统配置文件中定义。

更多技术细节可查阅Home Assistant平台项目文档的[组件 -> 群组章节](https://www.home-assistant.io/components/group/)：https://www.home-assistant.io/components/group/

智能家居助手中"网络电台"群组的配置示例：

`ais_radio_player.yaml`文件：

```yaml
group:
  Radio Player:
    control: hidden
    name: Radia Internetowe
    entities:
      - input_select.radio_type
      - input_select.radio_station_name
      - input_select.radio_player
```

![智能家居助手应用](/img/en/frontend/frontend-group-radio.png)