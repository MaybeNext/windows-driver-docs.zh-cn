---
title: SRB\_获取\_流\_信息
description: SRB\_获取\_流\_信息
ms.assetid: ff5412ee-6e4f-43f4-a90d-4a2bdfa5d4ae
keywords:
- SRB_GET_STREAM_INFO 流媒体设备
topic_type:
- apiref
api_name:
- SRB_GET_STREAM_INFO
api_type:
- NA
ms.date: 11/28/2017
ms.localizationpriority: medium
ms.openlocfilehash: d1deced6611edcd29ba91870d1abe51082175889
ms.sourcegitcommit: 4b7a6ac7c68e6ad6f27da5d1dc4deabd5d34b748
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2019
ms.locfileid: "72843301"
---
# <a name="srb_get_stream_info"></a>SRB\_获取\_流\_信息


## <span id="ddk_srb_get_stream_info_ks"></span><span id="DDK_SRB_GET_STREAM_INFO_KS"></span>


类驱动程序发送此请求以获取设备及其支持的流的描述。

### <a name="span-idreturn_valuespanspan-idreturn_valuespanreturn-value"></a><span id="return_value"></span><span id="RETURN_VALUE"></span>返回值

微型驱动程序应将以下内容之一设置为 SRB 中的状态：

<span id="STATUS_SUCCESS"></span><span id="status_success"></span>成功\_状态  
指示命令成功完成。

<span id="STATUS_IO_DEVICE_ERROR"></span><span id="status_io_device_error"></span>IO\_设备状态\_\_错误  
指示出现硬件故障。

### <a name="comments"></a>备注

类驱动程序传递-*pSrb*中的缓冲区&gt;**StreamBuffer**指定的大小，以响应类驱动程序的[**SRB\_初始化\_设备**](srb-initialize-device.md)请求。 *PSrb*指针指向[**HW\_STREAM\_请求\_块**](https://docs.microsoft.com/windows-hardware/drivers/ddi/strmini/ns-strmini-_hw_stream_request_block)结构。 另请参阅[**端口\_配置\_信息**](https://docs.microsoft.com/windows-hardware/drivers/ddi/strmini/ns-strmini-_port_configuration_information)。

微型驱动程序使用[**HW\_STREAM\_描述符**](https://docs.microsoft.com/windows-hardware/drivers/ddi/strmini/ns-strmini-_hw_stream_descriptor)填充**StreamBuffer** ，其中描述了设备及其支持的流。 此缓冲区的大小由[**端口\_配置\_信息**](https://docs.microsoft.com/windows-hardware/drivers/ddi/strmini/ns-strmini-_port_configuration_information)结构中的 " **StreamDescriptorSize** " 字段中的微型驱动程序指示。

类驱动程序通常只颁发此请求一次。 微型驱动程序可以通过调用[StreamClassReenumerateStreams](https://docs.microsoft.com/windows-hardware/drivers/ddi/strmini/nf-strmini-streamclassreenumeratestreams)强制类驱动程序重新发出此请求，以更新其支持的流的说明。

**当微型驱动程序接收到 SRB\_获取\_STREAM\_信息命令时，微型驱动程序应：**

1.  检索流标头和流信息数据结构的指针。 例如：

    ```cpp
     PHW_STREAM_HEADER pstrhdr =
      (PHW_STREAM_HEADER)&(pSrb->CommandData.StreamBuffer->StreamHeader);
     PHW_STREAM_INFORMATION pstrinfo =
      (PHW_STREAM_INFORMATION)&(pSrb->CommandData.StreamBuffer->StreamInfo);
     
    ```

2.  验证缓冲区是否足够大以容纳返回的数据。

3.  将信息写入缓冲区。
