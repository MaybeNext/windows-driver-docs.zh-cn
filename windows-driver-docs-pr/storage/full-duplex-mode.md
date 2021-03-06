---
title: 全双工模式
description: 全双工模式
ms.assetid: 01e3388d-d568-4476-9ff0-2125acafb841
ms.date: 04/20/2017
ms.localizationpriority: medium
ms.openlocfilehash: a2edef06203a4e9efec7f06244867ebd83186c36
ms.sourcegitcommit: 4b7a6ac7c68e6ad6f27da5d1dc4deabd5d34b748
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2019
ms.locfileid: "72843406"
---
# <a name="full-duplex-mode"></a>全双工模式


## <span id="ddk_full_duplex_mode_kg"></span><span id="DDK_FULL_DUPLEX_MODE_KG"></span>


Storport 驱动程序支持专门为高性能总线定制的 i/o 模型。 此 i/o 模型允许微型端口驱动程序在全双工模式下运行，这意味着，微型端口驱动程序可以将新请求添加到其队列中（即使正在完成其他请求）。 此外，在全双工模式下，微型端口驱动程序不必同步其[**StartIo**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdm/nc-wdm-driver_startio)和中断服务例程的执行。 这可能导致显著的性能增强。 但是，小型端口驱动程序必须设计为利用全双工模式，因为在默认情况下，Storport 以半双工模式运行。

微型端口驱动程序必须将 Storport 配置为在执行其[**HwStorFindAdapter**](https://docs.microsoft.com/windows-hardware/drivers/ddi/storport/nc-storport-hw_find_adapter)例程时以全双工模式运行。 为此，可将微型端口驱动程序的[**端口\_配置\_信息（STORPORT）** ](https://docs.microsoft.com/previous-versions/windows/hardware/drivers/ff563901(v=vs.85))结构的**SynchronizationModel**成员初始化为**StorSynchronizeFullDuplex**。

 

 




