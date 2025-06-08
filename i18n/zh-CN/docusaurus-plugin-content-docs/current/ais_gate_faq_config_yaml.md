---
title: "Zaawansowana konfiguracja Asystenta domowego"
sidebar_label: configuration.yaml
---

## 配置文件configuration.yaml

我们致力于让所有基础设置和常用集成都能通过用户界面进行配置。

但目前并非所有功能都支持界面化配置，某些设备集成仍需手动编辑Home Assistant的配置文件。该文件位于设备**/data/data//com.termux/files/home/AIS**目录下，名为**configuration.yaml**。

通过文件手动配置也允许高级用户添加任意自定义组件。

## 传感器示例

下面将逐步演示如何添加显示网关处理器温度的传感器。
当然，您也可以用相同方式添加其他系统元素，并在创建自动化时使用它们。

### Linux系统中的处理器温度

通过搜索引擎查找返回Linux系统CPU温度的命令（google.com），并在控制台进行测试。

```bash
cat /sys/class/thermal/thermal_zone0/temp
```

![](/img/en/bramka/faq_sensor_1.png)

### 编辑configuration.yaml文件

在控制台中进入Home Assistant配置目录。

```bash
cd ~/AIS
```

用您喜欢的文本编辑器打开configuration.yaml文件

```bash
nano configuration.yaml
```

并在文件末尾添加以下配置。

```bash
sensor:
 - platform: command_line
   name: Temperatura CPU
   unit_of_measurement: "°C"
   command: "cat /sys/class/thermal/thermal_zone0/temp"
   value_template: '{{ value | multiply(0.001) | round(1) }}'
```

![](/img/en/bramka/faq_sensor_2.png)

### 检查配置并重启服务

为确保配置正确，请点击系统通用选项中的**检查配置**按钮。然后通过**重新启动**按钮重启服务

![](/img/en/bramka/faq_sensor_4.png)

### 新实体

现在可以在系统实体状态信息中查找到新添加的系统元素（传感器）并查看其状态。

![](/img/en/bramka/faq_sensor_5.png)

### 在应用中显示

所有元素都可以在应用中展示，只需在选定视图上添加并配置包含新组件的卡片即可。

![](/img/en/bramka/faq_sensor_7.png)

![](/img/en/bramka/faq_sensor_6.png)