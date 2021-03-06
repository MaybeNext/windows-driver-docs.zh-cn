---
title: 纹理格式列表
description: 纹理格式列表
ms.assetid: 5e60d6e3-d0a2-4b52-86cb-06de839f970a
keywords:
- DirectX 8.0 发行说明 WDK Windows 2000 显示，纹理格式列表
- 纹理格式列出 WDK DirectX 8。0
- DPIXELFORMAT
ms.date: 04/20/2017
ms.localizationpriority: medium
ms.openlocfilehash: 08520cd5664624e7dc6d102f7378ef6c912502a6
ms.sourcegitcommit: 4b7a6ac7c68e6ad6f27da5d1dc4deabd5d34b748
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2019
ms.locfileid: "72825504"
---
# <a name="the-texture-format-list"></a>纹理格式列表


## <span id="ddk_the_texture_format_list_gg"></span><span id="DDK_THE_TEXTURE_FORMAT_LIST_GG"></span>


Direct 8.0 引入了一种用于描述像素格式的新机制。 以前版本的 DirectDraw 和 Direct3D 像素格式由数据结构（**DDPIXELFORMAT** （Direct3D 象素格式只是 fourcc，最小有效字节为零）描述。

DDPIXELFORMAT 数据结构不再通过 API 级接口公开。 但是，它仍在 DDI 级别使用。 驱动程序通过纹理格式数组（其中包含其嵌入式 DDPIXELFORMAT 数据结构的图面说明）来报告其支持的纹理格式。 不过，现在可以使用嵌入的像素格式结构来报告新样式像素格式。 若要使用 DDPIXELFORMAT 数据结构指定新的样式像素格式，请将结构的**dwFlags**字段设置为值 DDPF\_D3DFORMAT，并将新的像素格式标识符存储在**dwFourCC**字段中。

此外，某些其他新字段已添加到 DDPIXELFORMAT （新字段已添加为具有现有字段的联合成员，因此数据结构的大小相同）。 这些字段包括： **dwOperations**、 **dwPrivateFormatBitCount**、 **wFlipMSTypes**和**wBltMSTypes**。

DirectX 8.0 DDI 兼容驱动程序应继续通过标准机制（即在全局驱动程序数据结构（[**D3DHAL\_GLOBALDRIVERDATA**](https://docs.microsoft.com/windows-hardware/drivers/ddi/d3dhal/ns-d3dhal-_d3dhal_globaldriverdata)）和 Z/模具中报告的纹理格式列表报告 DX7 样式图面格式为响应来自[**DdGetDriverInfo**](https://docs.microsoft.com/windows/desktop/api/ddrawint/nc-ddrawint-pdd_getdriverinfo)的 GUID\_ZPixelFormats 而报告的列表。 但是，驱动程序还应通过下面所述的新的 DirectX 8.0 DDI 机制来报告其所有受支持的表面格式。

DirectX 8.0 DDI 样式表面格式使用**GetDriverInfo2**报告。 运行时使用两个**GetDriverInfo2**查询类型从驱动程序查询表面格式。 D3DGDI2\_类型\_GETFORMATCOUNT 用于请求驱动程序支持的 DirectX 8.0 样式表面格式的数目。 D3DGDI2\_类型\_IFORMATPROVIDER.GETFORMAT 用于从驱动程序查询特定的表面格式。

若要处理 D3DGDI2\_类型\_GETFORMATCOUNT，驱动程序必须在[**DD\_GETFORMATCOUNTDATA**](https://docs.microsoft.com/windows-hardware/drivers/ddi/d3dhal/ns-d3dhal-_dd_getformatcountdata)的**dwFormatCount**字段中存储它支持的 DirectX 8.0 DDI 样式表面格式的数目。

当运行时从驱动程序接收到受支持的格式的数目时，它将同时查询每种表面格式，同时为 D3DGDI2\_类型\_IFORMATPROVIDER.GETFORMAT 的**GetDriverInfo2**查询。 [**Dd\_GETDRIVERINFODATA**](https://docs.microsoft.com/windows/desktop/api/ddrawint/ns-ddrawint-_dd_getdriverinfodata)数据结构的 " **lpvData** " 字段指向的数据结构为，在本例中为[**dd\_GETFORMATDATA**](https://docs.microsoft.com/windows-hardware/drivers/ddi/d3dhal/ns-d3dhal-_dd_getformatdata)。

DirectX 8.0 运行时扫描驱动程序报告的纹理格式列表，检查每个像素格式的**dwFlags**字段。 如果任何纹理格式的**dwFlags**设置为 DDPF\_D3DFORMAT，则运行时将此纹理格式列表标识为 DX8 样式，并筛选像素格式未标记为 DDPF\_D3DFORMAT 的所有纹理格式。 此外，DX7 运行时还会筛选具有 DDPF\_D3DFORMAT 集的任何纹理格式。 因此，支持 DX8 DDI 的驱动程序可以返回一个纹理格式列表，其中包含每个受支持格式的两个项，一种是在旧样式中指定，另一个在新样式中。 DX8 运行时使用在新样式中指定的格式，DX7 运行时使用旧样式中指定的格式。

所有受支持的表面格式（如纹理、深度或模具缓冲区或呈现目标）都应通过**GetDriverInfo2**机制进行报告。 运行时将忽略通过旧机制（D3DHAL\_GLOBALDRIVERDATA 和 GUID\_ZPixelFormats）返回的纹理和 Z/模具格式。 不会尝试将这些格式映射到 DirectX 8.0 驱动程序的 DX8 样式格式。 但是，旧版格式将映射到 DirectX 7.0 或更早版本的驱动程序的新样式。 因此，驱动程序必须通过 DirectX 8.0 DDI 报告所有支持的表面格式。 此外，由于旧的运行时不会将新样式图面格式映射到旧样式格式，因此驱动程序将继续使用旧机制来报告 DirectX 7.0 样式图面和 Z/模具格式，这一点非常重要。

 

 





