---
title: "Usługi działające na bramce"
sidebar_label: Lokalne Usługi bramki
---

## 网关运行服务

网关上默认运行以下服务：

| Nazwa         | Protokół | Porty           | Komenda/URL                                            | Opis                             | Bramka                                                                                    |
| ------------- | -------- | --------------- | ------------------------------------------------------ | -------------------------------- | ----------------------------------------------------------------------------------------- |
| Aplikacja AIS | http     | **80** / `8180` | [http://ais-dom.local](http://ais-dom.local)           | serwer http                      |     |
| FTP           | ftp      | **21** / `1024` | [ftp://ais-dom.local](ftp://ais-dom.local)             | serwer ftp                       |     |
| SSH           | ssh      | **22** / `8022` | `ssh ais-dom.local`                                    | serwer ssh                       |     |
| MQTT          | mqtt     | **1883**        | `mosquitto_sub -h ais-dom.local -t '#'`                | serwer mqtt                      |     |
| Terminal      | http     | **8888**        | [http://ais-dom.local:8888](http://ais-dom.local:8888) | powłoka bash w aplikacji webowej |     |
| Zigbee        | http     | **8099**        | [http://ais-dom.local:8099](http://ais-dom.local:8099) | aplikajca zigbee2mqtt            |     |
| Rest API      | http     | **8122**        | [http://ais-dom.local:8122](http://ais-dom.local:8122) | api bramki                       |     |
| ADB           | tcp/ip   | **5555**        | `adb ais-dom.local`                                    | android debug bridge             |     |
| WebCmd           | http  | **8000**  |[http://ais-dom.local:8000](http://ais-dom.local:8000)                                   | menedżer plików            | 
| ScreenStream           | http  | **9966**  |[http://ais-dom.local:9966](http://ais-dom.local:9966)                                   | android device screen             |    |
| Zwave         | http     | **8091**        | [http://ais-dom.local:8091](http://ais-dom.local:8091) | aplikajca zwavejs2mqtt           |   |
| PostgreSQL    | tcp/ip   | **5432**        | `psql ha`                                              | relacyjna baza danych            |  |
| SIP Proxy     | udp      | **5060**        |                                                        | serwer udp sip                   |  |

## 实用链接

网关运行服务的链接及其他实用链接可通过应用程序获取，只需在菜单中选择**实用链接**选项

![实用链接](/img/en/bramka/ais_gate_links.png)