---
title: 在跟踪提供程序中使用 WPP 软件跟踪
description: 在跟踪提供程序中使用 WPP 软件跟踪
ms.assetid: e215a99b-5082-4e81-84b6-184a2fd4e270
keywords:
- Windows 软件跟踪预处理器 WDK，有关 WPP
- 跟踪 WDK，有关 WPP WPP 软件
ms.date: 04/20/2017
ms.localizationpriority: medium
ms.openlocfilehash: 9d0f5bda5d9026d4be87a79d2a31295f20a40006
ms.sourcegitcommit: fb7d95c7a5d47860918cd3602efdd33b69dcf2da
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/25/2019
ms.locfileid: "67381817"
---
# <a name="using-wpp-software-tracing-in-a-trace-provider"></a>在跟踪提供程序中使用 WPP 软件跟踪


## <span id="ddk_using_wpp_software_tracing_in_a_driver_tools"></span><span id="DDK_USING_WPP_SOFTWARE_TRACING_IN_A_DRIVER_TOOLS"></span>


若要使用 WPP 软件跟踪中的默认窗体[跟踪提供程序](trace-provider.md)，如内核模式驱动程序或用户模式应用程序，执行以下操作：

-   定义一个控件唯一标识 GUID[跟踪提供程序](trace-provider.md)。 提供程序在其定义中指定此 GUID [WPP\_控制\_GUID](https://docs.microsoft.com/previous-versions/windows/hardware/previsioning-framework/ff556186(v=vs.85))宏和中使用的相关的控件文件[Tracelog](tracelog.md)。

-   添加所需 WPP 相关 C 预处理器指令和 WPP 宏调用到提供程序的源文件，如中所述[添加到跟踪提供程序的 WPP 宏](adding-wpp-macros-to-a-trace-provider.md)并在[WPP 软件跟踪引用](https://docs.microsoft.com/previous-versions/windows/hardware/previsioning-framework/ff556205(v=vs.85))。

-   生成该驱动程序，如中所述[WPP 预处理器](wpp-preprocessor.md)。

-   使用其他工具进行软件跟踪，例如[TraceView](traceview.md)， [Tracelog](tracelog.md)， [Tracefmt](tracefmt.md)，以及[Tracepdb](tracepdb.md)配置、 启动和停止跟踪会话还可以显示和筛选跟踪消息。 这些工具包括在 Windows 驱动程序工具包 (WDK) 中\\工具\\跟踪目录。

 

 





