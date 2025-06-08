---
title: "Sterowanie z AIS"
sidebar_label: Sterowanie z AIS
---

## 描述

音频放大器板通过TTL串口与AIS家庭网关连接，这使得我们可以通过家庭助手控制音频放大器（均衡器和蓝牙音频模块）。

## 通过应用程序控制播放器

以这种方式连接到网关的扬声器可通过应用程序进行控制：

![|624x301](https://lh4.googleusercontent.com/SgDKRIgFL7uAmm6cJBoGRz-D9B6YOYctD2Lo6jyAL-vHkgjcKf8HGMAXREvxlcurOZi5zatJODrGezH-257j39LIjoJPRVO6eFgVU9jBjvhB5P4Lcz4gcopy5QGvdmwzCcFcGp_B)

也可将其选作播放媒体库内容的默认扬声器：

![|624x271](https://lh5.googleusercontent.com/CzJlEQfKaFKfdsANUzk3UhFHxXPeH-yi57YX0tPF8fXNGf_WWPZkJi9F2EsNYZ_j7q196ys5FdEJGBFiuLv4GTfa6F1pF9V2oXgyyf1gROPS6psQ55S8JAjPWNlRxEhpadJkY8NJ)

涉及音频控制的语音指令默认作用于连接到网关的扬声器。

![|624x372](https://lh6.googleusercontent.com/LCoyXBIiz9IhySLsVMgvF3_aRo9jx_b8eSG4q0z2a88bTc3TmAdMNa1VcTJRXLZXDhSDaa_kpET8pYR71MBRAOIYtN9zeqTlGRu15fpkKB2_HVHRCK7sSqabiGlD0J4NRGUDsp3t)

## 通过应用程序控制均衡器

在扬声器详情页中，可选择音频板支持的9种音效模式

![|624x379](https://lh6.googleusercontent.com/RLITeT3QE9qpkVigdX46d7oQMXOJYFCAkK_zdh_qX72Tvu7nxG7gEJ2wvQks_tMVv2_bw0izaHJNFejrCWqR0WrNnZJyUU0wRxpKmi9m4w6nLYi1o-FYPmLIRNi8xq0cjdpCz4Fx)

## 通过应用程序API控制音频板

在开发者工具中，我们提供了ais_amplifier_service集成服务，用于与音频板通信——通过TTL接口向音频板发送指令。

![|624x368](https://lh3.googleusercontent.com/Qj6yc_l7UgZSG59Vky7sOCkpv4u0KjlM6lBmzCLawHcC0544-a2oR-Sb6_BJYOA6aPwLhZcBTcoOKwLSGTuvuD-PaD2k4puC3zHYzjveTnhc4E7WRNS-mx3-zIQF9wgttNiIO2id)

ais_amplifier_service.change_work_mode服务允许切换扬声器模式，支持AUX或BT模式：

![|624x299](https://lh6.googleusercontent.com/3PFL8bi-luUbhf_6ay-jAysIHogqlKU8IbdHOYc3LDESNg1rXKk6zOpWjLl6XWhvWE9haIOLuPOOAE-yBmwQfaVXucja5tC2gDFCdRtoe3Ri9XoGujGD4mYZH8ATLZoLHB7RM7gD)

ais_amplifier_service.exec_command服务支持通过TTL接口向音频板发送任意控制指令：

![|624x331](https://lh4.googleusercontent.com/22tYXfNYZKfsl5dtFrQsxAalWysBR-gxgT_KxMxEYvyGVhE_4SpqKMuDgvDSrXALrEhGANDQ04Wx1WI4Ka7ph8ZUUogIZk-zs2Rc1SHBdV749SEdXAT-uvg6X_k99y-9CTs9GcGm)

## 完整指令列表

完整指令列表可在我们的GitHub仓库查看：https://github.com/sviete/BK3266

![|624x523](https://lh3.googleusercontent.com/Sq9rvuSQX1fjqvne9khXxe_EHNJaeslIuF-JRkf7lPxypZu6lPbUN5S3DLHSIMT0JtoHyxWR-E_DM9KsMTKBM34senx0PUS9HI6P4JftVv_vYyCYKjzzB3TsHXUWpWWt8qw6Et6a)

部分指令涉及FM收音机功能或控制从SD卡/USB存储器直接播放音频（需插入音频板）——由于实际使用场景中从未需要这些功能，我们未对其进行测试。

音频板上虽预留麦克风接口，但BK3266芯片是否支持麦克风功能尚不明确（博通公司未在官网更新BK3266的相关技术文档）。在与博通公司的技术沟通中，我们也未能获取软件层控制麦克风的具体方案，因此未将麦克风功能集成至DEV KIT SPEAKER 1开发套件中。