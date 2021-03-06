---
title: DirectSound 流数据范围
description: DirectSound 流数据范围
ms.assetid: cc31eb2d-7421-4748-b14c-f4d3d15f9884
keywords:
- DirectSound WDK 音频，流数据范围
ms.date: 04/20/2017
ms.localizationpriority: medium
ms.openlocfilehash: e00d726afbe86cce035adcbd9ed946a1c444d955
ms.sourcegitcommit: 4b7a6ac7c68e6ad6f27da5d1dc4deabd5d34b748
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2019
ms.locfileid: "72833473"
---
# <a name="directsound-stream-data-range"></a>DirectSound 流数据范围


## <span id="directsound_stream_data_range"></span><span id="DIRECTSOUND_STREAM_DATA_RANGE"></span>


此示例使用[**KSDATARANGE\_音频**](https://docs.microsoft.com/windows-hardware/drivers/ddi/ksmedia/ns-ksmedia-ksdatarange_audio)结构来描述 DirectSound 流的数据范围。

```cpp
  DataRange.FormatSize  = sizeof(KSDATARANGE_AUDIO);
  DataRange.Flags       = 0;
  DataRange.SampleSize  = 0;
  DataRange.Reserved    = 0;
  DataRange.MajorFormat = STATICGUIDOF(KSDATAFORMAT_TYPE_AUDIO);
  DataRange.SubFormat   = STATICGUIDOF(KSDATAFORMAT_SUBTYPE_PCM);
  DataRange.Specifier   = STATICGUIDOF(KSDATAFORMAT_SPECIFIER_DSOUND);
  MaximumChannels        = 4;   // max number of channels, or -1 for unlimited
  MinimumBitsPerSample   = 2;
  MaximumBitsPerSample   = 16;  // 16, 24, 32, etc.
  MinimumSampleFrequency = 5000;
  MaximumSampleFrequency = 48000;
```

此示例中的成员值与[PCM 多通道流数据范围](pcm-multichannel-stream-data-range.md)示例的成员值相似，但**MaximumBitsPerSample**值除外。 此值设置为示例容器大小，应为8的倍数。 例如，如果设备支持24位容器中的20位有效音频数据，则应将**MaximumBitsPerSample**的值设置为24。

 

 




