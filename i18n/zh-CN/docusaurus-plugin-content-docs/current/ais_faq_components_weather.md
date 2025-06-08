---
title: "Jak dodać własny serwis Pogodowy?"
sidebar_label: Własny serwis Pogodowy
---

当前家庭助理系统在出厂默认配置中提供来自两个数据源的天气信息：

- [Dark Sky天气服务](https://darksky.net/dev) - 该服务提供您所在位置的描述性天气预报。当询问助手天气状况时，返回的描述性天气信息即源自此服务
- [Open Weather Map服务](https://openweathermap.org/) - 该服务提供您所在位置的实时气象数据，这些数据会显示在应用的天气视图界面中

## 地理位置设置

默认情况下天气数据根据网关定义的位置获取。为获得更精准的天气数据，需在系统中设置您的具体位置。位置信息通过以下配置项定义：

![地理位置设置](/img/en/frontend/gps_settings.png)

## 自定义天气数据服务

您可更换天气数据提供商，只需从[Home Assistant Weather](https://www.home-assistant.io/components/#weather)提供的数十个预制天气组件中选择并配置即可
（当然也可自行实现天气数据组件，但这属于高阶选项且需要Python编程能力）。

以下我们将逐步演示如何添加Dark Sky天气服务数据，其他服务的添加方式可参照此流程。

### Dark Sky - API密钥获取

需申请免费的API密钥（需注册）。免费版每日最多可调用1000次接口。

> **注意** 若您已绑定信用卡且日调用量超过1000次，Dark Sky将按每次0.0001美元的标准计费。

注册地址：[Dark Sky API](https://darksky.net/dev)

### Dark Sky - 配置方法

将以下配置添加至configuration.yaml文件以启用Dark Sky：

`configuration.yaml`:

```yaml
# Przykład z configuration.yaml
weather:
  - platform: darksky
    api_key: TWOJ_KLUCZ_API
```

详细配置说明参见：[Home Assistant, Dark Sky](https://www.home-assistant.io/components/weather.darksky/)

### Dark Sky - 视图集成

要使新添加的天气服务数据显示在应用天气视图中，需覆盖默认的天气组定义。

组/视图的覆盖配置通过groups.yaml文件实现，该文件位于网关设备上，与主配置文件configuration.yaml处于同一配置目录。

系统在基础配置中提供的默认天气视图定义如下：

```yaml
# Domyślna definicja widoku pogody w aplikacji
pogoda:
  name: Pogoda
  view: yes
  icon: mdi:weather-partlycloudy
  entities:
    - weather.openweathermap
    - sensor.dark_sky_hourly_summary
    - sensor.dark_sky_daily_summary
```

要使用自定义配置覆盖默认定义，只需在groups.yaml文件中添加相应条目即可。
以下示例包含完整的基础配置以及我们新添加的Dark Sky天气组件（参见最后一行）：

`groups.yaml`:

```yaml
# Zmodyfikowana definicja widoku pogoda w aplikacji
pogoda:
  name: Pogoda
  view: yes
  icon: mdi:weather-partlycloudy
  entities:
    - weather.openweathermap
    - sensor.dark_sky_hourly_summary
    - sensor.dark_sky_daily_summary
    - weather.dark_sky
```

重启应用后，天气视图将显示来自两个天气服务的数据：

![家庭助理应用天气视图](/img/en/frontend/frontend-weather.png)