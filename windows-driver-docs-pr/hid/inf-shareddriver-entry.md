---
title: INF SharedDriver 条目
description: INF SharedDriver 条目
ms.assetid: 36d094b4-481d-41bb-b034-345b0743456e
keywords:
- INF 文件 WDK 非 HID 键盘/鼠标
- SharedDriver 条目 WDK 非 HID 键盘/鼠标
ms.date: 04/20/2017
ms.localizationpriority: medium
ms.openlocfilehash: 8e310ae8ba831d3577ba55c52c2b3bda2df8d800
ms.sourcegitcommit: fb7d95c7a5d47860918cd3602efdd33b69dcf2da
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/25/2019
ms.locfileid: "67363547"
---
# <a name="inf-shareddriver-entry"></a>INF SharedDriver 条目





**\[ControlFlags\]**

<em>SharedDriver</em> **=** <em>安装的部分名称</em>***，***<em>警告文本字符串</em>之前键盘或鼠标类安装程序安装 PS/2 设备，它会检查*SharedDriver*中的条目[INF **ControlFlags**部分](https://docs.microsoft.com/windows-hardware/drivers/install/inf-controlflags-section)设备。 如果存在此类条目值，类安装程序将通过显示警告文本字符串，来通知用户，并为用户提供选项来取消更改 PS/2 端口驱动程序。

### <a name="entries-and-values"></a>条目和值

<a href="" id="shareddriver"></a>*SharedDriver*  
将指定的 ps/2 键盘和鼠标设备共享的设备驱动程序。

<a href="" id="install-section-name"></a>*install-section-name*  
指定的设备*DDInstall*部分。

<a href="" id="warning-text-string"></a>*warning-text-string*  
指定类安装程序用于向用户发出警告然后再更改 PS/2 端口驱动程序的字符串。

 

 




