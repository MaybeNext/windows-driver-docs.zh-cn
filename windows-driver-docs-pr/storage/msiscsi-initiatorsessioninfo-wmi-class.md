---
title: MSiSCSI\_InitiatorSessionInfo WMI 类
description: MSiSCSI\_InitiatorSessionInfo WMI 类
ms.assetid: 73053af8-80b0-4cab-8e27-c651be8f0e8c
ms.localizationpriority: medium
ms.date: 10/17/2018
ms.openlocfilehash: 490df49cdd7a4b91efc18ebc0e2a56d2ccfad2f9
ms.sourcegitcommit: a33b7978e22d5bb9f65ca7056f955319049a2e4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/31/2019
ms.locfileid: "56554351"
---
# <a name="msiscsiinitiatorsessioninfo-wmi-class"></a>MSiSCSI\_InitiatorSessionInfo WMI 类


## <span id="ddk_msiscsi_initiatorsessioninfo_wmi_class_kr"></span><span id="DDK_MSISCSI_INITIATORSESSIONINFO_WMI_CLASS_KR"></span>


MSiSCSI\_InitiatorSessionInfo WMI 类公开与会话和属于所指示的 HBA 发起程序的集合相关联的信息。

因为此类与存储微型端口驱动程序的特定实例相关联，微型端口驱动程序必须注册使用的微型端口驱动程序管理的特定的物理设备对象 (PDO) 名称的类。

MSiSCSI\_InitiatorSessionInfo 类中定义*Mgmt.mof*。

```cpp
class MSiSCSI_InitiatorSessionInfo {
  [read,key] String  InstanceName;
  [read] boolean  Active;
  [WmiDataId(1), DisplayName("Adapter Id") : amended, 
    DisplayInHex, description("Id that is globally unique to
    each instance of each adapter. Using the address of the 
    Adapter Extension is a good idea.") : amended]
    uint64  UniqueAdapterId;
  [WmiDataId(2), read, DisplayName("Count of Elements in 
    SessionsList array") : amended,
    cpp_quote(
    "\n    // Number of elements in SessionList array\n"),
    Description("Number of elements in SessionList array") : 
    amended] 
    uint32  SessionCount;
  [WmiDataId(3), read, DisplayName("List Of Sessions") :
    amended, Description("Variable length array of sessions.
    SessionCount specifies the number of elements in the 
    array") : amended, WmiSizeIs("SessionCount")]  
    ISCSI_SessionStaticInfo  SessionsList[];
};
```

当 WMI 工具套件编译前面的类定义时，它会生成[ **MSiSCSI\_InitiatorSessionInfo** ](https://msdn.microsoft.com/library/windows/hardware/ff563054)数据结构。

 

 




