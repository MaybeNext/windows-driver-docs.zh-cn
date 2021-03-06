---
title: Bug Check 0xBF MUTEX_ALREADY_OWNED
description: MUTEX_ALREADY_OWNED bug 检查具有 0x000000BF 值。 这指示线程尝试获取 mutex 的所有权它已经拥有。
ms.assetid: 0008c6eb-3add-4169-b29a-6fe4d77c5c9e
keywords:
- Bug Check 0xBF MUTEX_ALREADY_OWNED
- MUTEX_ALREADY_OWNED
ms.date: 05/23/2017
topic_type:
- apiref
api_name:
- MUTEX_ALREADY_OWNED
api_type:
- NA
ms.localizationpriority: medium
ms.openlocfilehash: d9a5e33a175cc4745dcaa96cb1411ce2ddba8e1e
ms.sourcegitcommit: d03b44343cd32b3653d0471afcdd3d35cb800c0d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/02/2019
ms.locfileid: "67518974"
---
# <a name="bug-check-0xbf-mutexalreadyowned"></a>Bug 检查 0xBF：MUTEX\_ALREADY\_拥有的


MUTEX\_ALREADY\_拥有的 bug 检查的值为 0x000000BF。 这指示线程尝试获取 mutex 的所有权它已经拥有。

> [!IMPORTANT]
> 本主题面向程序员。 如果你已使用计算机时收到一个蓝色的屏幕，错误代码的客户，请参阅[疑难解答蓝屏错误](https://www.windows.com/stopcode)。


## <a name="mutexalreadyowned-parameters"></a>MUTEX\_ALREADY\_拥有的参数


<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">参数</th>
<th align="left">描述</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p>1</p></td>
<td align="left"><p>互斥体的地址</p></td>
</tr>
<tr class="even">
<td align="left"><p>2</p></td>
<td align="left"><p>导致了错误的线程</p></td>
</tr>
<tr class="odd">
<td align="left"><p>3</p></td>
<td align="left"><p>0</p></td>
</tr>
<tr class="even">
<td align="left"><p>4</p></td>
<td align="left"><p>保留</p></td>
</tr>
</tbody>
</table>

 

 

 




