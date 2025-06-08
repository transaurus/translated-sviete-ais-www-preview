---
title: "Jak dodać Node-RED?"
sidebar_label: Jak dodać Node-RED?
---

## 简介

本文档旨在通过实例说明以下内容：

- 如何在网关上安装额外服务（以Node-RED为例）
- 如何将该服务添加至网关的PM2进程管理器实现开机自启
- 如何为家庭助理界面新增应用视图
- 如何在家庭助手中生成令牌并授权外部应用访问其API
- 如何通过API从Node-RED调用家庭助手的示例服务

![Node-RED](/img/en/faq/node_red_hey_jolka.png)

## Node-RED安装

进入[网关控制台](/docs/ais_bramka_remote_ssh)并输入/粘贴以下命令：

```bash
npm i -g --unsafe-perm node-red && termux-fix-shebang /data/data/com.termux/files/usr/bin/node-red
```

执行效果应如下图所示：

![Node-RED](/img/en/faq/node_red_install.png)

### 启动Node-RED服务

在控制台输入命令：

```bash
node-red
```

执行效果应如下图所示：

![Node-RED](/img/en/faq/node_red_start.png)

此时我们已在网关上完成Node-RED服务的安装和运行。通过浏览器访问 http://网关本地IP:1880 即可使用Node-RED应用

![Node-RED](/img/en/faq/node_red_in_browser.png)

### 停止Node-RED服务

在控制台按下组合键 **Ctrl +c**，效果应如下图所示：

![Node-RED](/img/en/faq/node_red_stop_in_console.png)

### Node-RED服务开机自启

若需实现开机自启，需将该服务添加至PM2进程管理器，在网关控制台输入：

```bash
pm2 start node-red --node-args="--max-old-space-size=128" && pm2 save
```

执行效果应如下图所示：

![Node-RED](/img/en/faq/node_red_start_from_pm2.png)

### 将Node-RED应用添加为家庭助理视图

启用[用户界面配置](/docs/ais_app_ui_config)

添加新的Node-RED视图：

![Node-RED](/img/en/faq/node_red_view.png)

在Node-RED视图中添加IFRAME类型的新卡片

![Node-RED](/img/en/faq/node_red_new_card.png)

在卡片配置中，我们需要输入运行在网关上的Node-RED服务器地址：

![Node-RED](/img/en/faq/node_red_new_card_2.png)

返回视图设置界面，我们可以将视图切换为面板模式（勾选"Panel Mode"选项），这样Node-RED卡片将占据整个视图宽度。

![Node-RED](/img/en/faq/node_red_view_panel_mode.png)

效果应如下图所示：

![Node-RED](/img/en/faq/node_red_in_view.png)

## 连接Node-RED与家庭助理

### 安装家庭助理插件

在控制台中进入node-red目录，通过输入/粘贴以下命令安装"node-red-contrib-home-assistant-websocket"插件：

```bash
cd ~/.node-red
npm install node-red-contrib-home-assistant-websocket
```

效果应如下图所示：

![Node-RED](/img/en/faq/node_red_install_plugin_to_hass.png)

接着通过输入以下命令重启node-red进程：

```bash
pm2 restart node-red
```

效果应如下图所示：

![Node-RED](/img/en/faq/node_red_reset_from_pm2.png)

### 配置与家庭助理的连接

在家庭助理中进入个人资料配置（点击左下角菜单中用户图标），为Node-RED生成长效访问令牌

![Node-RED](/img/en/faq/node_red_long_token.png)

复制生成的令牌（该令牌不会再次显示）：

![Node-RED](/img/en/faq/node_red_long_token_copy.png)

返回Node-RED视图，配置与家庭助理的连接。
从可用组件列表中选择"home assistant" -> "call service"，点击该元素进入连接配置

输入家庭助理的URL地址和上一步生成的令牌。
URL地址：**http://localhost:8180**
令牌：**您在家庭助理中生成的令牌**

![连接家庭助理](/img/en/faq/Node-red-Home-Assistant-connection.png)

点击Node-RED中的**Deploy**按钮，建立与家庭助理的连接。

![连接家庭助理](/img/en/faq/node_red_deploy.png)

### 定义从Node-RED调用家庭助理服务

要调用在家庭助理中定义的服务，请再次点击我们的"call service"元素，并输入/选择以下服务参数：

- 名称：**你好 Jolka**
- 域：**ais_ai_service**
- 服务：**say_it**
- 数据：**"text":"你好 :)"**

![家庭助理连接](/img/en/faq/node_red_home_assistant_service_definition.png)

### 从Node-RED调用家庭助理服务

要手动调用我们的测试服务，首先从列表中添加第一个元素："inject"，然后将我们的节点元素连接起来，得到如下图所示的流程。

![Node-RED](/img/en/faq/node_red_test_call_service.png)

通过**Deploy**按钮保存我们的流程定义，然后点击左侧的"inject"元素手动启动流程：

![Node-RED](/img/en/faq/node_red_call_service.png)

执行后将获得3个结果：

- Node-RED应用中显示流程定义保存成功和服务调用成功的消息（如上图所示）
- 如果网关连接了扬声器或带扬声器的显示器/电视，我们应该能听到助理朗读我们输入的文本**你好 :)**
- 在家庭助理应用中可以看到我们输入的文本已被助理处理

![Node-RED](/img/en/faq/node_red_to_ais.png)