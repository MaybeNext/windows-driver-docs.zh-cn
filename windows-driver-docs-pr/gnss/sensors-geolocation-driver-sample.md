---
title: Windows 8.1 的地理位置驱动程序示例
description: Windows 8.1 的地理位置示例驱动程序演示了全球定位系统 (GPS) 设备的传感器驱动程序。
ms.assetid: 2675DB47-B973-419C-930D-1F1B9D65E42D
keywords:
- GPS
- 地理位置驱动程序
- GPS 驱动程序
- 单选管理 API
- 单选状态更改
- 传感器驱动程序
- UMDF 传感器驱动程序
ms.date: 04/20/2017
ms.localizationpriority: medium
ms.openlocfilehash: 214bae0a5ffe6a2ae46afdb67c98d205ec80ecf2
ms.sourcegitcommit: fb7d95c7a5d47860918cd3602efdd33b69dcf2da
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/25/2019
ms.locfileid: "67363624"
---
# <a name="geolocation-driver-sample-for-windows-81"></a>Windows 8.1 的地理位置驱动程序示例

> [!IMPORTANT] 
> 已弃用此文档和 Windows 8.1 的地理位置驱动程序示例。

Windows 8.1 的地理位置示例驱动程序演示了全球定位系统 (GPS) 设备的传感器驱动程序。 此驱动程序不会连接到硬件;否则，它是完全符合构建 UMDF 传感器驱动程序的最佳实践。 而不是发送实际的坐标，本示例模拟的传感器，发出海拔高度、 纬度、 经度和其他模拟的 GPS 数据。 此外，此示例会发出可测试和调试时的时间戳。

此示例具有三个用途：首先，它演示了 UMDF 传感器驱动程序所需的最小功能。 其次，它提供了其生成有效的驱动程序的主干。 第三，它包括像 GPS 这样的设备提供单选状态更改通知单选管理 API 的支持。

## <a name="related-topics"></a>相关主题
[传感器诊断工具](https://docs.microsoft.com/windows-hardware/drivers/sensors/the-sensor-diagnostic-tool)  
[编写位置传感器驱动程序](writing-a-location-sensor-driver.md)  
[编写传感器设备驱动程序](https://docs.microsoft.com/windows-hardware/drivers/sensors/writing-a-sensor-device-driver)  



