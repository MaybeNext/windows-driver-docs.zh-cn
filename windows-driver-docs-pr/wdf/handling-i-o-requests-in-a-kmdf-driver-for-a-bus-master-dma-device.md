---
title: 在适用于总线主控 DMA 设备的 KMDF 驱动程序中处理 I/O 请求
description: 本部分中的主题介绍了如何使用 KMDF 驱动程序来处理 i/o 请求。 如果要编写实现系统模式 DMA 的 KMDF 驱动程序，请参阅支持系统模式 DMA。
ms.assetid: c94819c5-212d-404f-a7c7-b736e0832282
keywords:
- DMA 操作 WDK KMDF、i/o 请求
- 总线主控 DMA WDK KMDF、i/o 请求
- I/o 请求 WDK KMDF，DMA 设备
- 请求处理 WDK KMDF，DMA 设备
ms.date: 04/20/2017
ms.localizationpriority: medium
ms.openlocfilehash: 3f4d69a8c9a01529f6fd4bc1833264d4a5dd38e9
ms.sourcegitcommit: 4b7a6ac7c68e6ad6f27da5d1dc4deabd5d34b748
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2019
ms.locfileid: "72845222"
---
# <a name="handling-io-requests-in-a-kmdf-driver-for-a-bus-master-dma-device"></a>在适用于总线主控 DMA 设备的 KMDF 驱动程序中处理 I/O 请求


\[仅适用于 KMDF\]

本部分中的主题介绍了如何使用 KMDF 驱动程序来处理 i/o 请求。 如果要编写实现系统模式 DMA 的 KMDF 驱动程序，请参阅[支持系统模式 dma](supporting-system-mode-dma.md)。




在 KMDF 驱动程序中处理针对总线主机 DMA 设备的 i/o 请求需要使用驱动程序的几个事件回调函数中的代码，如下图所示：

![kmdf 驱动程序中的 dma 实现](images/dma-implementation-in-kmdf.png)

如上所示，与 DMA 相关的处理发生在四个阶段中：

1.  驱动程序的[*EvtDriverDeviceAdd*](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdfdriver/nc-wdfdriver-evt_wdf_driver_device_add)或[*EvtDevicePrepareHardware*](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdfdevice/nc-wdfdevice-evt_wdf_device_prepare_hardware)回调函数必须为设备[启用 DMA 事务](enabling-dma-transactions.md)，以便您的驱动程序可以使用框架的 dma 功能。 如果设备和驱动程序需要访问共享内存缓冲区，则相同的回调函数还必须[创建公用缓冲区](using-common-buffers.md)。

2.  当驱动程序收到要求设备执行 DMA 操作的 i/o 请求时，驱动程序的[请求处理](request-handlers.md)程序之一必须[创建并初始化新的 DMA 事务](creating-and-initializing-a-dma-transaction.md)。 （请注意，如果驱动程序[重用 DMA 事务对象](reusing-dma-transaction-objects.md)，则驱动程序的[*EvtDriverDeviceAdd*](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdfdriver/nc-wdfdriver-evt_wdf_driver_device_add)回调函数可以创建事务对象。）然后，请求处理程序必须[启动 DMA 事务](starting-a-dma-transaction.md)，以便框架能够在必要时开始将事务拆分为较小的 DMA 传输，并调用驱动程序的[*EvtProgramDma*](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdfdmatransaction/nc-wdfdmatransaction-evt_wdf_program_dma)回调函数。

3.  驱动程序的[*EvtProgramDma*](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdfdmatransaction/nc-wdfdmatransaction-evt_wdf_program_dma)回调函数[将 dma 硬件](programming-dma-hardware.md)用于单个 dma 传输并启用设备中断。

4.  当设备中断时，框架会调用驱动程序的[*EvtInterruptIsr*](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdfinterrupt/nc-wdfinterrupt-evt_wdf_interrupt_isr)回调函数，该函数可保存可变的设备信息并计划驱动程序的[*EvtInterruptDpc*](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdfinterrupt/nc-wdfinterrupt-evt_wdf_interrupt_dpc)回调函数的执行。

    在硬件完成对每个 DMA 传输的处理之后，驱动程序的[*EvtInterruptDpc*](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdfinterrupt/nc-wdfinterrupt-evt_wdf_interrupt_dpc)回调函数将[完成每个 DMA 传输](completing-a-dma-transfer.md)。 DMA 事务的最终传输完成后， *EvtInterruptDpc*回调函数[完成 dma 事务](completing-a-dma-transaction.md)。

驱动程序可以[重复使用其 DMA 事务对象](reusing-dma-transaction-objects.md)，以确保在内存资源不足时可以运行。

你的驱动程序可以提供一组回调函数来处理[DMA 特定的电源管理操作](supporting-power-management-for-dma-devices.md)。

某些驱动程序使用设备和驱动程序都可以访问的[常见缓冲区](using-common-buffers.md)。

 

 





