---
title: 已检验版本和调试器
description: 已检验版本和调试器
ms.assetid: 851d9b5b-cd1c-4b1e-b3ec-d13645795705
keywords:
- 检查内部版本号 WDK，调试器
- 调试器 WDK 检查生成
- 主机计算机 WDK 检查生成
- 目标计算机 WDK 检查生成
- 空调制解调器电缆 WDK
ms.date: 04/20/2017
ms.localizationpriority: medium
ms.openlocfilehash: 62be0a7598133680490c9435e564d72a52c30deb
ms.sourcegitcommit: fb7d95c7a5d47860918cd3602efdd33b69dcf2da
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/25/2019
ms.locfileid: "67360929"
---
# <a name="the-checked-build-and-the-debugger"></a>已检验版本和调试器


## <span id="ddk_the_checked_build_and_the_debugger_tools"></span><span id="DDK_THE_CHECKED_BUILD_AND_THE_DEBUGGER_TOOLS"></span>


调试在 Windows 操作系统上的内核模式驱动程序的典型设置包括两个相连的计算机通过网络、 USB、 串行，或 1394年连接。 有关设置内核模式调试的信息，请参阅[Windows 调试](https://docs.microsoft.com/windows-hardware/drivers/debugger/index)。

*主机计算机*是调试器在运行的系统。 它应是稳定的系统，并且应始终运行操作系统的免费版本。

*目标计算机*是运行要测试的驱动程序。 它可以运行免费生成或调试内部版本。 对于更准确地调试已检验的版本是首选模型。

在主机计算机上运行调试器控制通过调试连接，建立在目标计算机。

 

 





