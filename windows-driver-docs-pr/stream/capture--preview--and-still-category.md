---
title: 捕获，预览版中，并且仍然类别
description: 捕获，预览版中，并且仍然类别
ms.assetid: b82cc3b6-1cea-4864-9501-95919f05455f
keywords:
- 流类别 WDK 视频捕获，捕获视频流
- 流类别 WDK 视频捕获，预览视频流
- 流类别 WDK 视频捕获，捕获静止图像
- 捕获 WDK 视频捕获的视频流类别
- 预览视频流类别 WDK 视频捕获
- 捕获静止图像类别 WDK 视频捕获
- PINNAME_VIDEO_CAPTURE
- NAME_VIDEO_PREVIEW
- PINNAME_VIDEO_STILL
ms.date: 04/20/2017
ms.localizationpriority: medium
ms.openlocfilehash: ca096532db207df77cfa9f430bab9ca81bb14def
ms.sourcegitcommit: a33b7978e22d5bb9f65ca7056f955319049a2e4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/31/2019
ms.locfileid: "56522785"
---
# <a name="capture-preview-and-still-category"></a>捕获，预览版中，并且仍然类别


以下 Guid 对应于用于捕获视频流、 预览视频流，并仍捕获映像 （如果支持的硬件） 类别：

-   **PINNAME\_视频\_捕获**

    输出插针，捕获类别提供压缩或未压缩数字视频的流。 此流类别用于写入到磁盘，到视频会议，以及进行图像分析的电影。

-   **PINNAME\_视频\_预览**

    输出插针，预览类别提供未压缩的数字视频的流。 此流类别用于在本地监视，可由 DirectDraw 直接显示的 RGB 或 YUV 格式查看视频流。 在资源受限的情况下，捕获微型驱动程序应确定优先级低于捕获流 pin 预览流 pin。

-   **PINNAME\_视频\_仍**

    仍将类别输出插针用于双模式照相机能够捕获流和静止的图像流 （这通常是比捕获流的质量更高） 生成。 静止图像流包括从外部或以编程方式触发采集的图像的功能。

捕获、 预览和仍的流 pin 类别是几乎相同的数据格式和流特征。

**请注意**  :因为许多照相机生成单个输出流，Microsoft DirectShow 包括智能 Tee 筛选器将单个流拆分为捕获和预览流。 因此，用于生成一个流的相机的微型驱动程序应在内部重复数据流中，以生成预览流。

 

指定时**PINNAME\_视频\_捕获**，或**PINNAME\_视频\_预览**，或**PINNAME\_视频\_仍**插针，使用下表中列出的信息。

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>属性</th>
<th>值</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>DataRange 结构</strong></p></td>
<td><p><a href="https://msdn.microsoft.com/library/windows/hardware/ff567628" data-raw-source="[&lt;strong&gt;KS_DATARANGE_VIDEO&lt;/strong&gt;](https://msdn.microsoft.com/library/windows/hardware/ff567628)"><strong>KS_DATARANGE_VIDEO</strong> </a> （仅帧）</p>
<p><a href="https://msdn.microsoft.com/library/windows/hardware/ff567629" data-raw-source="[&lt;strong&gt;KS_DATARANGE_VIDEO2&lt;/strong&gt;](https://msdn.microsoft.com/library/windows/hardware/ff567629)"><strong>KS_DATARANGE_VIDEO2</strong> </a> （字段或帧，bob，或将设置）</p>
<p><a href="https://msdn.microsoft.com/library/windows/hardware/ff567353" data-raw-source="[&lt;strong&gt;KS_DATARANGE_MPEG1_VIDEO&lt;/strong&gt;](https://msdn.microsoft.com/library/windows/hardware/ff567353)"><strong>KS_DATARANGE_MPEG1_VIDEO</strong></a></p>
<p><a href="https://msdn.microsoft.com/library/windows/hardware/ff567362" data-raw-source="[&lt;strong&gt;KS_DATARANGE_MPEG2_VIDEO&lt;/strong&gt;](https://msdn.microsoft.com/library/windows/hardware/ff567362)"><strong>KS_DATARANGE_MPEG2_VIDEO</strong></a></p></td>
</tr>
<tr class="even">
<td><p><strong>DataFormat 结构</strong></p></td>
<td><p>KS_DATAFORMAT_VIDEO （仅帧）</p>
<p>KS_DATAFORMAT_VIDEO2 （字段或帧，bob，或将设置）</p>
<p><a href="https://msdn.microsoft.com/library/windows/hardware/ff567658" data-raw-source="[&lt;strong&gt;KS_MPEG1VIDEOINFO&lt;/strong&gt;](https://msdn.microsoft.com/library/windows/hardware/ff567658)"><strong>KS_MPEG1VIDEOINFO</strong> </a> （适用于 MPEG1)</p>
<p><a href="https://msdn.microsoft.com/library/windows/hardware/ff567667" data-raw-source="[&lt;strong&gt;KS_MPEGVIDEOINFO2&lt;/strong&gt;](https://msdn.microsoft.com/library/windows/hardware/ff567667)"><strong>KS_MPEGVIDEOINFO2</strong> </a> （适用于 MPEG2)</p></td>
</tr>
<tr class="odd">
<td><p><strong>主要格式 GUID</strong></p></td>
<td><p>KSDATAFORMAT_TYPE_VIDEO</p></td>
</tr>
<tr class="even">
<td><p><strong>子设置的 GUID 格式</strong></p></td>
<td><p>RGB16、 RGB24、 UYVY、 JPEG</p></td>
</tr>
<tr class="odd">
<td><p><strong>说明符 GUID</strong></p></td>
<td><p>KSDATAFORMAT_SPECIFIER_VIDEOINFO （仅帧）</p>
<p>KSDATAFORMAT_SPECIFIER_VIDEOINFO2 （字段或帧）</p></td>
</tr>
<tr class="even">
<td><p><strong>扩展标头大小</strong></p></td>
<td><p><a href="https://msdn.microsoft.com/library/windows/hardware/ff567645" data-raw-source="[&lt;strong&gt;KS_FRAME_INFO&lt;/strong&gt;](https://msdn.microsoft.com/library/windows/hardware/ff567645)"><strong>KS_FRAME_INFO</strong> </a>如果不以 MPEG 格式。 如果 MPEG 格式，则为零。</p></td>
</tr>
<tr class="odd">
<td><p><strong>所需的属性集</strong></p></td>
<td><p><a href="https://msdn.microsoft.com/library/windows/hardware/ff566568" data-raw-source="[KSPROPSETID_Connection](https://msdn.microsoft.com/library/windows/hardware/ff566568)">KSPROPSETID_Connection</a></p>
<p><a href="https://msdn.microsoft.com/library/windows/hardware/ff567806" data-raw-source="[PROPSETID_VIDCAP_DROPPEDFRAMES](https://msdn.microsoft.com/library/windows/hardware/ff567806)">PROPSETID_VIDCAP_DROPPEDFRAMES</a></p></td>
</tr>
<tr class="even">
<td><p><strong>所需的事件集</strong></p></td>
<td><p>无</p></td>
</tr>
<tr class="odd">
<td><p><strong>DirectShow majortype</strong></p></td>
<td><p>MEDIATYPE_Video</p></td>
</tr>
<tr class="even">
<td><p><strong>DirectShow formattype</strong></p></td>
<td><p>FORMAT_VideoInfo （仅帧）</p>
<p>FORMAT_VideoInfo2 （字段或帧）</p></td>
</tr>
</tbody>
</table>

 

 

 



