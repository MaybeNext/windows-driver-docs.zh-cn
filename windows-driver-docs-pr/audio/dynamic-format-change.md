---
title: 动态格式更改
description: 动态格式更改
ms.assetid: 41e6ec8c-3a96-4103-a991-3b9ba6acad6c
ms.date: 04/20/2017
ms.localizationpriority: medium
ms.openlocfilehash: f9823ff3b834baf340a14bdc00af82332eb3cb2f
ms.sourcegitcommit: a33b7978e22d5bb9f65ca7056f955319049a2e4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/31/2019
ms.locfileid: "56548251"
---
# <a name="dynamic-format-change"></a>动态格式更改


动态格式更改是 Windows 7 和更高版本的 Windows 操作系统允许音频应用程序和音频适配器之间的流音频数据用于动态更改的格式中的功能。 动态格式更改可容纳的高清晰度多媒体接口 (HDMI) 设备中的音频流的行为。 本主题概述了动态格式更改，并介绍其工作原理。

以下列表显示在其中使用动态格式更改的方案。

-   **HDMI 设备提供新功能。** 当用于音频和视频传输的总 HDMI 带宽 HDMI 设备流音频或视频数据或这两者，固定的视频信号中的容量分配优先。 这意味着，如果有 HDMI 显示设备连接到计算机并更改显示分辨率，这会影响保留的音频数据传输到计算机的带宽的大小。

    例如，假设最初使用的数据格式设置为 192 KHz，与特定显示模式的 16 位立体声配置 HDMI 设备。 当更改为不同的显示模式时，流式处理音频数据的剩余带宽可能无法满足 192 KHz 格式。 使设备驱动程序通知有关在显示模式下，更改连接的计算机的音频服务，这将导致音频驱动程序和重新协商的音频数据格式音频服务。 如果当前所选的 192 KHz 格式不能进行流式处理中剩余的带宽，则选择一种新格式。 有关格式协商过程的详细信息，请参阅[格式协商](format-negotiation.md)。

    在另一个 HDMI 相关动态格式更改方案中，将音频设备被拔出并在插入新的、 支持 HDMI 的设备。 HDMI 设备的设备驱动程序生成的格式更改事件，音频服务重新进行协商的音频数据格式与设备驱动程序。

-   **一些独立的音频设备提供硬件控件，用户可以用来更改音频数据格式。** 在此方案中，用户操作的控制旋钮上环绕的声音放大器，例如，要选择的音频数据格式。 如果没有连接到独立的音频设备的计算机，这种新选择的数据格式会重新协商的数据格式，并可能是，更改它连接的计算机上导致音频驱动程序。

-   **在控制面板中的声音小程序的第三方 UI 提供了用于启用或禁用系统效果的选项。** 当开发你自己系统效果音频处理对象 (sAPOs) 时，您还可以提供自定义 UI**声音**控制面板中的小程序。 此自定义 UI 可以包括对修改**增强**或**高级**选项卡**声音**和 / 或小程序。 在此方案中，用户选择中的复选框**增强**选项卡来启用或禁用全局系统效果 (GFX) 功能，它要求要更改的音频数据格式。 由用户所做的选择会导致 HDMI 驱动程序生成的格式更改事件。 音频服务接收有关此事件通知，并选择新的音频数据格式的音频驱动程序重新进行协商。

若要提供 HDMI 和 IEC61937 符合压缩音频格式，如杜比数字和数字影院声音 (DTS) 的支持，Windows 7 和更高版本的 Windows 操作系统提供一组新的子类型的内核流式处理 (KS) 属性使用的 Guid 和结构。 国际电工委员会 (IEC) 标准，IEC 61937，适用于传输的非线性的数字音频接口[PCM](pcm-stream-data-format.md)编码位流。 有关子类型的 Guid 的详细信息，请参阅 KSDATAFORMAT\_子类型\_IEC61937\_中 Ksmedia.h Xxx Guid。

**请注意**  时音频的终结点生成器收到动态格式更改通知，并且建议的数据格式不受设备驱动程序，终结点生成器将然后重新计算新的默认设备数据格式。

并在经过重新设计的音频驱动程序现在支持新格式的情况下，它可以强制终结点生成器可为设备的默认格式选择新的格式。 若要为设备的默认值为新的格式强制转变，音频驱动程序时不能收到有关旧格式的格式支持查询。 失败的格式支持查询触发格式更改通知，并为终结点生成器然后计算设备的新默认格式。

 

 

 



