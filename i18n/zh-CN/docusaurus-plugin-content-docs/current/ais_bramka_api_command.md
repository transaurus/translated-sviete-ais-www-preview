---
title: "Wykonywanie komendy"
sidebar_label: Wykonywanie komendy
---

服务 **ais_ai_service.process** 允许在网关上执行文本命令。
必须参数为 **text**，即问题/指令的文本内容。示例参数值包括：

- 播放RMF电台
- 现在几点
- 天气如何
- 打开厨房灯
- 查找关于北约的信息

调用YouTube音乐播放的`curl`命令示例：

```bash
$ curl -X POST -H "Authorization: Bearer ABCDEFGH" \
       -H "Content-Type: application/json" \
       -d '{"text": "YouTube Pink Floyd the wall"}' \
       http://ais-dom.local:8180/api/services/ais_ai_service/process
```