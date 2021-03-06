---
title: AV/C 连接方案
description: AV/C 连接方案
ms.assetid: 392f996c-47aa-4ceb-adf9-0c8fd114a511
keywords:
- 连接 WDK AV/C
- AV/C WDK，连接方案
- 数字视频 WDK AV/C
- DV WDK AV/C
- 机顶盒 WDK AV/C
- STB WDK AV/C
- TV WDK AV/C
- 电视 WDK AV/C
- 子次级支持 WDK AV/C
- 内部连接 WDK AV/C
- 设备间连接 WDK AV/C
- Avc 函数驱动程序 WDK，连接
- 外部插头连接 WDK AV/C
ms.date: 04/20/2017
ms.localizationpriority: medium
ms.openlocfilehash: 2c62ae8ec252385b330f9479551e47a5cec9ee68
ms.sourcegitcommit: 4b7a6ac7c68e6ad6f27da5d1dc4deabd5d34b748
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2019
ms.locfileid: "72843366"
---
# <a name="avc-connection-scenarios"></a>AV/C 连接方案





在 Windows Vista 之前， *Avc*中的连接和兼容性管理（CCM）协议支持单一连接方案，在此方案中，计算机充当外部 AV/C 设备的控制器来启动来自设备的数据流。 例如，若要开始流式传输， *Avc*中的连接管理通过使用连接和断开连接单元命令（Avc\_在设备上的子单位和设备单位的同步输出插件之间建立连接。[**函数\_分别获取**](https://docs.microsoft.com/windows-hardware/drivers/stream/avc-function-acquire)和[**AVC\_函数\_版本**](https://docs.microsoft.com/windows-hardware/drivers/stream/avc-function-release)）。 有关 AV/C 规范和 CCM 协议的详细信息，请参阅[1394 贸易关联](https://go.microsoft.com/fwlink/p/?linkid=518448)网站。

在 Windows Vista 中，已对连接管理进行了改进，以支持7个以上的连接方案，使*Avc*支持8个单位/子单位的连接方案。 连接管理的改进增加了对从子源插入到其他子源的连接的支持;子单元连接可以在同一 AV/C 单位内或不同的 AV/C 单位内。 *Avc*使用信号源建立连接，然后输入-select CCM 协议单元命令。 （*Avc*支持将其他 CCM 协议单元命令（如输出预设）仅用于 AV/C 规范要求的级别。）

有两种常规连接类型与 AV/C 单元和子单元连接相关：

-   *一种连接，其中，外部设备连接到主计算机，并且计算机可以控制连接，但它不是连接的一部分*。 此连接类型不使用任何基于主机的内存。 相反，连接是包含设备的无内存介质，主机只充当控制器。 此类连接的一个示例是机顶盒（STB）的调谐器子组，它将数据直接流式传输到数字电视的 "监视" 子组，而不会在计算机上处理数据流。

-   *一种连接，其中，外部设备通过使用标准介质连接到主计算机，并使用缓冲区将数据从设备复制到主计算机的内存*。 这种连接类型的一个示例是数字视频（DV）设备，用于将数据流式传输到计算机，稍后对其进行处理。 *Msdv*驱动程序使用这种类型的连接（在 DV 设备和主计算机之间）。

为*Avc*中的 Windows Vista 实现的改进连接管理适用于第一种连接类型，在该连接中，设备可以响应 AV/C 命令进行内部连接。 如果设备支持 AV/C CCM 协议， *Avc*中改进的连接管理可以在不同的 AV/c 设备（同一 IEEE 1394 总线）上的两个磁带子单元连接之间建立端到端连接。

**请注意**，  *Avc*不支持第二种连接类型（内存缓冲区）。 但是，连接的内存缓冲区类型遵循[IEC 61883](https://docs.microsoft.com/windows-hardware/drivers/ieee/iec-61883-client-drivers)协议，并受同一堆栈中的基础*61883*驱动程序（其中计算机涉及到内存缓冲区连接）的支持。

 

### <a name="supported-connection-scenarios-in-windows-vista"></a>Windows Vista 中支持的连接方案

四种方案（1到4）表示单元*内部*连接。 这些连接完全包含在一个 AV/C 单元中。 其他四个方案（5到8）表示单元*间*的连接。 这些连接介于两个不同的 AV/C 单元之间。

以下主题讨论了8种不同的 AV/C 连接管理方案，以及[**AVCCONNECTINFO**](https://docs.microsoft.com/windows-hardware/drivers/ddi/avc/ns-avc-_avcconnectinfo)结构成员的各个值：

[一个 AV/C 单元中的子单位插头和单元插头之间的连接](connections-between-subunit-plugs-and-unit-plugs-within-one-av-c-unit.md)

[一个 AV/C 单元内两个子单位的连接](connections-between-two-subunit-plugs-within-one-av-c-unit.md)

[两个不同 AV/C 单位中的两个子单位的连接](connections-between-two-subunit-plugs-in-different-av-c-units.md)

[不同 AV/C 单元中两个单元插头之间的连接](connections-between-two-unit-plugs-in-different-av-c-units.md)

 

 




