---
title: DSM\_负载\_平衡\_策略\_V2 WMI 类
description: DSM\_负载\_平衡\_策略\_V2 WMI 类
ms.assetid: 8895d0ca-b9bd-4f8d-bf8f-4ba2f459c264
ms.localizationpriority: medium
ms.date: 10/17/2018
ms.openlocfilehash: d010206ab8be17f4dd1f33ade327aa83fb99f188
ms.sourcegitcommit: b3859d56cb393e698c698d3fb13519ff1522c7f3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/05/2019
ms.locfileid: "57349396"
---
# <a name="dsmloadbalancepolicyv2-wmi-class"></a>DSM\_负载\_平衡\_策略\_V2 WMI 类


MPIO 发布 DSM\_负载\_平衡\_策略\_V2 WMI 类但需要进行注册，GUID 和处理其实现的 DSM。 MPIO 驱动程序使用 DSM\_加载\_平衡\_策略\_V2 WMI 类，以标识应用于 MPIO 磁盘的负载平衡策略。

```cpp
class DSM_Load_Balance_Policy_V2
{

    //
    // Version information for further changes.
    //
    [WmiDataId(1),
     read,
     Description("Version Number") : amended
    ]
    uint32 Version;

    //
    // Load Balance type.
    //
    [WmiDataId(2),
     Description("Load Balance Policy implemented by the DSM") : amended,
     Values{"Fail Over Only",
            "Round Robin",
            "Round Robin with Subset",
            "Dynamic Least Queue Depth",
            "Weighted Paths",
            "Least Blocks",
            "Vendor Specific"} : amended,

     DefineValues{"DSM_LB_FAILOVER",
                  "DSM_LB_ROUND_ROBIN",
                  "DSM_LB_ROUND_ROBIN_WITH_SUBSET",
                  "DSM_LB_DYN_LEAST_QUEUE_DEPTH",
                  "DSM_LB_WEIGHTED_PATHS",
                  "DSM_LB_LEAST_BLOCKS",
                  "DSM_LB_VENDOR_SPECIFIC"},
     ValueMap{"1", "2", "3", "4", "5", "6", "7"}
    ]
    uint32 LoadBalancePolicy;

    //
    // If load balance policy is DSM_LB_VENDOR_SPECIFIC then the following
    // properties are not used. The caller would need to provide data for
    // setting the vendor specific Load Balance policy.
    //

    //
    // Number of paths.
    //
    [WmiDataId(3),
     Description("Number of entries in DSM_Paths array") : amended
    ]
    uint32 DSMPathCount;

    [WmiDataId(4),
     Description("Reserved field") : amended
    ]
    uint32 Reserved;

    //
    // Paths' array.
    //
    [WmiDataId(5),
     WmiSizeIs("DSMPathCount"),
     Description("DSM_Paths array") : amended
    ]
    MPIO_DSM_Path_V2 DSM_Paths[];
};
```

此类定义编译时通过 WMI 工具套件，它会生成[ **DSM\_负载\_平衡\_策略\_V2** ](https://msdn.microsoft.com/library/windows/hardware/ff552698)数据结构。 没有与此 WMI 类相关联的方法。

 

 




