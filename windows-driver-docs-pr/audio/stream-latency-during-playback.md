---
title: 播放期间的流延迟
description: 播放期间的流延迟
ms.assetid: 70b41245-f463-4225-b79c-0ee65d8a0132
ms.date: 04/20/2017
ms.localizationpriority: medium
ms.openlocfilehash: d121edf1edf9f6820b00361c129ddf67945dc755
ms.sourcegitcommit: fb7d95c7a5d47860918cd3602efdd33b69dcf2da
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/25/2019
ms.locfileid: "67354258"
---
# <a name="stream-latency-during-playback"></a>播放期间的流延迟


运行状态的音频播放流时，很小 WaveRT 端口驱动程序的角色。 下图中所示，在播放期间 WaveRT 端口驱动程序的客户端将其数据写入循环缓冲区，音频设备然后从缓冲区中读取此数据。 此活动无需干预从端口驱动程序。 换而言之，音频数据用户模式应用程序与音频硬件之间直接流动而无需涉及到的任何内核模式软件组件。

在图中，写入和运行位置不断进度从左到右为音频流数据流通过循环缓冲区。 缓冲区被描述为循环，因为当播放位置或写入位置到达它自动回绕到的缓冲区开始的缓冲区的末尾。

在播放期间则 Stream 延迟有两个主要源，指定在下图中为 A 和 b。

![说明播放流的延迟的关系图](images/wavert-playback.png)

在上图中，*写入位置*是刚超出最后一个样本的客户端已写入到缓冲区的位置。 *播放位置*是当前通过扬声器播放的音频设备的示例。

从客户端将音频示例写入到缓冲区之前的音频设备中播放的时间的延迟是只需写入和运行位置之间的分离。 这种分离是以下两个源的延迟时间的总和 (标记为 A 和 B 在关系图中):

**延迟的**:音频设备从缓冲区中读取数据后，数据将驻留在"先进先出"硬件 (FIFO) 缓冲区之前的音频设备时钟通过数字模拟转换器 (DAC) 的数据。

**延迟 B**:客户端将数据写入到循环缓冲区后，数据驻留在缓冲区中直到音频设备读取的数据。

客户端具有无法控制的完全取决于硬件的延迟。 典型的先进先出可能存储足够示例源为大约 64 计时周期的示例时钟 DAC。 但是，客户端执行控制延迟 b.延迟 B 太大，引入不必要的延迟到系统。但是，使其耗尽音频设备太小风险。

尽管客户端可以设置一个计时器定期激活其缓冲区写入的线程，但此方法不会获得的最小的延迟。 若要进一步降低延迟，客户端可以配置设备生成硬件通知每次设备完成从缓冲区读取新数据块的播放。 在这种情况下，通过硬件通知而不是由计时器激活客户端线程。

通过让通知客户端每次完成从缓冲区读取的数据块的音频设备，客户端可以缩小延迟比其他实用。

客户端可以获取通过发送参与流延迟的延迟问题的摘要[ **KSPROPERTY\_RTAUDIO\_HWLATENCY** ](https://docs.microsoft.com/windows-hardware/drivers/audio/ksproperty-rtaudio-hwlatency) WaveRT 端口驱动程序的请求。

客户端确定的分离以保持在之间写入和播放位置后，客户端监视中播放位置来确定如何最前移的写入位置的更改。 在 Windows Server 2008 和更高版本操作系统中，客户端发出[ **KSPROPERTY\_RTAUDIO\_POSITIONREGISTER** ](https://docs.microsoft.com/windows-hardware/drivers/audio/ksproperty-rtaudio-positionregister)属性请求以确定播放位置。 支持此功能提供的 PortCls 系统驱动程序中的改进。

如果音频设备已注册，在上图中所示的位置，属性请求将映射到用户模式下客户端可以访问的虚拟内存地址注册。 映射位置注册后，客户端可以读取内容的内存地址来确定当前播放位置。

 

 




