---
title: 安装分段筛选器
description: 安装分段筛选器
ms.assetid: 39f96c16-2408-460c-8aa3-08b6a6584bef
ms.date: 04/20/2017
ms.localizationpriority: medium
ms.openlocfilehash: e5d4168a7a93729ed5d605aa09f026b236419f3e
ms.sourcegitcommit: fb7d95c7a5d47860918cd3602efdd33b69dcf2da
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/25/2019
ms.locfileid: "67378939"
---
# <a name="installing-a-segmentation-filter"></a>安装分段筛选器





分段的筛选器应与 WIA 驱动程序一起安装。 若要执行此操作，必须对驱动程序的 INF 文件进行少量的新增功能。 下面的 INF 示例演示如何修改现有的驱动程序 INF 文件以包括分段筛选器。

```INF
[MyDriver.AddReg]
...
HKCR,CLSID\<UiClassId>\shellex\SegmentationFilter\<FilterClassId>
...
HKCR,CLSID\<FilterClassId>,,,"My Segmentation Filter"
HKCR,CLSID\<FilterClassId>\InProcServer32,,,%11%\Mysegfilter.dll
HKCR,CLSID\<FilterClassId>\InProcServer32,ThreadingModel,,"Both"
...
 
[MyDriver.CopyFiles]
...
Mysegfilter.dll
...
 
[SourceDisksFiles.x86]
...
Mysegfilter.dll=1
...
```

*&lt;UiClassId&gt;* 是值，以驱动程序返回的 WIA\_DIP\_UI\_CLSID 属性。 *&lt;FilterClassId&gt;* 分段的筛选器实现的类 id。 *Mysegfilter.dll*是包含分段筛选器实现的 DLL。

在设备中的第一个条目[ **INF AddReg 指令**](https://docs.microsoft.com/windows-hardware/drivers/install/inf-addreg-directive)寄存器分段作为扩展的驱动程序筛选器中，接下来的三项注册为 COM 组件的分段的筛选器。

如果驱动程序将使用由 Microsoft、 两个设备提供的 WIA 分段筛选器[ **INF CopyFiles 指令**](https://docs.microsoft.com/windows-hardware/drivers/install/inf-copyfiles-directive)， [ **INF SourceDisksFiles 部分** ](https://docs.microsoft.com/windows-hardware/drivers/install/inf-sourcedisksfiles-section)，也不需要的最后三个注册表项。 唯一要求是微型驱动程序实现 WIA\_IP\_分段属性。

COM **ThreadingModel**必须是**同时**。

有关 INF 文件的详细信息，请参阅[WIA 设备 INF 文件](inf-files-for-wia-devices.md)。

 

 




