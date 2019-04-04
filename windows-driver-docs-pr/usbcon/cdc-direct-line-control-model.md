---
Description: CDC Direct Line Control Model
title: CDC 直接行控制模型
ms.localizationpriority: medium
ms.date: 01/07/2019
ms.openlocfilehash: 3c0e57ff803e6127135338358258f57714789886
ms.sourcegitcommit: a33b7978e22d5bb9f65ca7056f955319049a2e4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/31/2019
ms.locfileid: "56569115"
---
# <a name="cdc-direct-line-control-model"></a>CDC 直接行控制模型


USB CDC 直接行控制模型 (DLCM) 接口集合具有以下属性。

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>属性</th>
<th>描述</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>参考</p></td>
<td><p><em>通用串行总线类定义通信设备</em>，版本 1.1 中，部分 3.6.1。</p></td>
</tr>
<tr class="even">
<td><p>主接口的类</p></td>
<td><p>通信接口类 (0x02)。</p></td>
</tr>
<tr class="odd">
<td><p>主接口的子类</p></td>
<td><p>DLCM (0x01).</p></td>
</tr>
<tr class="even">
<td><p>协议</p></td>
<td><p>无 (0x00)。</p></td>
</tr>
<tr class="odd">
<td><p>枚举</p></td>
<td><p>是。</p></td>
</tr>
<tr class="even">
<td><p>相关的接口</p></td>
<td><p>音频类或供应商定义的接口的联合功能描述符 (UFD) 引用。</p></td>
</tr>
<tr class="odd">
<td><p>硬件 Id</p></td>
<td><pre space="preserve"><code class="language-syntax">USB\Vid_%04x&amp;Pid_%04x&amp;Rev_%04x&amp;Cdc_01&amp;MI_%02x
USB\Vid_%04x&amp;Pid_%04x&amp;Rev_%04x&amp;Cdc_01
USB\Vid_%04x&amp;Pid_%04x&amp;Cdc_01&amp;MI_%02x
USB\Vid_%04x&amp;Pid_%04x&amp;Cdc_01</code></pre></td>
</tr>
<tr class="even">
<td><p>兼容 Id</p></td>
<td><pre space="preserve"><code class="language-syntax">USB\Class_02&amp;SubClass_01&amp;Prot_00
USB\Class_02&amp;SubClass_01
USB\Class_02</code></pre></td>
</tr>
<tr class="odd">
<td><p>特殊处理</p></td>
<td><p>UFD 引用独立于 DLCM 接口集合枚举的音频类接口集合。</p></td>
</tr>
</tbody>
</table>

 

 

 



