---
title: "Lokalny serwer z szyfrowaniem"
sidebar_label: HTTPS na bramce
---

## 启用本地加密服务器服务

最简单的方法是启用设备上已安装且默认配置了HTTPS的Caddy服务器（https://caddyserver.com/）。类似地，也可以通过nginx或apache服务器实现，但这些服务器默认未安装（需通过apt包管理器安装）。

以下基于Caddy服务器逐步说明安装流程：

1. 进入[设备控制台](/docs/ais_bramka_remote_ssh)
2. 通过以下命令检查Caddy服务器配置：

```bash
cat $PREFIX/bin/Caddyfile
```

控制台应返回如下响应：

``` bash
$ cat $PREFIX/bin/Caddyfile
:8123 {
    tls /data/data/com.termux/files/home/AIS/servercert.pem /data/data/com.termux/files/home/AIS/privekey.pem
    proxy / localhost:8180 {
        websocket
        transparent
    }
}
```

3. 运行以下命令启动服务器：

``` bash
caddy -conf $PREFIX/bin/Caddyfile
```

控制台应返回如下响应：

``` bash
$ caddy -conf $PREFIX/bin/Caddyfile
Activating privacy features... done.
...
```

4. 在浏览器访问 https://物联网网关IP:8123 验证服务运行状态

5. 若需设置开机自启，将服务添加至PM2进程管理器：

- 在控制台停止当前运行的服务器（步骤3中启动的）按 **Ctrl + c**
- 输入以下命令将服务器注册为守护进程：

``` bash
pm2 start caddy --name https -- -conf "$PREFIX/bin/Caddyfile"
```

- 执行 **pm2 save** 保存配置 - **https** 服务将在网关重启后自动运行

``` bash
pm2 save
```

![](/img/en/iot/bramka_caddy.png)