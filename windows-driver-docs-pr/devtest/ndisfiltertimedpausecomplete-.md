---
title: NdisFilterTimedPauseComplete 规则（ndis）
description: NdisFilterTimedPauseComplete 验证三项 FilterPause 函数将在10秒或更短时间内完成。FilterPause 函数不能失败。FilterPause 函数不得完成两次。
ms.assetid: 60B926CC-E2C4-42B8-8555-5E620DCDDAFC
ms.date: 05/21/2018
keywords:
- NdisFilterTimedPauseComplete 规则（ndis）
topic_type:
- apiref
api_name:
- NdisFilterTimedPauseComplete
api_type:
- NA
ms.localizationpriority: medium
ms.openlocfilehash: fcf139118b4347c517b1d6d0cf040e698e7faa6e
ms.sourcegitcommit: 4b7a6ac7c68e6ad6f27da5d1dc4deabd5d34b748
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2019
ms.locfileid: "72839340"
---
# <a name="ndisfiltertimedpausecomplete-rule-ndis"></a>NdisFilterTimedPauseComplete 规则（ndis）


**NdisFilterTimedPauseComplete**验证三个方面：

-   [*FilterPause*](https://docs.microsoft.com/windows-hardware/drivers/ddi/ndis/nc-ndis-filter_pause)函数将在10秒或更短时间内完成。

-   [*FilterPause*](https://docs.microsoft.com/windows-hardware/drivers/ddi/ndis/nc-ndis-filter_pause)函数不能失败。

-   [*FilterPause*](https://docs.microsoft.com/windows-hardware/drivers/ddi/ndis/nc-ndis-filter_pause)函数不得完成两次。

|              |      |
|--------------|------|
| 驱动程序模型 | NDIS |

|                                   |                                                                                                                                        |
|-----------------------------------|----------------------------------------------------------------------------------------------------------------------------------------|
| 使用此规则发现的错误检查 | [**Bug 检查0xC4：检测到\_冲突的驱动程序\_验证程序\_** ](https://docs.microsoft.com/windows-hardware/drivers/debugger/bug-check-0xc4--driver-verifier-detected-violation) （0x00092010） |

<a name="how-to-test"></a>如何测试
-----------

<table>
<colgroup>
<col width="100%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">在运行时</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p>运行<a href="https://docs.microsoft.com/windows-hardware/drivers/devtest/driver-verifier" data-raw-source="[Driver Verifier](https://docs.microsoft.com/windows-hardware/drivers/devtest/driver-verifier)">驱动程序验证程序</a>，并选择<a href="https://docs.microsoft.com/windows-hardware/drivers/devtest/ndis-wifi-verification" data-raw-source="[NDIS/WIFI verification](https://docs.microsoft.com/windows-hardware/drivers/devtest/ndis-wifi-verification)">NDIS/WIFI 验证</a>选项。 此规则也会用<a href="https://docs.microsoft.com/windows-hardware/drivers/devtest/ddi-compliance-checking" data-raw-source="[DDI compliance checking](https://docs.microsoft.com/windows-hardware/drivers/devtest/ddi-compliance-checking)">DDI 相容性检查</a>选项进行测试。</p></td>
</tr>
</tbody>
</table>

 

 

 





