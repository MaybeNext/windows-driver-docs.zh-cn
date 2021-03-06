---
title: 在 UMDF 1.x 驱动程序中读取设备注册表和写入到设备注册表
description: 在 UMDF 1.x 驱动程序中读取设备注册表和写入到设备注册表
ms.assetid: A0640E60-B0DF-4CAD-B292-CC1875EF7F7D
ms.date: 04/20/2017
ms.localizationpriority: medium
ms.openlocfilehash: 7e4803eb751b22c26475d62868515d37641faa8a
ms.sourcegitcommit: d30691c8276f7dddd3f8333e84744ddeea1e1020
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/19/2019
ms.locfileid: "75210867"
---
# <a name="reading-and-writing-to-device-registers-in-umdf-1x-drivers"></a>在 UMDF 1.x 驱动程序中读取设备注册表和写入到设备注册表


[!include[UMDF 1 Deprecation](../includes/umdf-1-deprecation.md)]

从 UMDF 版本1.11 开始，该框架提供了一组用于访问内存空间和 i/o 端口空间中的寄存器的例程。 [UMDF 寄存器/端口访问例程](https://docs.microsoft.com/windows-hardware/drivers/ddi/wudfddi/)非常类似于内核模式驱动程序使用的 HAL 例程。 当驱动程序具有在[UMDF 驱动程序中查找和映射硬件资源](https://docs.microsoft.com/windows-hardware/drivers/wdf/finding-and-mapping-hardware-resources-in-umdf-1-x-drivers)中所述的映射寄存器后，驱动程序将使用读/写\_将\_XXX 例程注册到各个寄存器。 对于 i/o 端口，驱动程序会将读/写\_端口称为\_Xxx 例程。

此示例演示如何写入内存映射寄存器。

```cpp
VOID
CMyQueue::WriteToDevice(
    __in IWDFDevice3* pWdfDevice,
    __in UCHAR Value
    )
{
    //
    // Write the UCHAR value at offset 2 from register base
    //
    WRITE_REGISTER_UCHAR(pWdfDevice, 
                      (m_MyDevice->m_RegBase)+2, 
                       Value);
}
```

默认情况下，UMDF 使用系统调用来访问映射到内存空间或 i/o 端口空间中的寄存器。 I/o 端口空间中的寄存器始终通过系统调用进行访问。 但是，在访问内存映射寄存器时，UMDF 驱动程序会通过将 INF 指令**UmdfRegisterAccessMode**设置为**RegisterAccessUsingUserModeMapping**，使框架将内存映射寄存器映射到用户模式地址空间。 出于性能方面的考虑，某些驱动程序可能需要执行此操作。 有关 UMDF INF 指令的完整列表，请参阅[在 INF 文件中指定 WDF 指令](specifying-wdf-directives-in-inf-files.md)。

驱动程序应使用读/写\_注册\_Xxx 例程，即使它已将寄存器映射到用户模式。 这些例程验证驱动程序输入，并确保该驱动程序不会请求访问无效位置。 通常，驱动程序可能需要直接访问用户模式映射寄存器，而无需使用这些例程。 要执行此操作，驱动程序会通过对映射基址调用[**IWDFDevice3：： GetHardwareRegisterMappedAddress**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wudfddi/nf-wudfddi-iwdfdevice3-gethardwareregistermappedaddress)来检索用户模式映射地址。 因为 UMDF 不验证以这种方式执行的读取和写入访问，因此不建议使用此方法来注册访问。

 

 





