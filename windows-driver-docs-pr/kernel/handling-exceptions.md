---
title: 处理异常
description: 处理异常
ms.assetid: 20040d86-5088-48ec-a5b9-54760d143871
keywords:
- 结构化异常处理 WDK 内核
- 异常 WDK 内核
- 访问冲突 WDK 内核
- 硬件定义异常 WDK 内核
- 软件定义的异常 WDK 内核
- 错误 WDK 内核
- 防护页冲突 WDK 内核
- 页读取错误 WDK 内核
ms.date: 06/16/2017
ms.localizationpriority: medium
ms.openlocfilehash: 3038f0d5490ce44e1ab4ddcb99d140627548ca03
ms.sourcegitcommit: 4b7a6ac7c68e6ad6f27da5d1dc4deabd5d34b748
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2019
ms.locfileid: "72836552"
---
# <a name="handling-exceptions"></a>处理异常





操作系统使用结构化异常处理来指示特定类型的错误。 驱动程序调用的例程可能会引发驱动程序必须处理的异常。

系统捕获以下一般类型的异常：

1.  硬件定义的故障或陷阱，如，

    -   访问冲突（见下文）
    -   数据类型 misalignments （例如，在奇数字节边界上对齐的16位实体）
    -   非法和特权说明
    -   锁定顺序无效（尝试在代码的互锁部分中执行无效的指令序列）
    -   整数除以零和溢出
    -   浮点除以零、溢出、下溢和保留操作数
    -   断点和单步执行（用于支持调试器）

2.  系统软件定义的异常，如，

    -   保护页冲突（尝试在保护页内的某个位置加载或存储数据）
    -   页读取错误（尝试将页面读入内存并遇到并发 i/o 错误）

*访问冲突*是指尝试在当前页面保护设置下不允许的页面上执行操作。 在下列情况下会发生访问冲突：

-   读取或写入操作无效，如写入只读页面。

-   访问超出当前程序地址空间限制的内存（称为长度冲突）。

-   访问当前驻留但专门用于系统组件的页面。 例如，不允许用户模式代码访问内核正在使用的页。

如果某个操作可能导致异常，则驱动程序应将此操作包含在**try/except**块中。 用户模式下的位置访问是异常的典型原因。 例如， [**ProbeForWrite**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdm/nf-wdm-probeforwrite)例程检查驱动程序是否可以实际写入用户模式缓冲区。 如果不能，则例程将引发状态\_访问\_冲突异常。 在下面的代码示例中，驱动程序在**try/except**中调用**ProbeForWrite** ，以便它可以处理生成的异常（如果应该发生）。

```cpp
try {
    ...
    ProbeForWrite(Buffer, BufferSize, BufferAlignment);
 
    /* Note that any access (not just the probe, which must come first,
     * by the way) to Buffer must also be within a try-except.
     */
    ...
} except (EXCEPTION_EXECUTE_HANDLER) {
    /* Error handling code */
    ...
}
```

驱动程序必须处理引发的任何异常。 未处理的异常会导致系统检查错误。 导致引发异常的驱动程序必须对其进行处理：较低级别的驱动程序无法依赖较高级别的驱动程序来处理该异常。

驱动程序可以通过使用[**ExRaiseAccessViolation**](https://docs.microsoft.com/windows-hardware/drivers/ddi/ntddk/nf-ntddk-exraiseaccessviolation)、 [**ExRaiseDatatypeMisalignment**](https://docs.microsoft.com/windows-hardware/drivers/ddi/ntddk/nf-ntddk-exraisedatatypemisalignment)或[**ExRaiseStatus**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdm/nf-wdm-exraisestatus)例程直接引发异常。 驱动程序必须处理这些例程引发的任何异常。

下面是部分例程列表，至少在某些情况下，可能会引发异常：

-   [**MmMapLockedPages**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdm/nf-wdm-mmmaplockedpages)

-   [**MmProbeAndLockPages**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdm/nf-wdm-mmprobeandlockpages)

-   [**ProbeForRead**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdm/nf-wdm-probeforread)

-   [**ProbeForWrite**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdm/nf-wdm-probeforwrite)

对用户模式缓冲区的内存访问也可能导致访问冲突。 有关详细信息，请参阅[引用用户空间地址中的错误](errors-in-referencing-user-space-addresses.md)。

请注意，结构化异常处理与C++异常截然不同。 内核不支持C++异常。

有关结构化异常处理的详细信息，请参阅 Microsoft Windows SDK 和 Visual Studio 文档。

 

 




