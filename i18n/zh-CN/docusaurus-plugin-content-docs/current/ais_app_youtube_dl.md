---
title: "YouTube"
sidebar_label: Muzyka z YouTube
---

## YouTube

YouTube是目前互联网上最大的免费音乐服务平台。我们可以播放几乎任何音频内容，只需说出***YouTube 搜索关键词***即可。

![AIS News](/img/en/frontend/ais_integration_yt.png)

## 遥控器控制

也可以通过我们专用的[收音机遥控器](/docs/ais_remote_index)启动YouTube搜索（无需屏幕应用程序）。使用遥控器时，可以通过[语音指令](/docs/ais_app_assistent_commands)进行语音搜索，或通过虚拟键盘及字母输入朗读功能实现。

## 技术信息

### YouTube API

我们在设备上提供了与YouTube服务的集成。使用官方且目前免费的[API v3](https://developers.google.com/youtube/v3/getting-started)在该平台进行音频搜索。

### youtube-dl

通过[youtube-dl](https://github.com/ytdl-org/youtube-dl/)播放API检索到的内容，这是一个支持从[数百个网站](http://ytdl-org.github.io/youtube-dl/supportedsites.html)播放/下载音视频的热门工具。

:::caution[注意]
youtube-dl曾因版权侵权投诉被微软在Github上短暂封禁。这引发了广泛争议，并激起了一场辩论——是否可以在自有应用中展示互联网上免费公开的内容？

我们当时在AI-Speaker论坛声明：若youtube-dl确实构成版权侵权，我们将立即移除该集成方案。

最终youtube-dl代码库获得解封，微软在博客中澄清投诉缺乏依据[《力挺开发者：youtube-dl回归》](https://github.blog/2020-11-16-standing-up-for-developers-youtube-dl-is-back/)。

**我们确保AI-Speaker所有代码、解决方案和集成均100%合法。若youtube-dl或任何组件被认定侵权，我们将立即从系统中移除该组件。**
:::