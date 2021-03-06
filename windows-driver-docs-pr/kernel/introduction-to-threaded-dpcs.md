---
title: 线程 DPC 简介
description: 线程 DPC 简介
ms.assetid: 891a8a52-83ff-400a-9477-8edca1b9a83c
keywords:
- 线程 Dpc WDK 内核
- 实时线程 WDK 内核
- 已抢占 Dpc WDK 内核
ms.date: 06/16/2017
ms.localizationpriority: medium
ms.openlocfilehash: 66466f956f520d0e381263b42c9900cd1bc01f57
ms.sourcegitcommit: 4b7a6ac7c68e6ad6f27da5d1dc4deabd5d34b748
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2019
ms.locfileid: "72838617"
---
# <a name="introduction-to-threaded-dpcs"></a>线程 DPC 简介





线程 Dpc 适用于 Windows Vista 和更高版本的 Windows。

*线程 dpc*是指系统以 IRQL = 被动\_级别执行的 dpc。 线程 Dpc 默认情况下处于启用状态，但你可以通过将**HKLM\\System\\CCS\\Control\\SessionManager\\内核\\ThreadDpcEnable**注册表项设置为零来禁用它们。 禁用线程 Dpc 后，它们将作为普通 Dpc 来执行。

普通 DPC 抢先于所有线程的执行，不能被线程或其他 DPC 抢占。 如果系统中有大量普通 Dpc 处于排队状态，或者其中一个 Dpc 长时间运行，则每个线程都将在任意长时间内保持暂停状态。 因此，每个普通 DPC 会增加系统延迟，这可能会影响对时间敏感的应用程序（如音频或视频播放）的性能。

相反，可以使用普通的 DPC 而不是其他线程来抢占线程 DPC。 因此，除非特定 DPC 不能被抢占，甚至不能使用其他 DPC，否则应该使用线程 Dpc，而不是普通 dpc。

系统将线程 Dpc （和普通 Dpc）表示为[**KDPC**](https://docs.microsoft.com/windows-hardware/drivers/kernel/eprocess)结构。 若要为线程化 DPC 初始化**KDPC**结构，请调用[**KeInitializeThreadedDpc**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdm/nf-wdm-keinitializethreadeddpc)例程，并向其传递执行 DPC 操作的[*CustomThreadedDpc*](https://msdn.microsoft.com/library/windows/hardware/ff542976)例程。

由于*CustomThreadedDpc*例程可以在被动\_级别执行或调度\_级别，因此必须确保*CustomThreadedDpc*例程在两个 IRQLs 上正确同步。 有关如何执行此操作的详细信息，请参阅[同步和线程 dpc](synchronization-and-threaded-dpcs.md)。

此外，还必须确保*CustomThreadedDpc*例程服从调度\_级别代码的所有限制。 如果启用了线程 Dpc，它们会以 IRQL = 被动\_级别运行，但仍受与普通 Dpc 相同的限制。 在线程 DPC 中执行的所有代码（包括*CustomThreadedDpc*例程调用的所有函数）必须符合 DPC 环境的限制。 例如，代码不得在被动级同步对象（如[KEVENT 对象](defining-and-using-an-event-object.md)）上阻塞。 大多数现有的设备堆栈（如网络、存储和 USB）不支持线程 DPC 处理，如果检测到它们在被动\_级别调用，它们可能会被阻止。 由于类似的原因，[内核模式驱动程序框架](https://docs.microsoft.com/windows-hardware/drivers/wdf/what-s-new-for-wdf-drivers)（KMDF）不支持线程化 dpc 处理，KMDF 驱动程序不应尝试使用线程 dpc。 有关 DPC 环境的详细信息，请参阅[编写 DPC 例程](writing-dpc-routines.md)。

若要将线程 DPC 添加到 DPC 队列，请调用[**KeInsertQueueDpc**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdm/nf-wdm-keinsertqueuedpc)。 若要从队列中删除线程化 DPC，请调用[**KeRemoveQueueDpc**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdm/nf-wdm-keremovequeuedpc)。

 

 




