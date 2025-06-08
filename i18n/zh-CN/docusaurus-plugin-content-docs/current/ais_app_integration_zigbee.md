---
title: "Zigbee2MQTT"
sidebar_label: Zigbee
---

## 简介

家庭助理中的Zigbee集成功能让您无需使用厂商网关即可便捷使用Zigbee设备。该解决方案基于[Zigbee2MQTT](https://www.zigbee2mqtt.io/)项目开发，并与我们的软件深度集成，使您能轻松将Zigbee设备接入家庭助理智能家居生态系统。

![CC2531](/img/en/frontend/ais_zigbee_web_app2.png)

## 集成方式

只需将[预先刷写好的适配器](/docs/ais_zigbee_index)插入USB端口，家庭助理将自动识别该USB设备，语音提示Zigbee服务启动，并在配置界面自动显示添加Zigbee设备的选项。

## 支持设备

我们支持Zigbee2MQTT项目列出的所有设备，根据Zigbee2MQTT官网信息[截至2021年6月已支持230个厂商的1490余款设备](https://www.zigbee2mqtt.io/information/supported_devices.html)。该项目发展迅速，新设备正在持续增加中。

## 添加新Zigbee设备

### 允许设备入网

为确保Zigbee网络安全并避免其他设备误接入，默认配置中**enable_join**参数设为false。

添加新设备前需在应用中临时开启配对模式，否则新设备将无法加入网络！进入zigbee2mqtt配置界面后，选择**配置**->**Zigbee设备配置**开启临时配对功能。

![Zigbee集成](/img/en/frontend/zigbee2mqtt_ais_dom_1.png)

随后点击**permit join**按钮授权新设备接入

![Zigbee集成](/img/en/bramka/zigbee_integration_enable_join.png)

### 配对操作

首先在Zigbee2MQTT官网的[支持设备列表](https://www.zigbee2mqtt.io/information/supported_devices.html)中查询选定型号的具体配对说明。

![Zigbee集成](/img/en/bramka/zigbee_integration_pair.png)

![Zigbee集成](/img/en/bramka/zigbee_integration_pair2.png)

若无相关说明，通常可通过恢复出厂设置完成配对

### 网络拓扑图

设备配对完成后，我们可以刷新Zigbee网络拓扑图页面，查看新设备已接入网关的状态

![Zigbee集成](/img/en/bramka/zigbee_integration_pair_device_map.png)

### 修改设备名称

![Zigbee集成](/img/en/bramka/zigbee_integration_change_name.png)

### 设备控制

新设备将自动出现在设备列表中

![Zigbee集成](/img/en/bramka/zigbee_integration_new_device.png)

选择设备后可查看详细信息并配置自动化规则

![Zigbee集成](/img/en/bramka/zigbee_integration_new_device_info.png)

新实体可添加至控制面板并用于自动化场景，具体案例将发布在[社区论坛](https://ai-speaker.discourse.group/)

-----------------------------------------------------

## 技术信息

### Zigbee进程

网关进程由[PM2进程管理器](http://pm2.keymetrics.io/)管控。PM2在检测到CC2531设备后会自动启动zigbee进程，并持续监控其运行状态。

查看zigbee进程状态需在终端输入：

```
pm2 show zigbee
```

![zigbee](/img/en/bramka/pm2_zigbee.png)

### 应用与二进制文件

zigbee进程基于[zigbee2mqtt](https://www.zigbee2mqtt.io/)应用运行，该应用依赖[nodejs-lts](https://nodejs.org/en/)环境

我们编译的nodejs二进制包托管在[bintray仓库](https://bintray.com/sviete/ais/nodejs-lts)

![zigbee](/img/en/bramka/nodejs_binary.png)

### 本地访问

该应用运行在**8099**端口，局域网内可通过浏览器访问``http://<网关IP>:8099``

![zigbee](/img/en/bramka/app_zigbee2mqtt.png)

### 远程访问

我们通过ais_proxy组件实现zigbee2mqtt网页端的远程访问，该功能需先登录家庭助理系统，采用[ingress](https://kubernetes.io/docs/concepts/services-networking/ingress/)机制实现

![zigbee](/img/en/bramka/app_zigbee2mqtt_proxy.png)

### 自动更新

Zigbee2Mqtt作为家庭助理系统的组件提供。**升级至最新稳定版Zigbee2Mqtt**可通过用户界面自动完成，该过程会从我们的OTA服务下载并解压预编译的Zigbee2Mqtt软件包到网关上。

![zigbee](/img/en/bramka/zigbee2mqtt_upgrade.png)

### 手动更新/安装

:::caution[注意]
**警告！** 手动更新是面向开发者和高级技术用户的复杂流程。若手动更新后出现问题，建议[执行应用完全重置](/docs/ais_bramka_reset_ais_step_by_step)
:::

如需安装Zigbee2Mqtt开发版以支持新设备或测试新功能，可通过控制台手动操作。手动安装需从GIT仓库拉取Zigbee2Mqtt代码，随后在网关上运行应用程序依赖项的安装流程。下方提供带步骤说明的bash脚本（需在控制台执行）。

``` bash
echo "Zatrzymanie serwisu zigbee..."
pm2 stop zigbee

echo "kopia konfiguracji zigbee..."
cp -R ~/zigbee2mqtt/data/configuration.yaml ~/configuration.yaml

echo "Usuwamy bieżącą wersję zigbee2mqtt..."
rm -rf ~/zigbee2mqtt

echo "Kolonujemy kody najnowszej wersji..."
git clone --depth=1 https://github.com/Koenkk/zigbee2mqtt.git

echo "Przechodzimy do folderu z kodami zigbee2mqtt..."
cd ~/zigbee2mqtt

echo "Przełączamy się na wersję kodu zigbee2mqtt który chcemy uruchomić..."
git checkout HEAD -- npm-shrinkwrap.json
git pull

echo "Instalujemy zależności..."
npm ci --unsafe-perm

echo "Przywracamy konfigurację zigbee2mqtt..."
cp ~/configuration.yaml ~/zigbee2mqtt/data/configuration.yaml
rm ~/configuration.yaml

echo "Uruchomienie serwisu zigbee2mqtt..."
pm2 start zigbee

```

### 配置

Zigbee2Mqtt配置文件位于网关的``~/zigbee2mqtt/data/configuration.yaml``路径下

:::caution[注意]
**警告！** 基础配置中默认参数已优化，通常无需修改。仅建议需要调整MQTT broker连接参数（如添加认证等）的开发者或高级用户更改配置。若配置变更后出现问题，建议[执行应用完全重置](/docs/ais_bramka_reset_ais_step_by_step)
:::

配置文件可通过应用界面编辑：进入设备配置后选择Zigbee设备配置项：

![zigbee](/img/en/integrations/zigbee2mqtt_go_to_configuration_yaml.png)

随后在右上角下拉菜单中选择"编辑Zigbee2Mqtt configuration.yaml"
![zigbee](/img/en/integrations/zigbee2mqtt_configuration_yaml.png)

![zigbee](/img/en/integrations/zigbee2mqtt_configuration_file.png)

标准配置文件路径为``~/zigbee2mqtt/data/configuration.yaml``。根据使用的适配器类型，配置存在差异：

- PRO版Zigbee适配器ConBee2

``` yaml
# configuration.yaml Zigbee2MQTT v 1.19.1   
homeassistant: true
permit_join: false
mqtt:
  base_topic: zigbee2mqtt
  server: 'mqtt://localhost'
serial:
  adapter: deconz
  port: /dev/ttyACM0
frontend:
  port: 8099
advanced:
  log_level: info
  log_output:
    - console
  channel: 11
```

- DEV版Zigbee适配器USB CC2531

``` yaml
# configuration.yaml Zigbee2MQTT v 1.19.1   
homeassistant: true
permit_join: false
mqtt:
  base_topic: zigbee2mqtt
  server: 'mqtt://localhost'
serial:
  adapter: zstack
  port: /dev/ttyACM0
frontend:
  port: 8099
advanced:
  log_level: info
  log_output:
    - console
  channel: 11
```