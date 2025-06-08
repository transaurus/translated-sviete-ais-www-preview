---
author: Andrzej Raczkowski
authorURL: https://github.com/sviete
authorFBID: 1546384510
title: Wersja systemu 0.83.7  
---

## 系统版本 0.83.7  发布于2018年12月10日

该版本新增功能：

- 新增"播放"语音指令 [指令列表](/docs/ais_app_assistent_commands)
- 集成最新版Home Assistant <a href="https://www.home-assistant.io/blog/2018/11/29/release-83/" target="_blank">0.83</a>，主要新增Fibaro智能中控<a href="https://www.home-assistant.io/components/fibaro/" target="_blank">Fibaro hub</a>的组件支持：
  * Fibaro二进制传感器 https://www.home-assistant.io/components/binary_sensor.fibaro/
  * Fibaro窗帘控制器 https://www.home-assistant.io/components/cover.fibaro/
  * Fibaro灯光控制 https://www.home-assistant.io/components/light.fibaro/
  * Fibaro传感器 https://www.home-assistant.io/components/sensor.fibaro/
  * Fibaro开关模块 https://www.home-assistant.io/components/switch.fibaro/

> **注意：本版本已停用Node-RED服务**，这是由于<a href="https://developers.home-assistant.io/docs/auth_api.html#long-lived-access-token" target="_blank">Home Assistant API访问机制变更</a>，所有API调用需使用令牌签名验证。

如需重新启用Node-RED进程，只需在控制台输入：

```bash
$ pm2 start node-red --name nred --node-args="--max-old-space-size=128"
```

若需实现网关启动时自动运行Node-RED：

```bash
$ pm2 save
```