---
title: 自定义打印机端口监视器
description: 自定义打印机端口监视器
ms.assetid: e5d4166a-2593-43fd-b476-c54642e2d099
keywords:
- 内置自动配置支持 WDK 打印机，自定义打印机端口监视器
- 双向扩展文件 WDK 打印机自动配置
- 内置自动配置支持 WDK 打印机，双向扩展文件
- 自定义打印机端口监视器 WDK
- 端口监视 WDK 打印，自定义
- 到双向数据类型 WDK 打印机的 WinSNMP 转换
- 双向通信 WDK 打印
- 双向通信 WDK 打印
ms.date: 04/20/2017
ms.localizationpriority: medium
ms.openlocfilehash: 23ea83d16f04cb2295c8e895a8b67ff52b672285
ms.sourcegitcommit: 4b7a6ac7c68e6ad6f27da5d1dc4deabd5d34b748
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2019
ms.locfileid: "72843376"
---
# <a name="customizing-the-printer-port-monitors"></a>自定义打印机端口监视器


你可以通过自定义 Windows Vista 提供的标准 TCP/IP 或 Web 服务（WSD）端口监视器，为具有高于和超过标准[双向通信架构](bidirectional-communication-schema.md)的功能的打印设备定义新的架构。 您必须创建一个双向扩展文件，该文件是一个 XML 文件，用于定义特定于该驱动程序的新架构。 此扩展文件在安装驱动程序时安装。 当 TCP/IP 或 WSD 端口监视器标识此扩展文件时，监视器将加载该文件，然后可以使用其他双向架构。

双向扩展文件中的架构是标准打印架构的子集。 此类架构必须符合 WDK 附带的 Tcpbidi 或 WsdBidi 文件的结构。

**请注意**  如果[双向通信架构](bidirectional-communication-schema.md)满足你的要求，则无需创建双向扩展文件，因此无需自定义打印端口监视器。

 

如果满足以下任一条件，则应创建一个双向扩展文件并将其与打印机驱动程序关联：

1.  打印机驱动程序需要打印机中找不到标准打印架构的信息。 若要获取此信息，必须通过附加查询扩展支持的架构。 枚举特定端口支持的架构的任何其他客户端将获取其他查询，但通常不能理解它们。

2.  你计划包括标准 TCP/IP 或 WSD 端口监视器不支持的标准打印架构中的查询，因为查询需要特定于驱动程序的信息。 在这种情况下，必须扩展打印架构。 通常情况下，应扩展与输入和输出箱相关的打印架构部分用于打印介质。 还应在双向架构中定义的储箱名称和打印机的管理信息基础（MIB）中提供映射。

3.  你打算自定义标准查询的工作方式，如设置自定义对象标识符（OID）或更改刷新间隔。 例如，在默认时间间隔为600秒（10分钟）的标准 TCP/IP 端口监视器对不支持 Web 服务事件的设备进行轮询。 可以通过创建在与设备关联的[值](value.md)构造中设置 refreshInterval 属性的双向扩展来更改轮询间隔。 （请参阅以下代码示例中的 `Memory` 属性。）

如果驱动程序没有关联的双向扩展文件，则标准打印架构中的双向通信支持无法响应需要驱动程序特定数据（如与输入和输出容器相关的数据）的查询。

**请注意**   Windows Vista 中的网络路由隔离舱，允许受信任的进程连接到不同的网络接口（无论虚拟还是物理），同时使各种接口彼此隔离。 例如，Windows Vista 使用这些隔离舱来强制执行不允许同时访问 VPN 和用户的本地网络和 Internet 的 VPN 策略。 打印期间，后台处理程序会在打开 TCP 打印机端口时模拟用户。 因此，当用户连接到 VPN 时，后台处理程序无法打印到本地网络打印机。

 

### <a name="structure-of-a-bidi-extension-file"></a>双向扩展文件的结构

双向扩展文件是格式正确的 XML，必须根据 Microsoft Windows 驱动程序工具包（WDK）提供的 Tcpbidi 或 WsdBidi 文件有效。 使用这些 .xsd 文件中定义的构造，可以定义新的架构。

下面是 TCP/IP 双向扩展文件的不完整示例，它显示了其基本结构。 WSD 双向扩展文件的结构类似。

```cpp
<?xml version="1.0" encoding="US-ASCII"?>
<bidi:Schema xmlns:bidi="http://schemas.microsoft.com/windows/2005/03/printing/bidi">
  <Schema>
    <Property name="Printer">
      <Property name="Configuration">
        <Property name= "Memory">
          <Value name="Size" type="BIDI_INT" oid="1.3.6.1.2.1.25.2.2" refreshInterval="600" drvPrinterEvent="true" />
          .
          .
          .
        </Property>
      </Property>
    </Property>
  </Schema>
</bidi:Schema>
```

在上面的代码示例中，请注意：

-   根元素只包含一个 Schema 元素。 架构的层次结构以 Schema 元素开头。

-   Schema 元素具有作为叶的节点和值元素的属性元素。

-   每个 Value 元素定义可用于检索数据的特定技术。

### <a name="conversion-of-winsnmp-to-bidi-data-types"></a>从 WinSNMP 到双向数据类型的转换

在[**双向\_类型**](https://docs.microsoft.com/windows-hardware/drivers/ddi/winspool/ne-winspool-bidi_type)枚举主题中提供了简单网络管理协议（SNMP）类型和双向类型之间的对应关系。

本部分的其余部分包含以下主题，可帮助您创建自己的双向架构扩展。

[TCP/IP 架构扩展](tcp-ip-schema-extensions.md)

[WSD 架构扩展](wsd-schema-extensions-for-driver-specific-queries.md)

 

 




