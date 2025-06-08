---
title: Wbudowane komendy
sidebar_label: Wbudowane komendy
---

家庭助手内置了对话组件，用于处理语音指令。该系统通过将记录的语句/句子转换为意图来实现这一功能。语句中可包含"引号内的变量"及[方括号内的可选词]。这些语句会结合用户先前操作的上下文进行处理，以精准识别用户意图并执行关联操作。

默认支持的语音控制功能包括：

## 设备控制

* **设备开关控制**：

您可以说"打开厨房灯"、"关闭客厅灯光"、"开启外部照明"、"停止草坪灌溉"或"将风扇调至二档"。通过这类指令可控制照明设备与开关装置。

```text
'Włącz "szukana-fraza"'; 'Zapal światło w "szukana-fraza"'
'Wyłącz "szukana-fraza"'; 'Zgaś Światło w "szukana-fraza"'
```

* **设备状态切换**：

使用"切换风扇"等指令可实现设备开关状态反转。该功能特别适用于NFC标签控制场景——通过单个"切换"指令标签即可交替执行"开启"与"关闭"操作。

```text
'Przełącz "szukana-fraza"'
```

* **开启与闭合控制**

支持"打开车库门"、"升起客厅窗帘"或"降下所有遮阳帘"等指令，用于控制电动窗帘与门禁系统。

```text
'Otwórz "szukana-fraza"'; 'Odsłoń "szukana-fraza"'
'Zamknij "szukana-fraza"'; 'Zasłoń "szukana-fraza"'
```

## 音频播放

* **电台播放**

只需说出"播放RMF电台"、"打开Zet广播"或直接说"三台"即可

```text
'Włącz [radio] "szukana-fraza"'; 'Graj "szukana-fraza" radio'
```

* **播客收听**

通过"播放Niebezpiecznik播客"或"打开省钱技巧播客"等指令，系统将自动获取最新期节目并播放

```text
'Podcast "szukana-fraza"'; 'Włącz [podcast] "szukana-fraza"'
```

* **YouTube音乐播放**

使用"播放Maria Peszek的音乐"或"YouTube Brodka"等指令，可自动搜索并播放YouTube平台音乐内容

```text
Włącz [z] [na] YouTube "szukana-fraza"'; 'YouTube "szukana-fraza"'
```

## 播放器控制

* **暂停播放**

支持指令："停止"、"暂停"、"结束"、"取消"、"驻停"

```text
Stop
```

* **恢复播放**
指令："开始"、"播放"、"继续播放"

```text
Graj
```

* **下一首**
指令："[播放] 下一首"、"[播放] 下一曲"、"[开始] 下一首"、"[开始] 下一曲"

```text
Następny
```

* **上一首**
指令："[播放] 上一首"、"[播放] 上一曲"、"[开始] 上一首"、"[开始] 上一曲"

```text
Poprzedni
```

## 传感器状态

您还可以向助手查询系统中任何元素的状态

* **检查传感器数值**

只需询问"客厅温度是多少"或"浴室湿度是多少"，您也可以查询报告外部服务数据的传感器，例如"紫外线指数是多少"或"太阳位置如何"

```text
'[Jaki] [ma] status "szukana-fraza"'
```

* **检查系统中其他任意元素的值**

询问"IP地址是什么"可获取设备IP信息，或"厨房灯状态如何"了解灯光是否开启，或"当前语音是什么"获取助手设置的语音信息

```text
'Jaki jest "szukana-fraza"'; 'Jaka jest "szukana-fraza"''
```

## 信息查询

询问"什么是联合国"或"安杰伊·瓦伊达是谁"，即可从知识库获取简明信息

```text
'Wyszukaj "szukana-fraza"'; 'Znajdź informację o "szukana-fraza"'
```

说出"维基百科 复活节"或"维基百科 波兰"可获取完整的维基百科文章

```text
'Wikipedia "szukana-fraza"'
```

## 时间和日期

当然支持"现在几点"和"今天星期几"这类基础指令

```text
'Godzina'; '[jaka] [jest] data'
```

## 场景激活

可通过"浪漫场景"或"激活观影场景"指令触发预定义场景

```text
'Scena "szukana-fraza"'; 'Aktywuj [scenę] "szukana-fraza"'
```

## 暖气控制

* **设置暖气温度**

说出"厨房暖气21度"

```text
'Ogrzewanie [w] "pomieszczenie" "stopni" stopni[e]'
```

* **切换暖气模式**

说出"暖气切换离家模式"或"暖气切换居家模式"

```text
'Ogrzewanie tryb "nazwa trybu"'
```

其他可选模式（取决于您的暖气配置是否支持）包括：

- "eco" - 节能模式
- "boost" - 快速加热
- "comfort" - 舒适模式  
- "sleep" - 睡眠模式
- "activity" - 活动模式

* **关闭暖气系统**

```text
Wyłącz całe ogrzewnie
```

* **开启暖气系统**

```text
Włącz całe ogrzewnie
```

## 文本广播

如需通过扬声器播报"晚餐已准备好"，只需对助手说："播报 晚餐已准备好"
（后续版本将支持指定播放设备）

```text
Powiedz "szukana-fraza"'; 'Mów "szukana-fraza"'; 'Echo "szukana-fraza"
```

## Spotify控制

若要助手在Spotify搜索并播放Dawid Podsiadło的歌曲，只需说："Spotify Dawid Podsiadło"
同样方式可搜索专辑或播放列表

```text
Spotify "wykonawca/album/playlista"
```

## 拼读功能

可要求助手拼读系统内任意元素状态，指令格式为："拼读 " + 元素名称：

```text
Przeliteruj "nazwa elementu"
```

## 触发自动化流程

可通过以下指令触发预定义的自动化流程：

```text
Jolka "nazwa automatyzacji"
```

或

```text
Uruchom "nazwa automatyzacji"
```

或

```text
Automatyzacja "nazwa automatyzacji"
```

也可为自动化流程名称添加"Jolka: "前缀，助手将识别前缀后的内容为指令。例如命名自动化流程为"Jolka: 浇灌草坪"，当系统收到"浇灌草坪"指令时即会触发该流程。
更多细节参见[自动化中的指令配置](/docs/ais_app_assistent_add_command/#komenda-w-automatyzacji)

## Google Home集成

可配置[Google Home集成](/docs/ais_app_ai_integration_google_home)实现语音指令中转：

```text
Google "komenda/polecenie"
```

## 人员定位查询

可通过指令查询人员位置：

```text
Gdzie jest "osoba"
```

或

```text
Lokalizacja "osoba"
```