---
title: "Sterowanie diodą LED"
sidebar_label: Sterowanie diodą LED
---

服务 **ais_shell_command.led** 可用于控制设备正面的LED指示灯。
需要传入一个参数 **brightness**，参数示例如下：

- 0 - 红色，
- 255 - 蓝色，
- timer - 启用闪烁功能，
- heartbeat - 启用心跳呼吸灯功能

例如，若要让LED呈现心跳节奏的呼吸效果，需调用ais_shell_command.led服务并传入以下参数：

```JSON
{"brightness": "heartbeat"}
```

![网络设置](/img/en/frontend/services_led.png)