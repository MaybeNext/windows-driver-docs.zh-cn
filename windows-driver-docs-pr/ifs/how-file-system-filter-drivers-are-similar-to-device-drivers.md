---
title: 文件系统筛选器驱动程序与设备驱动程序的类似程度如何
description: 文件系统筛选器驱动程序与设备驱动程序的类似程度如何
ms.assetid: 7797239e-e0cc-4422-bcc6-31cfe6efd8e4
keywords:
- 筛选器驱动程序 WDK 文件系统，与设备驱动程序
- 文件系统筛选器驱动程序 WDK，与设备驱动程序
- 设备驱动程序 WDK 文件系统
ms.date: 04/20/2017
ms.localizationpriority: medium
ms.openlocfilehash: 2c4bc6fd3ab1f47469a45fe502c7a9095f75fce0
ms.sourcegitcommit: a33b7978e22d5bb9f65ca7056f955319049a2e4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/31/2019
ms.locfileid: "56565324"
---
# <a name="how-file-system-filter-drivers-are-similar-to-device-drivers"></a>文件系统筛选器驱动程序与设备驱动程序的类似程度如何


## <span id="ddk_how_file_system_filter_drivers_are_similar_to_device_drivers_if"></span><span id="DDK_HOW_FILE_SYSTEM_FILTER_DRIVERS_ARE_SIMILAR_TO_DEVICE_DRIVERS_IF"></span>


以下各小节介绍了一些文件系统筛选器驱动程序和 Microsoft Windows 操作系统中的设备驱动程序之间的相似之处。

### <a name="span-idsimilarstructurespanspan-idsimilarstructurespanspan-idsimilarstructurespansimilar-structure"></a><span id="Similar_Structure"></span><span id="similar_structure"></span><span id="SIMILAR_STRUCTURE"></span>相似的结构

设备驱动程序，如文件系统筛选器驱动程序具有[ **DriverEntry**](https://msdn.microsoft.com/library/windows/hardware/ff544113)，[调度](https://msdn.microsoft.com/library/windows/hardware/ff566407)，以及[I/O 完成](https://msdn.microsoft.com/library/windows/hardware/ff565398)例程。 它们调用许多设备驱动程序调用，同一个内核模式例程，并与它们相关联的设备 （即，文件系统卷） 的 I/O 请求中筛选出。

### <a name="span-idsimilarfunctionalityspanspan-idsimilarfunctionalityspanspan-idsimilarfunctionalityspansimilar-functionality"></a><span id="Similar_Functionality"></span><span id="similar_functionality"></span><span id="SIMILAR_FUNCTIONALITY"></span>类似的功能

由于文件系统筛选器驱动程序和设备驱动程序 I/O 系统的一部分，它们都接收[I/O 请求数据包](https://msdn.microsoft.com/library/windows/hardware/ff558771)(Irp) 并采取相应措施。

设备驱动程序，如文件系统筛选器驱动程序还可以创建其自己的 Irp 和将其发送到较低级别的驱动程序。

这两种类型的驱动程序可以 （通过使用回调函数） 注册通知的各种系统事件。

### <a name="span-idothersimilaritiesspanspan-idothersimilaritiesspanspan-idothersimilaritiesspanother-similarities"></a><span id="Other_Similarities"></span><span id="other_similarities"></span><span id="OTHER_SIMILARITIES"></span>其他的相似之处

文件系统筛选器驱动程序可以接收设备驱动程序，如[简介 I/O 控制代码](https://msdn.microsoft.com/library/windows/hardware/ff548059)(Ioctl)。 但是，文件系统筛选器驱动程序还可以接收-并定义-[文件系统控制代码](https://msdn.microsoft.com/library/windows/hardware/ff540367)(FSCTLs)。

设备驱动程序，如要在系统启动时加载，或要加载更高版本，系统启动过程完成后，可以配置文件系统筛选器驱动程序。

 

 



