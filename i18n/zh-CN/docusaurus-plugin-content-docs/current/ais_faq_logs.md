---
title: "Logi dostępne na bramce"
sidebar_label: Logi dostępne na bramce
---

## 简介

当设备运行异常、更新故障或自定义集成/组件出现问题时，建议通过检查日志进行故障诊断。可通过SSH连接控制台查看日志，[SSH连接方法详见此处](/docs/ais_bramka_remote_ssh)。下文将介绍如何查看系统各组件的日志信息。

## 家庭助理进程日志

网关进程由<a href="http://pm2.keymetrics.io/" target="_blank">PM2进程管理器</a>控制。PM2负责管理核心应用程序状态，在系统启动时加载进程，并持续监控其运行状态。

查看进程状态的控制台命令：

```bash
pm2 status
```

![PM2](/img/en/bramka/pm2_console.png)

### 实时日志查看

实时查看所有进程最近15行日志的命令：

```bash
pm2 logs
```

![PM2](/img/en/bramka/pm2_console_logs.png)

实时查看MQTT服务器最近20行日志的命令：

```bash
pm2 logs mqtt --lines 20
```

### 日志文件

进程日志文件存储路径：**/data/data/com.termux/files/home/.pm2/logs/**

![PM2](/img/en/bramka/pm2_console_logs_files.png)

可将目标日志文件复制至**/sdcard**目录后通过FTP客户端下载：

控制台复制文件命令：

```bash
mkdir /sdcard/logs
cp /data/data/com.termux/files/home/.pm2/logs/* /sdcard/logs
```

网关FTP连接方法：
[通过FTP连接控制台](/docs/ais_bramka_remote_ftp)

## 系统更新日志

更新日志[可通过网页应用查看](/docs/ais_bramka_update_logs)

也可通过控制台访问，路径为**/data/data/com.termux/files/home/AIS/www**目录下的**upgrade_log.txt**文件。可使用Linux标准命令查看该文件内容，例如**cat**命令：

```bash
cat /data/data/com.termux/files/home/AIS/www/upgrade_log.txt
```

也可使用**tail -f**命令实时监控更新进度：

```bash
tail -f /data/data/com.termux/files/home/AIS/www/upgrade_log.txt
```

## Android系统日志

通过**logcat**命令可实时查看Android系统日志：

```bash
logcat
```

![Logcat](/img/en/bramka/console_logcat.png)

## Linux内核日志

使用 **dmesg** 命令可以查看 Linux 内核日志

```bash
dmesg
```

![dmesg](/img/en/bramka/console_dmesg.png)

## Linux 系统进程

可通过 **htop** 命令查看 Linux 系统进程

```bash
htop
```

![dmesg](/img/en/bramka/console_htop.png)