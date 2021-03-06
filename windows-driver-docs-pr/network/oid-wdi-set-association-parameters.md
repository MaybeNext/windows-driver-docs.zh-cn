---
title: OID_WDI_SET_ASSOCIATION_PARAMETERS
description: OID_WDI_SET_ASSOCIATION_PARAMETERS 指定适配器可以使用关联的一系列 BSSIDs 期间的参数。
ms.assetid: 86a6cc62-eaa4-435c-af6c-b76591d92c00
ms.date: 07/18/2017
keywords:
- 从 Windows Vista 开始 OID_WDI_SET_ASSOCIATION_PARAMETERS 网络驱动程序
ms.localizationpriority: medium
ms.custom: 19H1
ms.openlocfilehash: 681cc68754495e492b7593b3f862a0aa331811d4
ms.sourcegitcommit: fb7d95c7a5d47860918cd3602efdd33b69dcf2da
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/25/2019
ms.locfileid: "67353654"
---
# <a name="oidwdisetassociationparameters"></a>OID\_WDI\_设置\_关联\_参数


OID\_WDI\_设置\_关联\_参数指定该适配器可以使用关联的一系列 BSSIDs 期间的参数。

| 范围 | 设置与任务序列化 | 正常执行时间 （秒） |
|-------|--------------------------|---------------------------------|
| Port  | 否                       | 1                               |

 

此命令将替换以前配置的特定于 BSSID 的关联参数列表。

## <a name="set-property-parameters"></a>设置属性参数


| TLV                                                                     | 允许多个 TLV 实例 | 可选 | 描述                     |
|-------------------------------------------------------------------------|--------------------------------|----------|---------------------------------|
| [**WDI\_TLV\_CONNECT\_BSS\_条目**](https://docs.microsoft.com/windows-hardware/drivers/network/wdi-tlv-connect-bss-entry) | X                              |          | BSS 条目和参数。 |

 

## <a name="set-property-results"></a>设置属性结果


没有其他数据。 标头中的数据就足够了。

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

 

 




