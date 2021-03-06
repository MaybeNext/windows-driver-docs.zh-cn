---
title: 设置启动类型值
description: 设置启动类型值
ms.assetid: dcc38a36-4755-472b-94c8-dfed892460ee
keywords:
- INF 文件 WDK 显示的启动类型值
- 启动 WDK 显示类型值
ms.date: 04/20/2017
ms.localizationpriority: medium
ms.openlocfilehash: 26451d4fe3bea772584cbcefe3bba4c89599987e
ms.sourcegitcommit: fb7d95c7a5d47860918cd3602efdd33b69dcf2da
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/25/2019
ms.locfileid: "67365523"
---
# <a name="setting-the-start-type-value"></a>设置启动类型值


应将设置写入到 Windows 显示驱动程序模型 (WDDM) 开始运行按需在 Windows Vista 和更高版本，而不是在操作系统初始化过程中那样，仅仅在操作系统运行的显示器驱动程序使用的显示器驱动程序Windows Vista 之前。 此更改是由于清单和未出现在 Windows Vista 之前的操作系统上的基于映像的安装功能。 应设置为值**StartType**到服务的条目\_需\_而不是服务启动 (3)\_系统\_启动 (1)。

下面的示例演示一个服务安装部分的值与**StartType**条目设置为服务\_需\_开始以指示是否显示微型端口驱动程序已启动按需：

```inf
;
; Service Installation Section
;

[R200_Service_Inst]
ServiceType    = 1        ; SERVICE_KERNEL_DRIVER
StartType      = 3        ; SERVICE_DEMAND_START
ErrorControl   = 0        ; SERVICE_ERROR_IGNORE
LoadOrderGroup = Video
ServiceBinary  = %12%\r200.sys
```

详细了解与之关联的服务安装部分**AddService**指令，请参阅[ **INF AddService 指令**](https://docs.microsoft.com/windows-hardware/drivers/install/inf-addservice-directive)。

 

 





