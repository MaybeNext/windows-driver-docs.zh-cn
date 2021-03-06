---
title: 简介
description: 简介
ms.assetid: 0AEFA19D-C270-4777-8C08-E6056FBB6BC5
ms.date: 10/08/2019
ms.topic: article
ms.prod: windows-hardware
ms.technology: windows-devices
ms.openlocfilehash: 1524a7955611caef1238b87ed61ca290b366b65b
ms.sourcegitcommit: 0610366df5de756bf8aa6bfc631eba5e3cd84578
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/11/2019
ms.locfileid: "72262177"
---
# <a name="storage-driver-design-guide"></a>存储驱动程序设计指南

存储驱动程序包括[类](storage-class-drivers.md)、[端口](storage-port-drivers.md)、[微型端口](storage-miniport-drivers.md)和[筛选器](storage-filter-drivers.md)驱动程序。 通常情况下，设备供应商会为特定的适配器或适配器类型实现微型端口驱动程序。 可以定义一个新的存储类，并为其开发新的类驱动程序，尽管这不常见。 Windows 中的存储类包括磁盘类、CDROM 类、USB 存储类和加密驱动器类。 存储驱动程序开发通常仅限于编写一个适用于 [StorPort](storport-driver-overview.md) 端口驱动程序的微型端口驱动程序。

其他类型的存储设备驱动程序包括安全[接收器](storage-silo-drivers.md)驱动程序和特定于设备且适合多路径 I/O 的模块 (DSM)。 开发 [WMI](https://docs.microsoft.com/windows-hardware/drivers/storage/storage-wmi-classes) 提供程序作为驱动程序的控制接口是为了进行存储管理。

该存储驱动程序设计指南包含以下部分：

* [开发 Windows 存储驱动程序的路线图](roadmap-for-developing-storage-drivers.md)
* [Storport 微型端口驱动程序开发路线图](roadmap-for-developing-storport-miniport-drivers.md)  
* [存储驱动程序](storage-drivers.md)  
* [存储类驱动程序](storage-class-drivers.md)  
* [存储端口驱动程序](storage-port-drivers.md)  
* [存储器微型端口驱动程序](storage-miniport-drivers.md)  
* [存储器虚拟微型端口驱动程序](storage-virtual-miniport-drivers.md)  
* [存储筛选器驱动程序](storage-filter-drivers.md)  
* [故障转储筛选器驱动程序](crash-dump-filter-drivers.md)  
* [存储接收器驱动程序](storage-silo-drivers.md)  
* [CD-ROM 驱动程序](cd-rom-drivers.md)  
* [磁带驱动程序](tape-drivers-overview.md)  
* [更换器驱动程序](changer-drivers.md)  
* [存储方案](storage-scenarios.md)  

## <a name="samples"></a>示例

若要了解如何开发可以运行的存储驱动程序，比较实际的方法是研究示例。 GitHub 上提供[示例存储驱动程序](https://github.com/Microsoft/Windows-driver-samples)。

## <a name="driver-verification-for-storport"></a>StorPort 的驱动程序验证

在驱动程序开发过程中使用代码分析工具并进行测试有助于捕获存储驱动程序中的性能问题和缺陷。 [静态驱动程序验证程序 (SDV)](https://docs.microsoft.com/windows-hardware/drivers/devtest/static-driver-verifier) 工具可用于发现存储驱动程序代码中的缺陷。 SDV 中包含的符合性[规则](https://docs.microsoft.com/windows-hardware/drivers/devtest/declaring-functions-by-using-function-role-types-for-storport-drivers)用于验证微型端口驱动程序是否正确使用了 StorPort 例程。
