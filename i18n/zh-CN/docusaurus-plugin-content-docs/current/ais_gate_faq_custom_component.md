---
title: "Własny komponent w Asystencie domowym"
sidebar_label: Własny komponent w Asystencie domowym
---

## 添加自定义组件的目的

您已搜索了1700个现成组件却仍未找到与设备兼容的集成方案？现有功能未能完全满足需求且您有优化方案？开源项目的核心优势在于代码可访问性和可定制性——现在正是编写首个集成代码的最佳时机。

下文将逐步演示如何为家庭助理添加最基础的定制组件。更详尽的集成案例可参阅<a href="https://github.com/home-assistant/example-custom-config/tree/master/custom_components/" target="_blank">Home Assistant官方自定义组件示例库</a>

## 自定义组件目录

通过终端进入家庭助理配置目录

```bash
cd ~/AIS
```

创建custom_components文件夹

```bash
mkdir custom_components
```

在custom_components目录下新建组件文件夹（例如命名为**hej_dom**）

```bash
cd custom_components
mkdir hej_dom
```

进入hej_dom目录并创建两个核心文件：

1. **manifest.json**（包含组件元数据）

```json
{
  "domain": "hej_dom",
  "name": "Moja integracja",
  "documentation": "https://link-do-dokumentacji.pl",
  "dependencies": [],
  "codeowners": [],
  "requirements": []
}
```

2. **__init__.py**（集成功能主代码）

```python
DOMAIN = 'hej_dom'

async def async_setup(hass, config):
    hass.states.async_set('hej_dom.info', 'Cześć!')

    # Zwróć True, aby wskazać, że inicjalizacja komponentu powiodłTo jest całkiem proste — wprowadzimy Cię w ten proces krok po kroku.
a się.
    return True
```

### 将集成添加至系统配置

通过终端进入家庭助理配置目录

```bash
cd ~/AIS
```

使用文本编辑器打开configuration.yaml文件

```bash
nano configuration.yaml
```

在文件末尾追加以下配置

```yaml
hej_dom:
```

### 配置验证与服务器重启

通过系统全局设置中的**检查配置**按钮验证配置有效性，随后点击**重新启动**完成服务重启

![](/img/en/bramka/faq_sensor_4.png)

### 系统新增实体

在系统实体状态面板中可查看新增实体（hej_dom）的实时状态与属性参数

![](/img/en/bramka/faq_custom_component_1.png)

当然，这个示例仅是入门引导，您最终实现的组件肯定比我们的示例更有实用价值。我们故意没有在代码中添加任何业务逻辑，以免模糊核心概念。实际组件可以实现诸如查询汇率、预测股市涨跌概率或降雨量、语音订购啤酒等功能——完全自由发挥，我们不做评判 ;)
之后，您可以通过家庭助理的自动化功能轻松将这个新组件与其他组件联动。例如：当天气预报有雨时→自动关闭草坪灌溉系统；或在结婚纪念日时，助理会语音提醒您（未来甚至能自动预订晚餐并启动客厅的浪漫场景模式等）。

### 将组件提交至家庭助理正式版

若您认为自己的组件足够优秀并希望分享给他人，推荐通过**向Home Assistant提交Pull Request**的方式实现：

https://github.com/home-assistant/home-assistant

这种方式能让您的组件经过数百名开发者的代码审查和数千名用户的测试，最终随Home Assistant的最新版本正式集成到家庭助理系统中。

### 故障排查

有时自定义集成（本例为电视控制功能）可能无法通过验证并出现异常，典型表现如下：

![](/img/en/bramka/faq_custom_component_2.png)

这表明家庭助理未能成功验证并加载custom_components文件夹中的组件。可能原因包括代码错误或设备缺少集成所需的依赖库。
此时应检查集成代码，并确认设备是否已安装集成所需的全部依赖库。

![](/img/en/bramka/faq_custom_component_3.png)

上图案例显示代码中引用了wakeonlan库但设备未安装，因此我们需要手动安装该依赖。

完成后再执行配置检查、重启服务，即可正常控制电视机。

![](/img/en/bramka/faq_custom_component_4.png)

使用自定义组件时，日志中会出现相应警告提示：

![](/img/en/bramka/faq_custom_component_5.png)