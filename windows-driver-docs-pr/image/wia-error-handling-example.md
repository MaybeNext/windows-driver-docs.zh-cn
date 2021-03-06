---
title: WIA 错误处理示例
description: WIA 错误处理示例
ms.assetid: 7dc4b15e-40db-4e64-be41-d6bcc44603c6
ms.date: 04/20/2017
ms.localizationpriority: medium
ms.openlocfilehash: e4e145ab226945a8f79182cc95f26350e709ca75
ms.sourcegitcommit: 0cc5051945559a242d941a6f2799d161d8eba2a7
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "63379583"
---
# <a name="wia-error-handling-example"></a>WIA 错误处理示例


有关将设备状态消息发送的驱动程序的示例，请参阅中的扩展 WIA 这头怪兽驱动程序示例[WIA 驱动程序示例](https://go.microsoft.com/fwlink/p/?linkid=256210)。 此示例说明了如何实现一个简单的错误处理程序。

### <a name="example-error-handling-extension"></a>例如：错误处理扩展插件

以下代码片段演示如何实现简单的错误处理扩展插件。 此错误处理扩展插件仅处理 WIA\_错误\_涵盖\_打开设备状态错误，并显示模式对话框。 请注意，某些代码省略了为简化此示例。

```cpp
STDMETHODIMP

CErrHandler::ReportStatus(

IN LONG lFlags,

IN HWND hwndParent,

IN IWiaItem2 *pWiaItem2,

IN HRESULT hrStatus,

IN LONG lPercentComplete)

{

    HRESULT hr = WIA_STATUS_NOT_HANDLED;

    if (WIA_ERROR_COVER_OPEN == hrStatus)

    {

        int i;

        i = MessageBox(hwndParent,

        ERROR_COVER_OPEN_STR,

        TEXT("Driver UI Extension"),

        MB_RETRYCANCEL|MB_TASKMODAL|MB_ICONERROR);

        if (IDOK == i)

        {

            hr = S_OK;

        }

        else

        {

            hr = WIA_ERROR_COVER_OPEN;

        }

    }

    return hr;

}

STDMETHODIMP

CErrHandler::GetStatusDescription(

IN LONG lFlags,

IN IWiaItem2 *pWiaItem2,

IN HRESULT hrStatus,

OUT BSTR *pbstrDescription)

{

    HRESULT hr = pbstrDescription ? WIA_STATUS_NOT_HANDLED :

    E_INVALIDARG;

    if (WIA_ERROR_COVER_OPEN == hrStatus)

    {

        BSTR bstrDescription = NULL;

        bstrDescription = SysAllocString(ERROR_COVER_OPEN_STR);

        if (bstrDescription)

        {

            *pbstrDescription = bstrDescription;

            hr = S_OK;

        }

        else

        {

            hr = E_OUTOFMEMORY;

        }

    }

    return hr;

}
```

 

 




