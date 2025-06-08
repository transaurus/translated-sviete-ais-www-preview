---
title: S26, inteligentne gniazdo WiFi
sidebar_label: Inteligentne gniazdo WiFi
---

## 描述

1. 擦除所有闪存并将参数重置为固件默认值，但保留Wi-Fi设置并重启
Reset 5


2. 添加新设置
Backlog ssid2 8DB0839D; password2 094FAFE8; SetOption57 1; SetOption3 0; WifiConfig 4

SetOption3 0 - 禁用MQTT
WifiConfig 4 - 禁用Wi-Fi配置但会尝试其他接入点而不重启
SetOption57 - 每44分钟重新扫描Wi-Fi网络，若检测到信号强度+10dB更强的网络则切换（仅限可见网络）

LedPower - LED电源状态开关
0 = 关闭LED并设置LedState 0
1 = 开启LED并设置LedState 0
2 = 切换LED状态并设置LedState 0
（使用Backlog LedPower 0; SetOption31 1可禁用LED，即使Wi-Fi或MQTT未连接时也生效）

SetOption31 - 在Wi-Fi和MQTT连接问题期间禁用状态LED闪烁。此功能需将LedPower设置为0才能生效。
0 = 启用LED闪烁（默认）
1 = 禁用LED闪烁