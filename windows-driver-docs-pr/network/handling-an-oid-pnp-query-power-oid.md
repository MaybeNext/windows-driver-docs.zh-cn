---
title: 处理 OID_PNP_QUERY_POWER OID
description: 处理 OID_PNP_QUERY_POWER OID
ms.assetid: aec9393a-debb-41eb-a8a0-b3d1936d707b
keywords:
- OID_PNP_QUERY_POWER
- 网络接口卡 WDK 网络，转换的电源状态
- Nic WDK 网络，转换的电源状态
- 电源管理 WDK NDIS 微型端口转换的电源状态
- 设备电源状态 WDK 网络
- 电源状态 WDK 网络
- 转换电源状态 WDK 网络
ms.date: 04/20/2017
ms.localizationpriority: medium
ms.openlocfilehash: 2e25f95a384bd41e85af53143a6f508af3e79822
ms.sourcegitcommit: fb7d95c7a5d47860918cd3602efdd33b69dcf2da
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/25/2019
ms.locfileid: "67379825"
---
# <a name="handling-an-oidpnpquerypower-oid"></a>处理 OID\_PNP\_查询\_POWER OID





[OID\_PNP\_查询\_POWER](https://docs.microsoft.com/windows-hardware/drivers/network/oid-pnp-query-power) OID 请求以指示它是否可以转换到低功耗状态的网络适配器的微型端口驱动程序。 微型端口驱动程序必须始终返回 NDIS\_状态\_OID 的查询响应中的成功\_PNP\_查询\_电源。 通过返回 NDIS\_状态\_此 OID 的成功请求，微型端口驱动程序可保证它将转换为指定的设备电源状态在收到的后续的网络适配器[OID\_PNP\_设置\_电源](https://docs.microsoft.com/windows-hardware/drivers/network/oid-pnp-set-power)请求。 微型端口驱动程序，在这种情况下，必须执行任何操作危害到太空船转换。

[OID\_PNP\_查询\_POWER](https://docs.microsoft.com/windows-hardware/drivers/network/oid-pnp-query-power)请求始终后跟 OID\_PNP\_设置\_POWER 请求。 [OID\_PNP\_设置\_POWER](https://docs.microsoft.com/windows-hardware/drivers/network/oid-pnp-set-power)请求立即可以按照 OID\_PNP\_查询\_POWER 请求或可以到达的未指定时间间隔之后 OID\_PNP\_查询\_POWER 请求。 D0，OID 中指定的设备状态\_PNP\_设置\_电源请求，有效地取消前面的 OID\_PNP\_查询\_POWER 请求。

 

 





