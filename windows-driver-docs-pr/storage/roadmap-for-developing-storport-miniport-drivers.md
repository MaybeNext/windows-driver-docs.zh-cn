---
title: Storport 微型端口驱动程序开发路线图
description: Storport 微型端口驱动程序开发路线图
ms.assetid: 43a8f1ee-b2d3-4f97-b7e5-d59790ca6754
ms.date: 04/20/2017
ms.localizationpriority: medium
ms.openlocfilehash: d671327880d03c3c9c5c119dbc49428fa4515659
ms.sourcegitcommit: fb7d95c7a5d47860918cd3602efdd33b69dcf2da
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/25/2019
ms.locfileid: "67387171"
---
# <a name="roadmap-for-developing-storport-miniport-drivers"></a>Storport 微型端口驱动程序开发路线图


![示意图，带有文本"wdk"上一条高速公路上叠加的路线图](images/wdkroadmap-th.png)若要创建 storport 微型端口驱动程序，请执行以下步骤：

1.  **了解 Windows 体系结构和驱动程序。**

    务必了解驱动程序在 Windows 中的工作原理的基础知识。 了解基础知识将帮助您做出适当的设计决策，并可用于简化开发过程。 请参阅[的所有驱动程序开发人员概念](https://docs.microsoft.com/windows-hardware/drivers/gettingstarted/concepts-and-knowledge-for-all-driver-developers)。

2.  **了解 storport 微型端口驱动程序的基础知识。**

    若要了解 storport 微型端口驱动程序基础知识，请参阅[Windows 存储驱动程序体系结构](storage-driver-architecture.md)，[功能提供的 Storport](capabilities-provided-by-storport.md)，和[Storport 的接口与 Storport 微型端口驱动程序](storport-s-interface-with-storport-miniport-drivers.md)。

3.  **确定其他 storport 微型端口驱动程序的设计决策。**

    有关如何制定设计决策的信息，请参阅[功能提供的 Storport](capabilities-provided-by-storport.md)， [Storport 的存储类驱动程序接口](storport-s-interface-with-the-storage-class-driver.md)，[存储虚拟微型端口驱动程序：何时是否合适？](storage-virtual-miniport-drivers--when-are-they-appropriate-.md)，并[制定 SCSI 端口微型端口驱动程序使用 Storport](making-scsi-port-miniport-drivers-work-with-storport.md)。

4.  **了解有关在 Windows Vista 和更高版本操作系统的 storport 微型端口驱动程序。**

    请参阅[Storport 的历史记录](history-of-storport.md)Windows 驱动程序工具包 (WDK) 中。

5.  **了解有关 Windows 驱动程序生成、 测试和调试的进程和工具。**

    构建一个驱动程序不是与构建在用户模式应用程序相同。 请参阅[开发、 测试和部署驱动程序](https://docs.microsoft.com/windows-hardware/drivers)Windows 驱动程序生成、 调试和测试过程，驱动程序签名，和 Windows 徽标测试有关的信息。 请参阅[驱动程序开发工具](https://docs.microsoft.com/windows-hardware/drivers/devtest/index)有关生成、 测试、 验证和调试工具的信息。

6.  **查看 storport 微型端口驱动程序示例。**

    访问和查看 storport 微型端口驱动程序示例请参阅[Windows Driver Kit (WDK) 示例](https://go.microsoft.com/fwlink/p/?LinkId=618052)。

7.  **开发、 生成、 测试和调试 storport 微型端口驱动程序。**

    请参阅[构建一个驱动程序](https://docs.microsoft.com/windows-hardware/drivers/develop/building-a-driver)，[测试驱动程序](https://docs.microsoft.com/windows-hardware/drivers)，并[调试驱动程序](https://docs.microsoft.com/windows-hardware/drivers)有关迭代构建、 测试和调试信息。 此过程将有助于确保您构建适用的驱动程序。

8.  **创建 storport 微型端口驱动程序的驱动程序包。**

    有关详细信息，请参阅[创建驱动程序包](https://docs.microsoft.com/windows-hardware/drivers)。

9.  **签名和分发 storport 微型端口** **驱动程序。**

    最后一步是 （可选） 签名并分发驱动程序。 如果您的驱动程序满足 Windows 硬件认证为定义的质量标准，您可以通过 Microsoft Windows Update 计划分发。 有关详细信息，请参阅[分发驱动程序包](https://docs.microsoft.com/windows-hardware/drivers)。

这些是基本步骤。 其他步骤可能有必要在单独的驱动程序的需求。

 

 




