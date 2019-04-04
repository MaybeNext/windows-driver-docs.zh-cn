---
title: GFlags 详细信息
description: GFlags 详细信息
ms.assetid: 97faa63d-b876-4973-812f-f3bdd57c1778
keywords:
- GFlags、 详细信息
ms.date: 05/23/2017
ms.localizationpriority: medium
ms.openlocfilehash: 62855e3081ff115ab8abd0fdcc9b83362a62b8e5
ms.sourcegitcommit: d334150abe0b189faf33049908af7aab1458c13d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/06/2019
ms.locfileid: "57463987"
---
# <a name="gflags-details"></a>GFlags 详细信息


## <span id="ddk_gflags_details_dtools"></span><span id="DDK_GFLAGS_DETAILS_DTOOLS"></span>


GFlags 启用和禁用通过编辑 Windows 注册表和内部设置的系统功能。 本部分介绍 GFlags 的详细信息中的操作，并包括最有效地使用 GFlags 的技巧。

### <a name="span-idgeneralinformationspanspan-idgeneralinformationspangeneral-information"></a><span id="general_information"></span><span id="GENERAL_INFORMATION"></span>常规信息

-   若要显示 GFlags 对话框中，在命令行处，键入**gflags** （不带任何参数）。

-   在 Windows Server 2003 和早期版本的 Windows 上，若要设置标志，在注册表中或在内核模式下，必须在计算机上 Administrators 组的成员。 但是，在具有用户访问最低来宾帐户访问权限可以启动 GFlags 对话框中的程序。

-   GFlags 系统级注册表设置在注册表中会立即显示，但直到重新启动系统不会生效。

-   GFlags 图像文件注册表设置在注册表中会立即显示，但直到重新启动该进程不会生效。

-   GFlags 对话框中的调试器和启动功能是特定的程序。 您可以仅设置其上一个图像文件一次。

### <a name="span-idflagdetailsspanspan-idflagdetailsspanflag-details"></a><span id="flag_details"></span><span id="FLAG_DETAILS"></span>标志的详细信息

-   若要清除所有标志，请将标志设置为-FFFFFFFF。 将标志设置为 0 将 0 添加到当前的标志值。

-   Windows 将图像文件的标志设置为 FFFFFFFF (0xFFFFFFFF)，清除所有标志的图像文件，并删除**GlobalFlag**图像文件注册表项中的条目。 保留图像文件注册表项。

### <a name="span-iddialogboxandcommandlinespanspan-iddialogboxandcommandlinespandialog-box-and-command-line"></a><span id="dialog_box_and_command_line"></span><span id="DIALOG_BOX_AND_COMMAND_LINE"></span>对话框和命令行

可以通过使用其方便的对话框或命令行运行 GFlags。 大多数功能均可在两种形式，但存在以下例外。

**仅限对话框**

-   启动。 开始使用指定的标志的程序。

-   在调试器中运行程序。

-   [特殊池](special-pool.md)Windows Vista 之前的系统上。 在 Windows Vista 和更高版本的 Windows 上，可以在命令行或 Gflags 对话框中配置特殊池功能。

**只有命令行**

-   设置的用户模式堆栈跟踪数据库大小 (/ tracedb)。

-   设置页面堆验证选项。

### <a name="span-idregistryinformationspanspan-idregistryinformationspanregistry-information"></a><span id="registry_information"></span><span id="REGISTRY_INFORMATION"></span>注册表信息

会话之间保存的 GFlags 设置存储在注册表中。 可以使用注册表 Api、 Regedit 中或 reg.exe 来查询或更改这些值。 下表列出了设置和注册表中存储的类型。

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td align="left"><p>系统级设置 （"注册表"）</p></td>
<td align="left"><p>HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\Session Manager&lt;strong&gt;GlobalFlag</strong></p></td>
</tr>
<tr class="even">
<td align="left"><p>计算机的所有用户的特定于程序的设置 ("Image file")。</p></td>
<td align="left"><p>HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Image File Execution Options&lt;全身&gt;映像文件名</em>&lt;强&gt;GlobalFlag</strong></p></td>
</tr>
<tr class="odd">
<td align="left"><p>计算机的所有用户的特定程序 （"无提示进程退出"） 的无提示退出设置。</p></td>
<td align="left"><p>HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\SilentProcessExit&lt;em&gt;ImageFileName</em></p></td>
</tr>
<tr class="even">
<td align="left"><p>计算机的所有用户的图像文件的页面堆选项</p></td>
<td align="left"><p>HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Image File Execution Options&lt;全身&gt;映像文件名</em>&lt;强&gt;PageHeapFlags</strong></p></td>
</tr>
<tr class="odd">
<td align="left"><p>用户模式堆栈跟踪数据库大小 (<strong>tracedb</strong>)</p></td>
<td align="left"><p>HKLM\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Image File Execution Options&lt;em&gt;ImageFileName</em>&lt;strong&gt;StackTraceDatabaseSizeInMb</strong></p></td>
</tr>
<tr class="even">
<td align="left"><p>创建用户模式堆栈跟踪数据库 (ust，0x1000) 的图像文件</p></td>
<td align="left"><p>Windows 将图像文件名称添加到 USTEnabled 注册表项的值 (HKLM\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Image File Execution Options&lt;强&gt;USTEnabled</strong>)。</p></td>
</tr>
<tr class="odd">
<td align="left"><p>在可能的情况下大型页加载映像</p></td>
<td align="left"><p>HKLM\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Image File Execution Options&lt;全身&gt;映像文件名</em>&lt;强&gt;UseLargePages</strong>。</p></td>
</tr>
<tr class="even">
<td align="left"><p>特殊池</p>
<p>（内核特殊池标记）</p></td>
<td align="left"><p>HKLM\SYSTEM\CurrentControlSet\Control\Session Manager\Memory Management&lt;strong&gt;PoolTag</strong></p></td>
</tr>
<tr class="odd">
<td align="left"><p>验证开始/验证结束</p></td>
<td align="left"><p>HKLM\SYSTEM\CurrentControlSet\Control\Session Manager\Memory Management\PoolTagOverruns. <strong>验证启动</strong>选项设置为 0 的值。 <strong>验证结束</strong>选项的值设置为 1。</p></td>
</tr>
<tr class="even">
<td align="left"><p>图像文件的调试器</p></td>
<td align="left"><p>HKLM\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Image File Execution Options&lt;全身&gt;映像文件名</em>&lt;强&gt;调试器</strong></p></td>
</tr>
<tr class="odd">
<td align="left"><p>对象引用跟踪</p></td>
<td align="left"><p>HKLM\SYSTEM\CurrentControlSet\Control\Session Manager\Kernel&lt;strong&gt;ObTraceProcessName</strong>, <strong>ObTracePermanent</strong> and <strong>ObTracePoolTags</strong></p></td>
</tr>
</tbody>
</table>

 

 

 




