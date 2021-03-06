---
title: Windows 10 的蓝牙通用 Windows 驱动程序模型
description: 在 Windows 10 中，所有设备的蓝牙传输驱动程序接口聚合，并使用通用 Windows 驱动程序模型。
ms.assetid: E65A71D3-C0D2-4E13-9E19-1E6C6C1A172E
ms.date: 04/20/2017
ms.localizationpriority: medium
ms.openlocfilehash: 8eef5c6812ec27632b0c81dc3f09eb3c575d12c7
ms.sourcegitcommit: fb7d95c7a5d47860918cd3602efdd33b69dcf2da
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/25/2019
ms.locfileid: "67364605"
---
# <a name="bluetooth-universal-windows-driver-model-for-windows-10"></a>Windows 10 的蓝牙通用 Windows 驱动程序模型


在 Windows 10 中，所有设备的蓝牙传输驱动程序接口聚合，并使用通用 Windows 驱动程序模型。 你可以编写在所有 Windows 设备平台上运行的单个驱动程序。

蓝牙音频驱动程序接口区域针对 Windows 10 划分，并允许以下两个选项：

-   您可以编写适用于桌面和移动设备的新音频通用 Windows 驱动程序。
-   现有的 Windows Phone 8.1 蓝牙音频驱动程序将在 Windows 10 移动版上运行。

## <a name="span-idhowtowriteabluetoothuniversalwindowsdriverspanspan-idhowtowriteabluetoothuniversalwindowsdriverspanspan-idhowtowriteabluetoothuniversalwindowsdriverspanhow-to-write-a-bluetooth-universal-windows-driver"></a><span id="How_to_write_a_Bluetooth_Universal_Windows_driver"></span><span id="how_to_write_a_bluetooth_universal_windows_driver"></span><span id="HOW_TO_WRITE_A_BLUETOOTH_UNIVERSAL_WINDOWS_DRIVER"></span>如何编写蓝牙通用 Windows 驱动程序


若要编写蓝牙通用 Windows 驱动程序，请参阅[通用 Windows 驱动程序入门](https://docs.microsoft.com/windows-hardware/drivers)，并按照一节中的步骤*构建通用 Windows 驱动程序*构建通用Windows 驱动程序使用内核模式驱动程序 (KMDF) 模板。

然后，请参阅实现指南蓝牙设计和引用部分。

-   [蓝牙配置文件驱动程序](bluetooth-profile-drivers-overview.md)
-   [蓝牙设备参考](https://msdn.microsoft.com/library/windows/hardware/ff536585)

 

 





