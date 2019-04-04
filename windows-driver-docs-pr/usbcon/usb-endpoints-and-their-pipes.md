---
Description: A USB device has endpoints that are used to for data transfers.
title: USB 终结点和其管道
ms.date: 04/20/2017
ms.localizationpriority: medium
ms.openlocfilehash: f6e04a27d03fe54fcd80370d8ae6e40b66b22566
ms.sourcegitcommit: a33b7978e22d5bb9f65ca7056f955319049a2e4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/31/2019
ms.locfileid: "56556168"
---
# <a name="usb-endpoints-and-their-pipes"></a>USB 终结点和其管道


**摘要**

-   终结点是设备; 上的硬件管道是宿主端的软件。
-   未配置终结点;管道配置为传输
-   主机发送或接收到或从管道的数据。

USB 设备都有用于数据传输到的终结点。 在主机端，终结点都是管道。 本主题区分这些两个词之间。

## <a name="usb-endpoint"></a>USB 终结点


*终结点*是 USB 设备上的缓冲区。 终结点是一个术语，它与自身独立于主机操作系统的硬件。 主机可以发送和接收数据，该缓冲区。 终结点可划分为控制和数据的终结点。

每个 USB 设备必须提供至少一个控制终结点位于名为默认终结点或 Endpoint0 地址 0。 此终结点是双向的。 也就是说，主机可以将数据发送到终结点和一次传输中从其接收数据。 控制传输的目的是使宿主能够获取设备信息，请配置设备，或执行是唯一的设备的控制操作。

数据终结点是可选的用于将数据传输。 它们是单向的具有类型 （控件、 中断、 大容量等时） 和其他属性。 所有这些属性一个终结点描述符中所述 （请参阅标准 USB 描述符）。

在 USB 术语中，终结点 （以及传输到或从它们） 的方向基于主机。 因此，在始终是指从设备到主机的传输和 OUT 始终是指传输从主机到设备。 USB 设备还可以支持的双向数据传输的控件。

在设备上的终结点进行分组到功能接口和一组接口构成了为设备配置。 有关详细信息，请参阅 USB 设备布局。

在之前配置设备的终结点信息时或在所选内容的一项备用设置，可以查看主机软件。 将循环访问所有这些接口，然后通过每个接口设置的列表，并查看每个终结点的属性或整个组设置中的终结点。 查看终结点信息不会影响设备的配置的状态。

## <a name="usb-pipes"></a>USB 管道


USB 设备和 USB 宿主通过调用一种抽象之间传输数据*管道*。 管道是纯粹的软件术语。 管道与终结点在设备上，并且该终结点具有地址。 管道另一端始终是主控制器。

或者通过选择配置配置设备和接口的备用时，会打开一个终结点的管道设置。 因此，它们成为 I/O 操作的目标。 管道都有一个终结点的所有属性，但它处于活动状态，可用来与主机通信。

未配置的终结点称为终结点，而配置的终结点调用管道。

![usb 管道和终结点](images/endpoints.png)

## <a name="related-topics"></a>相关主题
[所有 USB 开发人员的概念](usb-concepts-for-all-developers.md)  


