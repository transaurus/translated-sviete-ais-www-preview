---
title: ""
sidebar_label: Opis produktu AIS-Adapter-1
---

## Zigbee 3.0 适配器

![ais](/img/AIS-ADAPTER-1/bramka.png)

**AIS-adapter-1** 作为Zigbee适配器，支持通过以太网或WiFi传输Zigbee数据包。该适配器可实现不同厂商设备（如涂鸦、宜家、小米、Gledopto、Moes、Sonoff等）的统一集成。

**AIS-adapter-1** 的核心优势在于：支持128个Zigbee设备同时在线、覆盖范围达200米，并能通过LAN网线接入本地网络，从而确保家庭自动化系统与Zigbee网络的稳定可靠连接。

**适配器特性**：

- 支持128个子设备接入
- 覆盖范围超过200米
- 采用USB-C供电（随附线缆）
- 可通过WiFi或10/100 Mbps LAN网线接入本地网络（随附线缆）
- 兼容ZigBee 3.0智能产品（如传感器、灯具、开关等）
- 基于高性能Espressif ESP32芯片运行，可扩展支持蓝牙LE网关功能*
- 采用EFR32MG21射频芯片，可同步支持Zigbee和Thread(Matter)无线通信协议*

``*`` - 需通过固件升级实现

## 技术规格

高性能ESP32芯片负责适配器通信（WiFi和以太网），同时运行适配器配置软件。芯片资源占用约25%，由于ESP32支持蓝牙LE，未来可扩展蓝牙网关功能。

![esp](/img/AIS-ADAPTER-1/esp.png)

Zigbee通信由**EFR32MG21A020F768IM32**芯片实现，该芯片基于80MHz主频的ARM Cortex-M33内核，配备768kB闪存和64kB RAM，射频模块最大输出功率20dBm。其多协议2.4GHz 802.15.4射频模块可同步支持Zigbee 3.0（EmberZNet/EZSP）和Thread/Matter（OpenThread/Spinel）传输，为未来支持双模协议奠定基础。

![efr](/img/AIS-ADAPTER-1/efr.png)

**AIS-adapter-1 技术参数**

- 输入电压：AC 100 ~ 240V 50 / 60Hz
- 芯片：ESP32 和 EFR32MG21
- 支持协议：Zigbee 3.0、WiFi 2.4GHz、以太网、蓝牙低功耗（BLE）
- 无线频率：IEEE 802.11b/G/n 2.4G
- 工作温度：-10 ~ 55 ℃
- 外壳材质：ABS + PC
- 产品尺寸：95*95*22.5mm（含随附线缆）

## 兼容性

**AIS-adapter-1** 兼容 Home Assistant 内置的 [Zigbee Home Automation](https://www.home-assistant.io/integrations/zha/) 集成以及 [Zigbee2mqtt](https://www.zigbee2mqtt.io/) 方案，因此可适配所有主流智能家居系统。设备开箱即用，只需接入局域网和电源即可运行。我们在适配器软件中提供了ZHA和Z2M的配置生成器，使得集成过程仅需点击操作并复制生成的配置文件。

![efr](/img/AIS-ADAPTER-1/ha.png)

## 软件系统

设备运行的软件由我们持续开发维护，代码已开源至 [Github](https://www.github.com/sviete) 仓库。下文将介绍软件的核心功能模块。

![about](/img/AIS-ADAPTER-1/about.png)

在`General`选项卡中，可选择适配器工作模式（默认为``LAN模式``或``WiFi模式``），并可配置LED指示灯开关状态。

![general](/img/AIS-ADAPTER-1/general.png)

`Ethernet`菜单提供有线网络参数配置界面。

![ethernet](/img/AIS-ADAPTER-1/ethernet.png)

`WiFi`菜单用于配置无线网络连接参数。

![wifi](/img/AIS-ADAPTER-1/wifi.png)

`Z2M and ZHA`选项卡包含串行通信端口设置（用于与外部系统通信）以及Home Assistant和Zigbee2Mqtt的配置生成器。

![ha](/img/AIS-ADAPTER-1/z2m.png)

`Security`选项卡提供设备安全设置功能，可设置管理员密码并阻止未经授权的配置访问。

![ha](/img/AIS-ADAPTER-1/security.png)

`System Control`菜单支持修改设备网络标识名称及执行设备重启操作。

![ha](/img/AIS-ADAPTER-1/system_control.png)

`System tools`选项卡提供系统更新、配置文件查看编辑以及Zigbee通信控制台功能。

![ha](/img/AIS-ADAPTER-1/system_tools.png)

## 可用性与价格

:::warning[商店]
<center>
<button className="snipcart-add-item button button--outline button--secondary button--lg"
              data-item-id="ais-adapter-1"
              data-item-description="AIS ADAPTER 1, Zigbee 3.0 Adapter {info} urządzeń zigbee (będących jednocześnie online), ma zasięg 200 metrów i działa w sieci LAN."
              data-item-image="/img/ais_adapter_1.png"
              data-item-name="AIS ADAPTER 1"
              data-item-price="{&quot;usd&quot;:45,&quot;eur&quot;:40, &quot;pln&quot;: 179}"
              data-item-custom1-name="Wiadomość"
              data-item-custom1-type="textarea"
              >
              加入购物车  
            </button>
[该设备也可在我们的Allegro平台店铺购买](https://allegro.pl/uzytkownik/AI-Speaker)
<br/>
[<img src="/img/allegro.png" alt="drawing" width="200"/>](https://allegro.pl/uzytkownik/AI-Speaker)
</center>
:::