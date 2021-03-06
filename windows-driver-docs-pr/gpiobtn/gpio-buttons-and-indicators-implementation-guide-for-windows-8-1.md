---
title: GPIO 按钮和指示器实现指南
description: Windows 8 通过 HID 微型端口类驱动程序引入了对常规 I/O (GPIO) 按钮和指示器的支持。
ms.assetid: E073E15A-7068-43D0-9DBA-7DD2E7FE2993
ms.localizationpriority: medium
ms.date: 10/17/2018
ms.openlocfilehash: cce7dd181f2a90555f273e104a7855c6f0ec57bd
ms.sourcegitcommit: fb7d95c7a5d47860918cd3602efdd33b69dcf2da
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/25/2019
ms.locfileid: "67385166"
---
# <a name="gpio-buttons-and-indicators-implementation-guide"></a>GPIO 按钮和指示器实现指南


Windows 8 通过 HID 微型端口类驱动程序引入了对常规 I/O (GPIO) 按钮和指示器的支持。 目标是以标准化方式提供对主要按钮（电源、Windows、音量和旋转锁）的支持，另外还介绍了已关联的相应 Windows 工程指南 (WEG)。 Windows 8.1 专注于增强端到端用户体验的质量以及统一各种创新性外形规格的行为。

## <a name="span-idinthissectionspanin-this-section"></a><span id="in_this_section"></span>本部分中的内容


<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">主题</th>
<th align="left">描述</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p><a href="state-indicators.md" data-raw-source="[State indicators](state-indicators.md)">状态指示器</a></p></td>
<td align="left"><p>本部分介绍的模式和停靠的指示器的状态。</p></td>
</tr>
<tr class="even">
<td align="left"><p><a href="physical-buttons.md" data-raw-source="[Physical buttons](physical-buttons.md)">物理按钮</a></p></td>
<td align="left"><p>硬件按钮允许用户执行许多常见任务不具有一个方便的用户界面的替代方法。 本部分解决的情况下，硬件按钮通常用于物理键盘不是可供用户使用，如双用型或平板电脑外形规格上时出现的任务。</p></td>
</tr>
<tr class="odd">
<td align="left"><p><a href="interface-implementation-guidance.md" data-raw-source="[Interface implementation guidance](interface-implementation-guidance.md)">接口实现指南</a></p></td>
<td align="left"><p>本部分提供了接口实现的指南。</p></td>
</tr>
<tr class="even">
<td align="left"><p><a href="code-samples.md" data-raw-source="[Code samples](code-samples.md)">代码示例</a></p></td>
<td align="left"><p>本部分包含代码示例和示例接口实现描述符。</p></td>
</tr>
<tr class="odd">
<td align="left"><p><a href="implement-the-unattended-windows-setup-setting.md" data-raw-source="[Implement the unattended Windows Setup setting](implement-the-unattended-windows-setup-setting.md)">实现的无人参与的 Windows 安装程序设置</a></p></td>
<td align="left"><p>本主题介绍如何设置无人参与的 Windows 安装程序组件设置。</p></td>
</tr>
<tr class="even">
<td align="left"><p><a href="logging-and-investigations.md" data-raw-source="[Logging and investigations](logging-and-investigations.md)">日志记录和调查</a></p></td>
<td align="left"><p>本主题介绍日志记录和调查的 GPIO 实现。</p></td>
</tr>
<tr class="odd">
<td align="left"><p><a href="running-test-passes.md" data-raw-source="[Running test passes](running-test-passes.md)">正在运行的测试通过</a></p></td>
<td align="left"><p>MITT 平台可以提供测试自动化和选择自定义发送目标调查的 GPIO 模式测试 GPIO 按钮。</p></td>
</tr>
</tbody>
</table>

 

Windows 8.1 投资的一部分**msgpio**按钮驱动程序带来了重要的增强功能：

-   若要加速调查的增强日志记录。
-   改进了同步和错误处理来增强可靠性。
-   新 ConvertibleSlateMode[无人参与 Windows 安装程序](https://go.microsoft.com/fwlink/p/?linkid=276788)用于非 GPIO 便携式计算机上将以静态方式将模式设置为便携式计算机的 OEM 映像自定义的一部分。

GPIO 按钮和指示器实现有关的问题，将一封电子邮件发送到的 Microsoft 支持小组dockingsupport@microsoft.com。

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>相关主题
[电源按钮行为和实现](https://aka.ms/connect-redirect?DownloadID=47452)  
[连接的备用唤醒源](https://aka.ms/connect-redirect?DownloadID=49891)  
[ACPI 设计指南](https://aka.ms/connect-redirect?DownloadID=48755)  
[GetSystemMetrics 函数](https://go.microsoft.com/fwlink/p/?linkid=324686)  
[Windows 8 中的键盘增强功能](https://go.microsoft.com/fwlink/p/?linkid=324536)  
[Windows 硬件兼容性计划](https://docs.microsoft.com/windows-hardware/design/compatibility/index)  
[Windows 桌面应用认证要求](https://go.microsoft.com/fwlink/p/?linkid=306131)  
[I²C 上的 HID](https://go.microsoft.com/fwlink/p/?linkid=324690)  
[在 MITT GPIO 测试](https://docs.microsoft.com/windows-hardware/drivers/spb/gpio-tests-in-mitt)  
[Windows 系统映像管理器技术参考](https://go.microsoft.com/fwlink/p/?linkid=324691)  
[无人参与 Windows 安装程序参考](https://go.microsoft.com/fwlink/p/?linkid=276788)  
[Windows Driver Kit (WDK) 8.1](https://go.microsoft.com/fwlink/p/?linkid=310164)  



