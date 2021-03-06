---
title: 初始化和 DMA 缓冲区创建
description: 初始化和 DMA 缓冲区创建
ms.assetid: d84aed8a-9e22-4172-89c2-807b4e06108f
keywords:
- DMA 缓冲 WDK 显示，为 GDI 硬件加速创建
ms.date: 04/20/2017
ms.localizationpriority: medium
ms.openlocfilehash: 237d527943639e96aba271635a7e2085b99944a7
ms.sourcegitcommit: 4b7a6ac7c68e6ad6f27da5d1dc4deabd5d34b748
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2019
ms.locfileid: "72840380"
---
# <a name="initialization-and-dma-buffer-creation"></a>初始化和 DMA 缓冲区创建


## <span id="ddk_introduction_to_command_and_dma_buffers_gg"></span><span id="DDK_INTRODUCTION_TO_COMMAND_AND_DMA_BUFFERS_GG"></span>


若要指示 GPU 支持 GDI 硬件加速，则[**DriverEntry**](https://docs.microsoft.com/windows-hardware/drivers/display/driverentry-of-display-miniport-driver)函数的显示微型端口驱动程序的实现必须填写驱动程序的**DXGKDDIRENDERKM**成员[ **\_初始化\_数据**](https://docs.microsoft.com/windows-hardware/drivers/ddi/dispmprt/ns-dispmprt-_driver_initialization_data)结构，其中包含指向驱动程序实现的[**DxgkDdiRenderKm**](https://docs.microsoft.com/windows-hardware/drivers/ddi/d3dkmddi/nc-d3dkmddi-dxgkddi_renderkm)函数的指针。

DirectX 图形内核子系统将调用*DxgkDdiRenderKm*函数，以便从由操作系统提供的内核模式规范显示驱动程序（CDD）传递的命令缓冲区生成 DMA 缓冲区。

当 DirectX 图形内核子系统（*Dxgkrnl*）的显示端口驱动程序调用[**DxgkDdiCreateContext**](https://docs.microsoft.com/windows-hardware/drivers/ddi/d3dkmddi/nc-d3dkmddi-dxgkddi_createcontext)函数时，它会将[**pCreateContext**](https://docs.microsoft.com/windows-hardware/drivers/ddi/d3dkmddi/ns-d3dkmddi-_dxgkarg_createcontext)-&gt;[**标志**](https://docs.microsoft.com/windows-hardware/drivers/ddi/d3dkmddi/ns-d3dkmddi-_dxgk_createcontextflags)-&gt;**GdiContext**用于指示 GDI 硬件加速所使用的上下文的成员。

同样，当显示端口驱动程序调用[**DxgkDdiCreateDevice**](https://docs.microsoft.com/windows-hardware/drivers/ddi/d3dkmddi/nc-d3dkmddi-dxgkddi_createdevice)函数时，它会将[**pCreateDevice**](https://docs.microsoft.com/windows-hardware/drivers/ddi/d3dkmddi/ns-d3dkmddi-_dxgkarg_createdevice)-设置&gt;[**标志**](https://docs.microsoft.com/windows-hardware/drivers/ddi/d3dkmddi/ns-d3dkmddi-_dxgk_createdeviceflags)-&gt;**GdiDevice**成员，以指示用于 GDI 的设备硬件加速。

 

 





