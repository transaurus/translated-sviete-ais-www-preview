---
title: "API systemu"
sidebar_label: API systemu
---

## 简介

RESTful API基于HTTP协议运行。通过该协议的通信主要使用几种标准方法，我们主要使用POST方法（发送数据）和GET方法（获取数据）。Web服务以资源形式提供，可通过HTTP协议调用特定URL地址进行访问。

网关提供两类Web API：

1. **网关原生API**（访问Android系统原生资源）运行在8122端口
2. **Home Assistant/家庭助理标准Web API** 与Web服务器使用相同端口（80和8180，外部访问时为443端口）

:::tip[提示]
所有API接口仅接受和返回JSON编码的对象。

以下示例使用网关本地主机名：ais-dom.local。若您的局域网无法解析该主机名，请改用网关的本地IP地址。
:::

## 网关本地API

当前提供两个资源端点：`http://ais-dom.local:8122/text_to_speech` 和 `http://ais-dom.local:8122/command`

:::caution[注意]
**此API仅限局域网访问，因此无需身份验证和加密。**

从互联网（局域网外）调用网关API需通过家庭助理API实现。此类调用要求身份验证和加密（HTTPS协议）。
完整的网关本地API均可通过家庭助理API访问——具体说明详见下文。
:::

**JSON文本必须使用Unicode编码。默认编码为UTF-8。**

非ASCII字符（如各国语言符号）在发送至API前，应转换为UTF-8编码字符。此类转换通常由REST客户端/程序自动完成。

### /text_to_speech资源

该资源允许通过POST方法向网关发送待朗读文本：

```
curl -v --header "Content-Type: application/json" \
--request POST  \
--data '{"text":"Witaj Jolka"}' \
http://ais-dom.local:8122/text_to_speech
```

可用TTS参数

| Parametr | Domyślna wartość | Opis / Dostępne opcje |
| --- | --- | --- |
| `text` | - | Tekst do przeczytania / Dowolny tekst|
| `pitch` | 1.0  | Ton mowy / 1.0 to normalny ton, niższe wartości obniżają ton syntetyzowanego głosu, większe wartości go zwiększają.|
| `rate` |  1.0  | Szybkość mowy / 1.0 to normalna szybkość mowy, niższe wartości spowalniają mowę (0,5 to połowa normalnej szybkości mowy), większe wartości ją przyspieszają (2,0 to dwukrotność normalnej szybkości mowy).|
| `language` | `pl_PL` | Język / Inne dostępne opcje to uk_UA, en_GB, en_US|
| `path` | - | Ścieżka do zapisu pliku w formacie wav|

为简化操作，**text_to_speech**资源也支持**GET**方法调用——用户只需在浏览器地址栏输入包含待朗读文本的网关地址即可调用API。
使用GET方法时，参数需通过查询字符串(Query string)传递。以下是GET方法调用示例：

- 英语火警通知

`http://ais-dom.local:8122/text_to_speech?language=en_GB&rate=1&pitch=1&text=Attention. Attention. This is Fire alarm! Evacuation on fire route number five in two minutes`

- 乌克兰语休息通知

`http://ais-dom.local:8122/text_to_speech?language=uk_UA&rate=1&pitch=1&text=Ми запрошуємо вас на 30-хвилинну перерву на сніданок. Смачного。`

- 波兰语公告

`http://ais-dom.local:8122/text_to_speech?language=pl_PL&rate=1&pitch=1&text=Mamy więcej zamówień do zrealizowania, prosimy chętnych o pozostanie 2 godziny dłużej w pracy. Płacimy 200% extra。`

Python调用API示例

``` python
import requests
requests.post('http://ais-dom.local:8122/text_to_speech', json={'text':'cześć'})
```

### 资源 /command

该资源允许我们发送待执行命令。示例命令为向网关发送待播放音频：

```
curl -v --header "Content-Type: application/json" \
--request POST  \
--data '{"playAudio": "http://stream3.polskieradio.pl:8080/"}' \
http://ais-dom.local:8122/command
```

可用命令

