---
title: OID_WWAN_PROVISIONED_CONTEXTS
description: OID_WWAN_PROVISIONED_CONTEXTS 读取或更新存储在 MB 设备或订户标识模块（SIM）上的预配上下文条目。
ms.assetid: 7634fc32-9059-4f89-a591-7aa663b0c188
ms.date: 08/08/2017
keywords: -从 Windows Vista 开始 OID_WWAN_PROVISIONED_CONTEXTS 网络驱动程序
ms.localizationpriority: medium
ms.openlocfilehash: ee4ef4382aa1dc7eb6007f972c0efa7df28c508c
ms.sourcegitcommit: 4b7a6ac7c68e6ad6f27da5d1dc4deabd5d34b748
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2019
ms.locfileid: "72843805"
---
# <a name="oid_wwan_provisioned_contexts"></a>OID\_WWAN\_预配\_上下文


OID\_WWAN\_预配\_上下文读取或更新存储在 MB 设备或订户标识模块（SIM）上的预配上下文条目。

微型端口驱动程序必须异步处理集和查询请求，最初返回 NDIS\_状态\_指示\_需要原始请求，稍后发送[**ndis\_状态\_WWAN\_预配\_上下文**](ndis-status-wwan-provisioned-contexts.md)状态通知，包含[**NDIS\_WWAN\_预配\_上下文**](https://docs.microsoft.com/windows-hardware/drivers/ddi/ndiswwan/ns-ndiswwan-_ndis_wwan_provisioned_contexts)结构，以提供存储在 MB 设备或订阅服务器上的预配上下文条目的相关信息标识模块（SIM），而不考虑完成的集合或查询请求。

<a name="remarks"></a>备注
-------

有关使用此 OID 的详细信息，请参阅[WWAN 数据包上下文管理](https://docs.microsoft.com/windows-hardware/drivers/network/mb-packet-context-management)。

如果端口支持的 MB 设备不支持检索预配的上下文，则微型端口驱动程序应返回 NDIS\_状态\_不\_支持。

基于 GSM 的设备可以选择支持查询和设置操作。 基于 CDMA 的设备可以选择支持查询操作报告简单 IP （WWAN\_CTRL\_CAP\_CDMA\_简单\_IP）。

存储在 MB 设备上的预配上下文条目或 SIM 在设备本地。 小型端口驱动程序不应连接到网络来读取这些字段。

Set 请求的输入结构为 NDIS\_WWAN\_集\_预配\_上下文和状态指示此对象为 NDIS\_状态\_WWAN\_预配\_上下文。

预配的上下文与缓存 APNs 列表的3GPP 中的 GPRS 上下文定义不同。 预配的上下文是连接参数（AccessString、用户名和密码），由设备预配的操作员或 OTA 预配，并且可以存储在设备内存或 SIM 中。 MB 服务将使用由预配的上下文返回的连接参数进行 PDP 激活。

使用此对象的查询和设置形式。

此请求的处理不需要网络访问，但需要在 MB 设备上访问 SIM 或辅助内存。

微型端口驱动程序将 NDIS\_状态\_WWAN\_预配\_上下文通知发送到操作系统。 **ContextListHeader**成员应设置为*WwanStructContext*。 当发送通知以响应某个设置请求时，微型端口驱动程序应将**elementcount 多于**成员设置为0。

在执行任何单个上下文激活或停用之前，MB 服务应从设备检索预配的上下文列表。 预配上下文的列表必须仅限制为主提供商网络，即使设备可能能够存储多个网络提供程序上下文。 上下文列表必须始终是特定于家乡提供商网络的，即使是漫游也是如此。

设置 OID\_WWAN\_预配\_上下文操作应将上下文与在 WWAN\_集\_上下文结构的**ProviderId**成员的 set 请求中指定的网络提供程序相关联。 通过设置 OID 存储的预配上下文\_WWAN\_预配\_上下文请求必须跨系统重新启动和设备电源回收保持不变。

所有空上下文都需要在查询上报告，并与适用于 home 提供商网络的预配上下文一起报告。

为 SimpleIP 配置的 CDMA 设备（WWAN\_CTRL\_CAP\_CDMA\_简单\_IP 在 WwanControlCaps 中，可以选择性地返回至少一个预配的上下文，其中填充了正确的**AccessString**、**用户名**和**密码**成员，用于来自 MB 服务的查询请求。

预配的上下文列表应在设备中预配，\_WWAN\_预配\_上下文操作中进行更新，或使用 SMS 或 OTA 通过设备/操作员更新。 不能基于 OID\_WWAN\_通过 MB 服务进行连接操作中提供的上下文信息进行动态更新。

若要详细了解如何从 MB 设备访问列表中每个预配上下文的 AccessString、UserName 和 Password，请参阅[**WWAN\_上下文**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wwan/ns-wwan-_wwan_context)。

<a name="requirements"></a>要求
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p>版本</p></td>
<td><p>在 windows 7 和更高版本的 Windows 中可用。</p></td>
</tr>
<tr class="even">
<td><p>标头</p></td>
<td>Ntddndis （包括 Ndis .h）</td>
</tr>
</tbody>
</table>

## <a name="see-also"></a>另请参阅


[WWAN 数据包上下文管理](https://docs.microsoft.com/windows-hardware/drivers/network/mb-packet-context-management)

 

 




