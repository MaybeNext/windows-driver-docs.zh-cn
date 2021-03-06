---
title: Bug 检查 0x16E ERESOURCE_INVALID_RELEASE
description: ERESOURCE_INVALID_RELEASE bug 检查具有 0x0000016E 值。 这表明目标线程指针提供给 ExReleaseResourceForThreadLite 无效。
ms.assetid: F180D28D-70B7-4E78-9E04-C5DC19A41EB9
keywords:
- Bug 检查 0x16E ERESOURCE_INVALID_RELEASE
- ERESOURCE_INVALID_RELEASE
ms.date: 05/23/2017
topic_type:
- apiref
api_name:
- ERESOURCE_INVALID_RELEASE
api_type:
- NA
ms.localizationpriority: medium
ms.openlocfilehash: 5a38a325f2d312f3166f44558598569052f606f7
ms.sourcegitcommit: d03b44343cd32b3653d0471afcdd3d35cb800c0d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/02/2019
ms.locfileid: "67519929"
---
# <a name="bug-check-0x16e-eresourceinvalidrelease"></a>Bug 检查 0x16E：ERESOURCE\_无效\_版本


ERESOURCE\_无效\_发布 bug 检查的值为 0x0000016E。 这表明目标线程指针提供给 ExReleaseResourceForThreadLite 无效。

> [!IMPORTANT]
> 本主题面向程序员。 如果你已使用计算机时收到一个蓝色的屏幕，错误代码的客户，请参阅[疑难解答蓝屏错误](https://www.windows.com/stopcode)。


## <a name="eresourceinvalidrelease-parameters"></a>ERESOURCE\_无效\_发布参数


| 参数 | 描述                                    |
|-----------|------------------------------------------------|
| 1         | 正在释放资源                    |
| 2         | 当前线程                             |
| 3         | 传入的不正确的目标线程 |
| 4         | 保留                                       |

 

<a name="cause"></a>原因
-----

如果调用 ExSetOwnerPointerEx 跳过 API 客户端 （如果有意的跨线程版本） 或提供其他的值中意外传递调用方将命中此 bug 检查通过 ExGetCurrentResourceThread。

 

 