| Komenda | Przykładowa wartość | Opis |
| --- | --- | --- |
| `playAudio` | `http://stream3.<br/>polskieradio.<br/>pl:8080/` | Odtwarzanie audio/video |
| `stopAudio` | `true` | Zatrzymanie odtwarzacza |
| `pauseAudio` | `true` | Pauza odtwarzacza |
| `setVolume` | `50` | Ustawienie głośności odtwarzacza od 0 do 100 |
| `upVolume` | `true` | Głośniej, to samo co naciśnięcie przycisku w pilocie |
| `downVolume` | `true` | Ciszej, to samo co naciśnięcie przycisku w pilocie |
| `setPlaybackPitch` | `1` | Częstotliwość audio, szczegóły w [dokumentacji PlaybackParams Android] (https://developer.android.com/reference/android/media/PlaybackParams) |
| `setPlaybackSpeed` | `1` | Szybkość odtwarzania |
| `seekTo` | `100` | Przewiń do pozycji w Milisekundach (ms) |
| `skipTo` | `100` | Przeskocz do pozycji w Milisekundach (ms) |
| `tone` | `86` | Odtworzenie tonu , szczegóły w [dokumentacji ToneGenerator Android] (https://developer.android.com/reference/android/media/ToneGenerator) |
| `setPlayerShuffle` | `false` | Odtwarzanie losowe, przydatne przy Spotify |
| `micOn` | `true` | Włączenie mikrofonu |
| `micOff` | `true` | Wyłączenie mikrofonu |
| `addBookmark` | `true` | Dodanie zakładki do odtwarzanych multimediów, przydatne przy audiobookach |
| `goToActivity` | `ActivityMenu` | Przejście do aktywności (ekranu na bramce). Dostępne opcje to:<ul><li>`ActivityMenu` - "Aktywność menu - sterowanie na monitorze",</li><li>`SplashScreenActivity` - "Sterowanie bez monitora",</li><li>`ExoPlayerActivity` - "Aktywność odtwarzacz multimediów",</li><li>`ConsoleActivity` - "Konsola Asystenta domowego", </li><li>`AndroidSettingsActivity` - "Ustawienia systemu Android",</li><li>`SettingsActivity`  - "Ustawienia Serwisu Asystent domowy na bramce",</li><li>`FilesActivity` - "Aplikacja menedżer plików na bramce",</li><li>`AndroidWifiActivity` - "Ustawienia WiFi w systemie Android",</li><li>`SpotifyActivity` - "Przejście do aplikacji Spotify"</li></ul>  |
| `showCamera` | `{"streamUrl": "rtsp://192.168.2.38/unicast", "haCamId": "camera.domek"}` | Wyświetlanie wideo (obraz i dźwięk) z kamery w aktywności. W parametrze haCamId podajemy identyfikator camery w Asystencie domowym - z tym identyfikatorem zostaną zgłoszone zdarzenia naciśnięcia przycisków (otwieranie drzwi/bramy) w systemie. |

## Home Assistant的RESTful API

家庭助理在80和8180端口提供Web服务

* http://ais-dom.local:8180/ 这里是系统控制应用程序
* http://ais-dom.local:8180/api/ 这里是RESTful API接口

### 在应用程序中调用/测试服务

:::tip[提示]
要查看应用程序中的可用服务，请从主菜单进入`开发者工具`->`服务`。您可以在此处调用/测试网关上的任何可用服务。
:::

:::important[重要信息]
应用程序中每项服务包含：
- 描述
- 参数列表（参数名、描述及示例值）

因此文档中不再详细描述服务，仅提供示例调用。
:::

调用/测试服务步骤：

1. 使用`管理员`权限登录家庭助理应用
2. 进入`开发者工具`->`服务`
3. 从列表中选择要调用的服务
4. 以JSON或YAML格式提供参数
5. 点击"调用服务"按钮

JSON格式参数示例：

```json
{"text": "Cześć, jak się masz?"}
```

YAML格式等效参数：

```yaml
text: "Cześć, jak się masz?"
```

![服务](/img/en/frontend/services_1.png)

:::tip[提示]
网关的完整API（上文详述）可通过`ais_ai_service.publish_command_to_frame`服务在家庭助手中访问。

这使得我们也能以安全方式（加密和令牌认证）从外部调用网关API。
:::

![服务](/img/en/frontend/services_2.png)

### 使用curl调用服务

:::important[重要信息]
若要从外部系统调用家庭助理的API，我们需要一个访问令牌。
首先在应用程序中生成一个长期有效的访问令牌(long-lived access token)，该令牌有效期为10年。
:::

#### 生成访问令牌

在应用程序中进入个人资料页面，滚动至页面底部并选择`创建令牌`：

![令牌](/img/en/frontend/tokens_1.png)

输入令牌名称：

![令牌](/img/en/frontend/tokens_2.png)

复制令牌：

![令牌](/img/en/frontend/tokens_3.png)

:::caution[注意]
无法再次查看令牌值，因此请将其复制到安全位置。

如需撤销API访问权限，请删除该令牌。
:::

![令牌](/img/en/frontend/tokens_4.png)

#### 对/api/资源执行GET方法

检查/api/是否可用以及身份验证是否正常工作。

```bash
curl -v -H "Authorization: Bearer TOKEN-DOSTĘPU" \
       -H "Content-Type: application/json" http://ais-dom.local:8180/api/
```

若API正常运行，将返回以下响应：

```json
{"message": "API running."}
```

### 对/api/services/&lt;domain>/&lt;service>执行POST方法

网关上的组件会公开其服务。这些组件服务既可以在系统发生特定事件时自动触发，也可以通过API从外部系统调用。

使用curl调用网关文本朗读服务的示例：

```bash
curl -X POST -H "Authorization: Bearer TOKEN-DOSTĘPU" \
       -H "Content-Type: application/json" \
       -d '{"text": "Cześć! Jak się masz?"}' \
       http://ais-dom.local:8180/api/services/ais_ai_service/say_it
```