---
title: INF 文件概述
description: INF 文件概述
ms.assetid: 94682cba-1f68-416f-af74-99ede81eadc7
keywords:
- INF 文件 WDK 设备安装
- INF 文件 WDK 设备安装，创建
- 设备设置 WDK 设备安装，INF 文件
- 设备安装 WDK、INF 文件
- 安装设备 WDK、INF 文件
- 使用 INF 文件安装驱动程序
ms.date: 04/20/2017
ms.localizationpriority: High
ms.openlocfilehash: 78dfa6c2a5df5e01417f0bf53275fbe3a1c4a98d
ms.sourcegitcommit: c73954a5909ec8c7e189f77fd5813f2eb749687c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/07/2019
ms.locfileid: "72007587"
---
# <a name="overview-of-inf-files"></a>INF 文件概述

Windows 使用安装信息（INF）文件安装设备的下列组件：

-   支持设备的一个或多个驱动程序。

-   设备特定的配置或设置，使设备联机。

INF 文件是包含[设备安装组件](https://docs.microsoft.com/previous-versions/ff541277(v=vs.85))用于安装驱动程序的所有信息的文本文件。 Windows 使用 INF 文件安装驱动程序。 此信息包括：

-   驱动程序名称和位置
-   驱动程序版本信息
-   注册表信息

可以使用*INX*文件自动创建 INF 文件。 INX 文件是一个 INF 文件，其中包含表示版本信息的字符串变量。 Build 实用工具和[Stampinf](https://docs.microsoft.com/windows-hardware/drivers/devtest/stampinf)工具将 INX 文件中的字符串变量替换为表示特定硬件体系结构或 framework 版本的文本字符串。 有关 INX 文件的详细信息，请参阅[使用 INX 文件创建 INF 文件](https://docs.microsoft.com/windows-hardware/drivers/wdf/using-inx-files-to-create-inf-files)。


有关 INF 文件格式的完整说明，请参阅[Inf 文件部分和指令](inf-file-sections-and-directives.md)。
