---
title: "Obsługa kart dźwiękowych"
sidebar_label: Obsługa kart dźwiękowych
---

### 简介

> 描述内容准备中

### 显示所有音频设备

通过控制台命令可列出系统中所有可用音频设备（已连接且驱动安装完毕）：

```bash
cat /proc/asound/cards
```

输出结果应类似如下所示：

```bash
$ cat /proc/asound/cards
 0 [AMLM8AUDIO     ]: AML-M8AUDIO - AML-M8AUDIO
                      AML-M8AUDIO
 1 [CameraB409241  ]: USB-Audio - USB Camera-B4.09.24.1
                      OmniVision Technologies, Inc. USB Camera-B4.09.24.1 at usb-xhci-hcd.0.auto-2, h
 2 [dabaizhiyin16k1]: USB-Audio - dabaizhiyin16k16b
                      dabaizhiyin dabaizhiyin16k16b at usb-xhci-hcd.0.auto-1.3, full speed
```

### 音频设备测试

```bash
$ su -c 'tinymix -D 0'
```

> 待完善