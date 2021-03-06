---
title: WriteErrorLog 规则 (ndis)
description: WriteErrorLog 规则指定，是否 MiniportInitializeEx 函数中调用 NdisMAllocateSharedMemory 函数，则该驱动程序还应调用 NdisWriteErrorLogEntry 是否分配失败。
ms.assetid: b626f25a-3101-4c0a-b0a9-fef6ce964055
ms.date: 05/21/2018
keywords:
- WriteErrorLog 规则 (ndis)
topic_type:
- apiref
api_name:
- WriteErrorLog
api_type:
- NA
ms.localizationpriority: medium
ms.openlocfilehash: a686eeeea1c746fe2004de92a503f3b9d948e259
ms.sourcegitcommit: f663c383886d87ea762e419963ff427500cc5042
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/25/2019
ms.locfileid: "67392107"
---
# <a name="writeerrorlog-rule-ndis"></a>WriteErrorLog 规则 (ndis)


WriteErrorLog 规则指定，如果**NdisMAllocateSharedMemory**调用函数*MiniportInitializeEx*函数，该驱动程序还应调用**NdisWriteErrorLogEntry**如果分配失败。

通常情况下，它是在日志中记录一个错误条目分配内存操作失败时的好办法。 中发生的分配操作的大多数*MiniportInitializeEx*回调函数。 请参阅下面的代码示例，详细了解如何记录错误。

|              |      |
|--------------|------|
| 驱动程序模型 | NDIS |

<a name="example"></a>示例
-------

```
// an example of how to log an error if memory allocation fails PVOID p;
NdisMAllocateSharedMemory(par1, par2, par3, &p, ...);
if (p == NULL)
{
 NdisWriteErrorLogEntry("Memory allocation failed");
}
```

<a name="how-to-test"></a>如何测试
-----------

<table>
<colgroup>
<col width="100%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">在编译时</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p>运行<a href="https://docs.microsoft.com/windows-hardware/drivers/devtest/static-driver-verifier" data-raw-source="[Static Driver Verifier](https://docs.microsoft.com/windows-hardware/drivers/devtest/static-driver-verifier)">Static Driver Verifier</a>并指定<strong>WriteErrorLog</strong>规则。</p>
使用以下步骤来分析你的代码：
<ol>
<li><a href="https://docs.microsoft.com/windows-hardware/drivers/devtest/using-static-driver-verifier-to-find-defects-in-drivers#preparing-your-source-code" data-raw-source="[Prepare your code (use role type declarations).](https://docs.microsoft.com/windows-hardware/drivers/devtest/using-static-driver-verifier-to-find-defects-in-drivers#preparing-your-source-code)">准备你的代码 （使用角色类型声明）。</a></li>
<li><a href="https://docs.microsoft.com/windows-hardware/drivers/devtest/using-static-driver-verifier-to-find-defects-in-drivers#running-static-driver-verifier" data-raw-source="[Run Static Driver Verifier.](https://docs.microsoft.com/windows-hardware/drivers/devtest/using-static-driver-verifier-to-find-defects-in-drivers#running-static-driver-verifier)">运行的 Static Driver Verifier。</a></li>
<li><a href="https://docs.microsoft.com/windows-hardware/drivers/devtest/using-static-driver-verifier-to-find-defects-in-drivers#viewing-and-analyzing-the-results" data-raw-source="[View and analyze the results.](https://docs.microsoft.com/windows-hardware/drivers/devtest/using-static-driver-verifier-to-find-defects-in-drivers#viewing-and-analyzing-the-results)">查看和分析结果。</a></li>
</ol>
<p>有关详细信息，请参阅<a href="https://docs.microsoft.com/windows-hardware/drivers/devtest/using-static-driver-verifier-to-find-defects-in-drivers" data-raw-source="[Using Static Driver Verifier to Find Defects in Drivers](https://docs.microsoft.com/windows-hardware/drivers/devtest/using-static-driver-verifier-to-find-defects-in-drivers)">以找到缺陷驱动程序中使用 Static Driver Verifier</a>。</p></td>
</tr>
</tbody>
</table>

 

 





