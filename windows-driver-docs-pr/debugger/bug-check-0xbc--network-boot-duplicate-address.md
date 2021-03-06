---
title: Bug 检查 0xBC NETWORK_BOOT_DUPLICATE_ADDRESS
description: NETWORK_BOOT_DUPLICATE_ADDRESS bug 检查具有 0x000000BC 值。 这指示关闭网络启动时重复的 IP 地址已分配给此计算机。
ms.assetid: 54c45e73-7054-4dba-abe4-91f5f5a064a4
keywords:
- Bug 检查 0xBC NETWORK_BOOT_DUPLICATE_ADDRESS
- NETWORK_BOOT_DUPLICATE_ADDRESS
ms.date: 05/23/2017
topic_type:
- apiref
api_name:
- NETWORK_BOOT_DUPLICATE_ADDRESS
api_type:
- NA
ms.localizationpriority: medium
ms.openlocfilehash: 05f093807c9d59dd7a34e07888160790edb09ab3
ms.sourcegitcommit: d03b44343cd32b3653d0471afcdd3d35cb800c0d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/02/2019
ms.locfileid: "67518997"
---
# <a name="bug-check-0xbc-networkbootduplicateaddress"></a>Bug 检查 0xBC：网络\_引导\_重复\_地址


网络\_引导\_重复\_地址错误检查的值为 0x000000BC。 这指示关闭网络启动时重复的 IP 地址已分配给此计算机。

> [!IMPORTANT]
> 本主题面向程序员。 如果你已使用计算机时收到一个蓝色的屏幕，错误代码的客户，请参阅[疑难解答蓝屏错误](https://www.windows.com/stopcode)。


## <a name="networkbootduplicateaddress-parameters"></a>网络\_引导\_重复\_地址参数


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
<td align="left"><p>显示以 DWORD 的 IP 地址。 形式的地址<em>aa.bb.cc.dd</em>将显示为 0xDDCCBBAA。</p></td>
</tr>
<tr class="even">
<td align="left"><p>2</p></td>
<td align="left"><p>其他计算机的硬件地址。 （对于以太网连接，请参阅以下注释）。</p></td>
</tr>
<tr class="odd">
<td align="left"><p>3</p></td>
<td align="left"><p>其他计算机的硬件地址。 （对于以太网连接，请参阅以下注释）。</p></td>
</tr>
<tr class="even">
<td align="left"><p>4</p></td>
<td align="left"><p>其他计算机的硬件地址。 （对于以太网连接，这将为零。）</p></td>
</tr>
</tbody>
</table>

 

**请注意**  时参数 4 等于零，则这指示以太网连接。 在这种情况下，将参数 2 和参数 3 中存储的 MAC 地址。 在窗体的以太网 MAC 地址*aa-bb-cc-dd-ee-ff*将导致参数 2 为等于 0xAABBCCDD 和参数 3 为等于 0xEEFF0000。

 

<a name="cause"></a>原因
-----

此错误表示，TCP/IP 发送出其 IP 地址 ARP 时，它指示重复的 IP 地址在其他计算机中接收到响应。

当从网络启动 Windows 时，这是一个错误。

 

 




