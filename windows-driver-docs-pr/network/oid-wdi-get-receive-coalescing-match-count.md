---
title: OID_WDI_GET_RECEIVE_COALESCING_MATCH_COUNT
description: OID_WDI_GET_RECEIVE_COALESCING_MATCH_COUNT 请求接收的网络端口的筛选器的具有匹配的数据包数。
ms.assetid: 45b68057-d62a-4b77-9634-dfbed2817f23
ms.date: 07/18/2017
keywords:
- 从 Windows Vista 开始 OID_WDI_GET_RECEIVE_COALESCING_MATCH_COUNT 网络驱动程序
ms.localizationpriority: medium
ms.openlocfilehash: c7b76b1122662f2fd035154703328a5b51bc9fcd
ms.sourcegitcommit: fb7d95c7a5d47860918cd3602efdd33b69dcf2da
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/25/2019
ms.locfileid: "67387269"
---
# <a name="oidwdigetreceivecoalescingmatchcount"></a>OID\_WDI\_GET\_RECEIVE\_COALESCING\_MATCH\_COUNT


OID\_WDI\_获取\_接收\_COALESCING\_匹配\_计数请求接收的网络端口的筛选器的具有匹配的数据包数。

| 范围 | 设置与任务序列化 | 正常执行时间 （秒） |
|-------|--------------------------|---------------------------------|
| Port  | 是                      | 1                               |

 

## <a name="get-property-parameters"></a>获取属性参数


任何其他参数。 标头中的数据就足够了。
## <a name="get-property-results"></a>获取属性的结果


| TLV                                                                                              | 允许多个 TLV 实例 | 可选 | 描述                                                                  |
|--------------------------------------------------------------------------------------------------|--------------------------------|----------|------------------------------------------------------------------------------|
| [**WDI\_TLV\_COALESCING\_FILTER\_MATCH\_COUNT**](https://docs.microsoft.com/windows-hardware/drivers/network/wdi-tlv-coalescing-filter-match-count) |                                |          | 接收的网络端口的筛选器的具有匹配的数据包数。 |

 

<a name="requirements"></a>要求
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p>最低受支持的客户端</p></td>
<td><p>Windows 10</p></td>
</tr>
<tr class="even">
<td><p>最低受支持的服务器</p></td>
<td><p>Windows Server 2016</p></td>
</tr>
<tr class="odd">
<td><p>Header</p></td>
<td>Dot11wdi.h</td>
</tr>
</tbody>
</table>

 

 




