---
title: IWiaLog COM 接口
description: IWiaLog COM 接口
ms.assetid: e5d42b5d-796f-42f3-9c01-4234b8765ca6
ms.date: 04/20/2017
ms.localizationpriority: medium
ms.openlocfilehash: 3ba8c608708f11feca58d20042732625aeaad079
ms.sourcegitcommit: 4b7a6ac7c68e6ad6f27da5d1dc4deabd5d34b748
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2019
ms.locfileid: "72840798"
---
# <a name="iwialog-com-interface"></a>IWiaLog COM 接口





[**IWiaLog 接口**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wia_lh/nn-wia_lh-iwialog)在 MICROSOFT Windows XP 和更高版本中已过时，不再受支持。 请改用 WIA 诊断日志宏。

提供它只是为了实现向后兼容性。 此接口中的方法允许微型驱动程序将错误、跟踪和警告消息写入日志。 **IWiaLog**接口提供以下方法。

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>方法</th>
<th>描述</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><a href="https://docs.microsoft.com/windows-hardware/drivers/ddi/wia_lh/nf-wia_lh-iwialog-initializelog" data-raw-source="[&lt;strong&gt;IWiaLog::InitializeLog&lt;/strong&gt;](https://docs.microsoft.com/windows-hardware/drivers/ddi/wia_lh/nf-wia_lh-iwialog-initializelog)"><strong>IWiaLog：： InitializeLog</strong></a></p></td>
<td><p>初始化日志记录实用程序。</p></td>
</tr>
<tr class="even">
<td><p><a href="https://docs.microsoft.com/windows-hardware/drivers/ddi/wia_lh/nf-wia_lh-iwialog-log" data-raw-source="[&lt;strong&gt;IWiaLog::Log&lt;/strong&gt;](https://docs.microsoft.com/windows-hardware/drivers/ddi/wia_lh/nf-wia_lh-iwialog-log)"><strong>IWiaLog：： Log</strong></a></p></td>
<td><p>将消息记录到文件或其他目标。</p></td>
</tr>
<tr class="odd">
<td><p><a href="https://docs.microsoft.com/windows-hardware/drivers/ddi/wia_lh/nf-wia_lh-iwialog-hresult" data-raw-source="[&lt;strong&gt;IWiaLog::hResult&lt;/strong&gt;](https://docs.microsoft.com/windows-hardware/drivers/ddi/wia_lh/nf-wia_lh-iwialog-hresult)"><strong>IWiaLog：： hResult</strong></a></p></td>
<td><p>将 HRESULT 转换为字符串。</p></td>
</tr>
</tbody>
</table>

 

有关此接口的详细信息，请参阅[IWiaLog 接口和诊断日志宏](https://docs.microsoft.com/windows-hardware/drivers/ddi/_image/index)。

 

 




