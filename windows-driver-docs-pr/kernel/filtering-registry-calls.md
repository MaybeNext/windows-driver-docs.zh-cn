---
title: 筛选注册表调用
description: 筛选注册表调用
ms.assetid: 6b35c3a0-4ece-4101-b348-e71f5cccf0c8
keywords:
- 筛选注册表调用 WDK 内核
- 注册表筛选驱动程序 WDK 内核
- RegistryCallback
- 筛选注册表调用 WDK 内核，关于筛选注册表调用
- 注册表筛选驱动程序 WDK 内核，关于筛选注册表调用
ms.date: 06/16/2017
ms.localizationpriority: medium
ms.openlocfilehash: ca5d0791cd6e1eea41ecdef1af956d55f3339e52
ms.sourcegitcommit: 4b7a6ac7c68e6ad6f27da5d1dc4deabd5d34b748
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2019
ms.locfileid: "72838692"
---
# <a name="filtering-registry-calls"></a>筛选注册表调用


*注册表筛选驱动程序*是任何筛选注册表调用的内核模式驱动程序，如防病毒软件包的驱动程序组件。 用于实现注册表的配置管理器允许注册表筛选驱动程序筛选任何线程对注册表功能的调用。 Microsoft Windows XP 中首次支持对注册表调用进行筛选。

在 Windows XP 中，注册表筛选驱动程序可以调用[**CmRegisterCallback**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdm/nf-wdm-cmregistercallback)来注册[*RegistryCallback*](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdm/nc-wdm-ex_callback_function)例程，并使用[**CmUnRegisterCallback**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdm/nf-wdm-cmunregistercallback)注册回调例程。 在 configuration manager 处理操作之前， *RegistryCallback*例程会接收每个注册表操作的通知。 一组**REG\_*XXX*\_密钥\_信息**数据结构包含有关每个注册表操作的信息。 *RegistryCallback*例程会阻止注册表操作。 当配置管理器已完成创建或打开注册表项时，回调例程还会收到通知。

Windows Server 2003 提供了额外的完成通知。

Windows Vista 提供了以下附加注册表筛选功能：

-   注册表筛选驱动程序可以在驱动程序堆栈中分层，堆栈中的每个驱动程序都可以筛选注册表操作。

-   **CmRegisterCallback**例程由[**CmRegisterCallbackEx**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdm/nf-wdm-cmregistercallbackex)例程替换。

-   驱动程序可以完全处理注册表操作（或将请求的操作重定向到其他操作），并阻止 configuration manager 处理该操作。

-   驱动程序可以将上下文信息分配给单独的注册表操作或密钥对象。

-   驱动程序可以修改注册表操作的输出参数和返回值。

-   其他成员已添加到所有**REG\_*XXX*\_密钥\_信息**数据结构中。

-   驱动程序接收其他注册表操作的通知。

有关驱动程序可以对每个版本的 Windows 进行筛选的注册表操作的列表，请参阅[**REG\_通知\_类**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdm/ne-wdm-_reg_notify_class)。

若要了解有关筛选注册表调用的详细信息，请参阅以下主题：

[注册通知](registering-for-notifications.md)

[处理通知](handling-notifications.md)

[支持分层注册表筛选驱动程序](supporting-layered-registry-filtering-drivers.md)

[指定上下文信息](specifying-context-information.md)

[获取其他注册表信息](obtaining-additional-registry-information.md)

[注册表通知中的密钥对象指针无效](invalid-key-object-pointers-in-registry-notifications.md)

[筛选应用程序配置单元上的注册表操作](filtering-registry-operations-on-application-hives.md)

 

 




