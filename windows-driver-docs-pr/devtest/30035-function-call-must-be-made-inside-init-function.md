---
title: C30035
description: 警告的 C30035 调用了，必须从进行初始化函数 （例如，DriverEntry() 或 DllInitialize()) 内部函数。 PREfast 无法确定是否从初始化函数进行调用。
ms.assetid: 1A5F97EA-7DDC-4D3A-8058-B9C0C2211DA9
ms.date: 04/20/2017
ms.localizationpriority: medium
f1_keywords:
- C30035
ms.openlocfilehash: af75a975cb322252cbd5ca8cc471cb0d5cb63f45
ms.sourcegitcommit: fb7d95c7a5d47860918cd3602efdd33b69dcf2da
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/25/2019
ms.locfileid: "67371472"
---
# <a name="c30035"></a>C30035


警告 C30035:必须从进行初始化函数内的函数调用了 (例如， **DriverEntry()** 或**DllInitialize()** )。 PREfast 无法确定是否从初始化函数进行调用。

已禁止\_内存优化\_分配\_也许\_错误\_调用\_站点

代码编译[池\_NX\_OPTIN](https://docs.microsoft.com/windows-hardware/drivers/kernel/single-binary-opt-in-pool-nx-optin)宏，但初始化内没有发生**DriverEntry()** 或**DllInitialize()** . 若要解决此问题，将初始化函数内部调用。

## <a name="span-idexamplespanspan-idexamplespanspan-idexamplespanexample"></a><span id="Example"></span><span id="example"></span><span id="EXAMPLE"></span>示例


下面的代码生成此警告。

在源文件中：

```
C_DEFINES=$(C_DEFINES) -DPOOL_NX_OPTIN=1
```

```
NTSTATUS
DriverEntry (
    _In_ PDRIVER_OBJECT DriverObject,
    _In_ PUNICODE_STRING RegistryPath
    )
{
    NTSTATUS status;

    MakeSafeInitialization ();
…
}

void MakeSafeInitialization()
{
    ExInitializeDriverRuntime(DrvRtPoolNxOptIn);
}
```

下面的代码可避免此警告：

```
NTSTATUS
DriverEntry (
    _In_ PDRIVER_OBJECT DriverObject,
    _In_ PUNICODE_STRING RegistryPath
    )
{
    NTSTATUS status;

    ExInitializeDriverRuntime(DrvRtPoolNxOptIn);
…
}
```

 

 





