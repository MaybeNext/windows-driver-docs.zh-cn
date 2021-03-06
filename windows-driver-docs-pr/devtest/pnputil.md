---
title: PnPUtil
description: PnPUtil
ms.assetid: 3678fd41-c3ee-4538-b783-6f099ac104a6
ms.date: 04/20/2017
ms.localizationpriority: medium
ms.openlocfilehash: 183f37ceb8bc6c1e6ec8a0a1ab119e803dc96fec
ms.sourcegitcommit: fb7d95c7a5d47860918cd3602efdd33b69dcf2da
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/25/2019
ms.locfileid: "67363841"
---
# <a name="pnputil"></a>PnPUtil


PnPUtil (PnPUtil.exe) 是一个命令行工具，使管理员可以执行以下操作[驱动程序包](https://docs.microsoft.com/windows-hardware/drivers/install/driver-packages):

-   将添加到驱动程序包[驱动程序存储区](https://docs.microsoft.com/windows-hardware/drivers/install/driver-store)。

-   在计算机上安装驱动程序包。

-   从驱动程序存储区中删除驱动程序包。

-   枚举驱动程序存储区中当前存在的驱动程序包。 列出不是现成的包的唯一驱动程序包。 *现成*驱动程序包是一个包含在 Windows 或其服务包的默认安装中。

<table>
<colgroup>
<col width="100%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">在何处可以下载 PnPUtil？</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p>PnPUtil (PnPUtil.exe) 包含在每个版本的 Windows，从 Windows Vista 开始 （在 %windir%\system32 目录中）。 没有单独的 PnPUtil 下载包。</p>
<ul>
<li>打开<strong>命令提示符</strong>窗口 (<strong>以管理员身份运行</strong>)。</li>
<li>类型<strong>pnputil /？</strong> 若要查看命令选项。 请参阅<a href="pnputil-command-syntax.md" data-raw-source="[&lt;strong&gt;PnPUtil Command Syntax&lt;/strong&gt;](pnputil-command-syntax.md)"> <strong>PnPUtil 命令语法</strong></a>有关详细信息。</li>
</ul>
<div class="alert">
<strong>请注意</strong>PnPUtil 支持在 Windows Vista 和更高版本的 Windows 上。 PnPUtil 不是适用于 Windows XP，但是，可以使用<a href="https://docs.microsoft.com/windows-hardware/drivers/install/difx-guidelines" data-raw-source="[Driver Install Frameworks (DIFx)](https://docs.microsoft.com/windows-hardware/drivers/install/difx-guidelines)">驱动程序安装框架 (DIFx)</a>工具创建和自定义安装的驱动程序包。
</div>
<div>
 
</div></td>
</tr>
</tbody>
</table>

 

本部分包含下列内容：

[PnPUtil 命令语法](pnputil-command-syntax.md)

[PnPUtil 示例](pnputil-examples.md)

 

 





