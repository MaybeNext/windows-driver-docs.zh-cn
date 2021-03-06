---
title: 检索设备实例的状态和问题代码
description: 检索设备实例的状态和问题代码
ms.assetid: 22ca9ac2-fe67-427d-a6e4-f1d9cbbede52
ms.date: 04/20/2017
ms.localizationpriority: medium
ms.openlocfilehash: af76c971342ad2fdb429d608fe3fd641bc563173
ms.sourcegitcommit: fb7d95c7a5d47860918cd3602efdd33b69dcf2da
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/25/2019
ms.locfileid: "67378023"
---
# <a name="retrieving-the-status-and-problem-code-for-a-device-instance"></a>检索设备实例的状态和问题代码


在 Windows Vista 和更高版本的 Windows，[统一的设备属性模型](unified-device-property-model--windows-vista-and-later-.md)包括[设备状态属性和问题代码属性](https://docs.microsoft.com/previous-versions/ff542254(v=vs.85))。 统一的设备属性模型使用[属性键](property-keys.md)来表示这些属性。

Windows Server 2003、 Windows XP 和 Windows 2000 不支持属性键的属性的统一的模型，也不支持表示这些属性的相应注册表项值。 但是，通过调用检索相应信息[ **CM_Get_DevNode_Status** ](https://docs.microsoft.com/windows/desktop/api/cfgmgr32/nf-cfgmgr32-cm_get_devnode_status)函数。 若要保持与早期版本的 Windows 兼容性，Windows Vista 和更高版本还支持**CM_Get_DevNode_Status**。 但是，应使用统一的设备属性模型属性键来访问设备驱动程序属性。

属性的密钥标识符用于访问在 Windows Vista 和更高版本中的属性按列出的设备驱动程序属性。

有关如何使用属性键来访问在 Windows Vista 和更高版本的设备驱动程序属性的信息，请参阅[访问设备实例属性 （Windows Vista 和更高版本）](accessing-device-instance-properties--windows-vista-and-later-.md)。

若要访问 Windows Server 2003、 Windows XP 和 Windows 2000 上的设备实例的状态和问题代码，调用**CM_Get_DevNode_Status**并提供以下参数：

-   设置*pulStatus*到接收设备实例设置的状态位标志的 ULONG 类型化值的指针。 状态值可以是具有前缀"DN_"中定义的位标志的任意组合*Cfg.h*。

-   设置*pulProblemNumber*到接收的设备实例已设置的问题数的 ULONG 类型化值的指针。 问题数是一个具有前缀"CM_PROB_"中定义的常量*Cfg.h*。 **CM_Get_DevNode_Status** DN_HAS_PROBLEM 设置，才设置问题数*pulStatus*。

-   设置*dnDevInst*到为其检索状态和问题代码设备的设备实例句柄。

-   设置*ulFlags*为零。

如果在调用**CM_Get_DevNode_Status**成功， **CM_Get_DevNode_Status**检索请求的状态和设备实例的问题代码，并返回 CR_SUCCESS。 如果函数调用失败， **CM_Get_DevNode_Status**返回一个具有前缀"CR_"中定义的错误代码*Cfgmgr32.h*。

 

 





