---
title: 微驱动程序函数
description: 微驱动程序函数
ms.assetid: 491b954a-8ffa-4899-8c7d-0aee409f4742
ms.date: 04/20/2017
ms.localizationpriority: medium
ms.openlocfilehash: 08d8dfd1f773bc1bc65321850ec4bf0c750f9046
ms.sourcegitcommit: 4b7a6ac7c68e6ad6f27da5d1dc4deabd5d34b748
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2019
ms.locfileid: "72840783"
---
# <a name="microdriver-functions"></a>微驱动程序函数





WIA 平板驱动程序通过调用 WIA microdriver 函数来响应来自 WIA 服务的请求。 这些函数必须由供应商提供的每个 microdriver 实现，并且包含以下各项：

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>函数</th>
<th>描述</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><a href="https://docs.microsoft.com/windows-hardware/drivers/ddi/wiamicro/nf-wiamicro-microentry" data-raw-source="[&lt;strong&gt;MicroEntry&lt;/strong&gt;](https://docs.microsoft.com/windows-hardware/drivers/ddi/wiamicro/nf-wiamicro-microentry)"><strong>MicroEntry</strong></a></p></td>
<td><p>响应 WIA 平板驱动程序发送的命令。</p></td>
</tr>
<tr class="even">
<td><p><a href="https://docs.microsoft.com/windows-hardware/drivers/ddi/wiamicro/nf-wiamicro-scan" data-raw-source="[&lt;strong&gt;Scan&lt;/strong&gt;](https://docs.microsoft.com/windows-hardware/drivers/ddi/wiamicro/nf-wiamicro-scan)"><strong>检测</strong></a></p></td>
<td><p>从设备读取数据并将数据返回到 WIA 平板驱动程序。</p></td>
</tr>
<tr class="odd">
<td><p><a href="https://docs.microsoft.com/windows-hardware/drivers/ddi/wiamicro/nf-wiamicro-setpixelwindow" data-raw-source="[&lt;strong&gt;SetPixelWindow&lt;/strong&gt;](https://docs.microsoft.com/windows-hardware/drivers/ddi/wiamicro/nf-wiamicro-setpixelwindow)"><strong>SetPixelWindow</strong></a></p></td>
<td><p>设置要扫描的区域。</p></td>
</tr>
</tbody>
</table>

 

 

 




