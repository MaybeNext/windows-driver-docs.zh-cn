---
title: 开发 WIA 视频驱动程序
description: 开发 WIA 视频驱动程序
ms.assetid: 3cf14fd3-1dfa-480e-a69c-c4d2c196a504
ms.date: 04/20/2017
ms.localizationpriority: medium
ms.openlocfilehash: 3bc4ada8af6ec6090ddd3b3b340ebc41412b9cd1
ms.sourcegitcommit: fb7d95c7a5d47860918cd3602efdd33b69dcf2da
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/25/2019
ms.locfileid: "67353816"
---
# <a name="developing-a-wia-video-driver"></a>开发 WIA 视频驱动程序





WIA 支持视频和视频摄像机。 要使用 WIA 的摄像机应使用随 Windows Me、 Windows XP 和更高版本操作系统的版本中，或开发 DirectShow 视频驱动程序的视频驱动程序。 WIA 依赖于 DirectShow 获取映像仍对视频流中。

仅几个对的 INF 文件的修改 DirectShow 驱动程序所需的 WIA 以将它识别为受支持的照相机。 必要的更改是：

```INF
[Device]
Include= sti.inf
Needs= STI.WIAVideo.Registration
SubClass=StillImage
DeviceType=3
DeviceSubType=0x1
Capabilities=0x00000031
ICMProfiles="sRGB Color Space Profile.icm"
```

如果没有进行这些新增功能 WIA 将无法识别该设备。 请务必*添加*INF 文件对这些更改。 不要使用仅以下行替换 INF 文件。

有关如何支持的示例从摄像机 USBCAMD 模型使用从您的驱动程序仍处于 pin WIA 请参阅[USB-Based 照相机，摄像机带有捕获按钮](https://docs.microsoft.com/windows-hardware/drivers/stream/usb-based-camera-with-a-capture-button)。

 

 




