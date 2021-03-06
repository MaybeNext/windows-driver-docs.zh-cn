---
title: 使用设备安装函数
description: 使用设备安装函数
ms.assetid: a7cfa359-a45c-45fa-a854-ee70de66b12e
keywords:
- 安装程序 Api 函数 WDK，设备安装函数
- 设备安装函数 WDK SetupAPI
ms.date: 04/20/2017
ms.localizationpriority: medium
ms.openlocfilehash: a8201aacada4f2f5d09d6665f4167c20750d91d1
ms.sourcegitcommit: fb7d95c7a5d47860918cd3602efdd33b69dcf2da
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/25/2019
ms.locfileid: "67384767"
---
# <a name="using-device-installation-functions"></a>使用设备安装函数





本部分总结了[设备安装函数](https://docs.microsoft.com/previous-versions/ff541299(v=vs.85))。 通过使用设备安装功能，安装软件可以执行以下类型的操作：

-   安装驱动程序

-   处理 DIF 代码。

-   管理设备信息设置。

-   管理驱动程序列表。

-   管理设备接口。

-   管理图标和其他位图。

若要执行本部分中描述的安装程序 Api 函数不支持的设备安装操作，调用适当[常规安装函数](https://docs.microsoft.com/previous-versions/ff544985(v=vs.85))或[即插即用 Configuration Manager 功能](https://docs.microsoft.com/previous-versions/ff549717(v=vs.85))(CM_*Xxx*函数<em>)。</em>

下表提供以下类型的函数的摘要：

[驱动程序安装函数](#ddk-update-driver-function-dg)

[设备信息函数](#ddk-setupdi-device-information-functions-dg)

[驱动程序信息函数](#ddk-setupdi-driver-information-functions-dg)

[驱动程序选择函数](#ddk-setupdi-driver-selection-functions-dg)

[设备安装处理程序](#ddk-setupdi-device-installation-handlers-dg)

[设备安装自定义函数](#ddk-setupdi-device-installation-customization-functions-dg)

[安装程序类函数](#ddk-setupdi-setup-class-functions-dg)

[位图和图标函数](#ddk-setupdi-class-bitmap-and-icon-functions-dg)

[设备接口函数](#ddk-setupdi-device-interface-functions-dg)

[设备属性函数 (Windows Vista 及更高版本)](#ddk-setupdi-device-property-functions-dg)

[注册表函数](#ddk-setupdi-registry-functions-dg)

[其他函数](#ddk-other-setupdi-functions-dg)

### <a href="" id="ddk-update-driver-function-dg"></a>驱动程序安装函数

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td align="left"><p><a href="https://docs.microsoft.com/windows/desktop/api/newdev/nf-newdev-diinstalldevice" data-raw-source="[&lt;strong&gt;DiInstallDevice&lt;/strong&gt;](https://docs.microsoft.com/windows/desktop/api/newdev/nf-newdev-diinstalldevice)"><strong>DiInstallDevice</strong></a></p></td>
<td align="left"><p>安装指定的驱动程序中已预装<a href="driver-store.md" data-raw-source="[driver store](driver-store.md)">驱动程序存储区</a>系统中存在的即插即用设备上。 （Windows Vista 和更高版本的 Windows）</p></td>
</tr>
<tr class="even">
<td align="left"><p><a href="https://docs.microsoft.com/windows/desktop/api/newdev/nf-newdev-diinstalldrivera" data-raw-source="[&lt;strong&gt;DiInstallDriver&lt;/strong&gt;](https://docs.microsoft.com/windows/desktop/api/newdev/nf-newdev-diinstalldrivera)"><strong>DiInstallDriver</strong></a></p></td>
<td align="left"><p>预安装了驱动程序存储区中的驱动程序，然后将匹配的系统中存在的即插即用设备上安装驱动程序。 （Windows Vista 和更高版本的 Windows）</p></td>
</tr>
<tr class="odd">
<td align="left"><p><a href="https://docs.microsoft.com/windows/desktop/api/newdev/nf-newdev-dirollbackdriver" data-raw-source="[&lt;strong&gt;DiRollbackDriver&lt;/strong&gt;](https://docs.microsoft.com/windows/desktop/api/newdev/nf-newdev-dirollbackdriver)"><strong>DiRollbackDriver</strong></a></p></td>
<td align="left"><p>回滚到为设备设置的备份驱动程序在指定设备安装的驱动程序。 （Windows Vista 和更高版本的 Windows）</p></td>
</tr>
<tr class="even">
<td align="left"><p><a href="https://docs.microsoft.com/windows/desktop/api/newdev/nf-newdev-dishowupdatedevice" data-raw-source="[&lt;strong&gt;DiShowUpdateDevice&lt;/strong&gt;](https://docs.microsoft.com/windows/desktop/api/newdev/nf-newdev-dishowupdatedevice)"><strong>DiShowUpdateDevice</strong></a></p></td>
<td align="left"><p>显示指定设备的硬件更新向导。 （Windows Vista 和更高版本的 Windows）</p></td>
</tr>
<tr class="odd">
<td align="left"><p><a href="https://docs.microsoft.com/windows/desktop/api/newdev/nf-newdev-diuninstalldevice" data-raw-source="[&lt;strong&gt;DiUninstallDevice&lt;/strong&gt;](https://docs.microsoft.com/windows/desktop/api/newdev/nf-newdev-diuninstalldevice)"><strong>DiUninstallDevice</strong></a></p></td>
<td align="left"><p>卸载设备并删除其设备节点 (<a href="https://docs.microsoft.com/windows-hardware/drivers/#wdkgloss-devnode" data-raw-source="&lt;em&gt;devnode&lt;/em&gt;"><em>devnode</em></a>)) 从系统。 （Windows 7 和更高版本的 Windows）</p></td>
</tr>
<tr class="even">
<td align="left"><p><a href="https://docs.microsoft.com/windows-hardware/drivers/install/installselecteddriver" data-raw-source="[&lt;strong&gt;InstallSelectedDriver&lt;/strong&gt;](https://docs.microsoft.com/windows-hardware/drivers/install/installselecteddriver)"><strong>InstallSelectedDriver</strong></a></p></td>
<td align="left"><p>在所选的设备上安装了所选驱动程序。</p></td>
</tr>
<tr class="odd">
<td align="left"><p><a href="https://docs.microsoft.com/windows/desktop/api/newdev/nf-newdev-updatedriverforplugandplaydevicesa" data-raw-source="[&lt;strong&gt;UpdateDriverForPlugAndPlayDevices&lt;/strong&gt;](https://docs.microsoft.com/windows/desktop/api/newdev/nf-newdev-updatedriverforplugandplaydevicesa)"><strong>UpdateDriverForPlugAndPlayDevices</strong></a></p></td>
<td align="left"><p>更新为匹配的系统中存在的即插即用设备安装的功能驱动程序。</p></td>
</tr>
</tbody>
</table>

 

### <a href="" id="ddk-setupdi-device-information-functions-dg"></a>设备信息函数

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td align="left"><p><a href="https://docs.microsoft.com/windows/desktop/api/setupapi/nf-setupapi-setupdicreatedeviceinfolist" data-raw-source="[&lt;strong&gt;SetupDiCreateDeviceInfoList&lt;/strong&gt;](https://docs.microsoft.com/windows/desktop/api/setupapi/nf-setupapi-setupdicreatedeviceinfolist)"><strong>SetupDiCreateDeviceInfoList</strong></a></p></td>
<td align="left"><p>创建一个空<a href="device-information-sets.md" data-raw-source="[device information set](device-information-sets.md)">设备信息集</a>。 此组可以与类 GUID 相关联。</p></td>
</tr>
<tr class="even">
<td align="left"><p><a href="https://docs.microsoft.com/windows/desktop/api/setupapi/nf-setupapi-setupdicreatedeviceinfolistexa" data-raw-source="[&lt;strong&gt;SetupDiCreateDeviceInfoListEx&lt;/strong&gt;](https://docs.microsoft.com/windows/desktop/api/setupapi/nf-setupapi-setupdicreatedeviceinfolistexa)"><strong>SetupDiCreateDeviceInfoListEx</strong></a></p></td>
<td align="left"><p>创建一个空的设备信息集。 这组类 GUID 与相关联，并且可以是远程计算机上的设备。</p></td>
</tr>
<tr class="odd">
<td align="left"><p><a href="https://docs.microsoft.com/windows/desktop/api/setupapi/nf-setupapi-setupdicreatedeviceinfoa" data-raw-source="[&lt;strong&gt;SetupDiCreateDeviceInfo&lt;/strong&gt;](https://docs.microsoft.com/windows/desktop/api/setupapi/nf-setupapi-setupdicreatedeviceinfoa)"><strong>SetupDiCreateDeviceInfo</strong></a></p></td>
<td align="left"><p>创建新的设备信息元素并将其作为新成员添加到指定的设备信息设置。</p></td>
</tr>
<tr class="even">
<td align="left"><p><a href="https://docs.microsoft.com/windows/desktop/api/setupapi/nf-setupapi-setupdiopendeviceinfoa" data-raw-source="[&lt;strong&gt;SetupDiOpenDeviceInfo&lt;/strong&gt;](https://docs.microsoft.com/windows/desktop/api/setupapi/nf-setupapi-setupdiopendeviceinfoa)"><strong>SetupDiOpenDeviceInfo</strong></a></p></td>
<td align="left"><p>检索有关现有实例的设备信息并将其添加到指定的设备信息设置。</p></td>
</tr>
<tr class="odd">
<td align="left"><p><a href="https://docs.microsoft.com/windows/desktop/api/setupapi/nf-setupapi-setupdienumdeviceinfo" data-raw-source="[&lt;strong&gt;SetupDiEnumDeviceInfo&lt;/strong&gt;](https://docs.microsoft.com/windows/desktop/api/setupapi/nf-setupapi-setupdienumdeviceinfo)"><strong>SetupDiEnumDeviceInfo</strong></a></p></td>
<td align="left"><p>返回设备信息元素的设备信息集的上下文的结构。</p></td>
</tr>
<tr class="even">
<td align="left"><p><a href="https://docs.microsoft.com/windows/desktop/api/setupapi/nf-setupapi-setupdigetdeviceinstanceida" data-raw-source="[&lt;strong&gt;SetupDiGetDeviceInstanceId&lt;/strong&gt;](https://docs.microsoft.com/windows/desktop/api/setupapi/nf-setupapi-setupdigetdeviceinstanceida)"><strong>SetupDiGetDeviceInstanceId</strong></a></p></td>
<td align="left"><p>检索设备信息元素与关联的设备实例 ID。</p></td>
</tr>
<tr class="odd">
<td align="left"><p><a href="https://docs.microsoft.com/windows/desktop/api/setupapi/nf-setupapi-setupdigetdeviceinfolistclass" data-raw-source="[&lt;strong&gt;SetupDiGetDeviceInfoListClass&lt;/strong&gt;](https://docs.microsoft.com/windows/desktop/api/setupapi/nf-setupapi-setupdigetdeviceinfolistclass)"><strong>SetupDiGetDeviceInfoListClass</strong></a></p></td>
<td align="left"><p>检索设备信息设置如果它具有一个关联的类关联的 GUID 的类。</p></td>
</tr>
<tr class="even">
<td align="left"><p><a href="https://docs.microsoft.com/windows/desktop/api/setupapi/nf-setupapi-setupdigetdeviceinfolistdetaila" data-raw-source="[&lt;strong&gt;SetupDiGetDeviceInfoListDetail&lt;/strong&gt;](https://docs.microsoft.com/windows/desktop/api/setupapi/nf-setupapi-setupdigetdeviceinfolistdetaila)"><strong>SetupDiGetDeviceInfoListDetail</strong></a></p></td>
<td align="left"><p>检索设备信息设置包括类 GUID、 远程计算机句柄和远程计算机的名称相关联的信息。</p></td>
</tr>
<tr class="odd">
<td align="left"><p><a href="https://docs.microsoft.com/windows/desktop/api/setupapi/nf-setupapi-setupdigetclassdevpropertysheetsa" data-raw-source="[&lt;strong&gt;SetupDiGetClassDevPropertySheets&lt;/strong&gt;](https://docs.microsoft.com/windows/desktop/api/setupapi/nf-setupapi-setupdigetclassdevpropertysheetsa)"><strong>SetupDiGetClassDevPropertySheets</strong></a></p></td>
<td align="left"><p>检索指向指定的设备信息元素或属性表的句柄<a href="device-setup-classes.md" data-raw-source="[device setup class](device-setup-classes.md)">设备安装程序类</a>指定的设备信息设置。</p></td>
</tr>
<tr class="even">
<td align="left"><p><a href="https://docs.microsoft.com/windows/desktop/api/setupapi/nf-setupapi-setupdigetclassdevsw" data-raw-source="[&lt;strong&gt;SetupDiGetClassDevs&lt;/strong&gt;](https://docs.microsoft.com/windows/desktop/api/setupapi/nf-setupapi-setupdigetclassdevsw)"><strong>SetupDiGetClassDevs</strong></a></p></td>
<td align="left"><p>返回包含指定类的所有设备的设备信息集。</p></td>
</tr>
<tr class="odd">
<td align="left"><p><a href="https://docs.microsoft.com/windows/desktop/api/setupapi/nf-setupapi-setupdigetclassdevsexa" data-raw-source="[&lt;strong&gt;SetupDiGetClassDevsEx&lt;/strong&gt;](https://docs.microsoft.com/windows/desktop/api/setupapi/nf-setupapi-setupdigetclassdevsexa)"><strong>SetupDiGetClassDevsEx</strong></a></p></td>
<td align="left"><p>返回包含指定类的本地或远程计算机上的所有设备的设备信息集。</p></td>
</tr>
<tr class="even">
<td align="left"><p><a href="https://docs.microsoft.com/windows/desktop/api/setupapi/nf-setupapi-setupdisetselecteddevice" data-raw-source="[&lt;strong&gt;SetupDiSetSelectedDevice&lt;/strong&gt;](https://docs.microsoft.com/windows/desktop/api/setupapi/nf-setupapi-setupdisetselecteddevice)"><strong>SetupDiSetSelectedDevice</strong></a></p></td>
<td align="left"><p>设置为当前所选的设备信息的成员的指定的设备信息元素集。 安装向导通常使用此函数。</p></td>
</tr>
<tr class="odd">
<td align="left"><p><a href="https://docs.microsoft.com/windows/desktop/api/setupapi/nf-setupapi-setupdigetselecteddevice" data-raw-source="[&lt;strong&gt;SetupDiGetSelectedDevice&lt;/strong&gt;](https://docs.microsoft.com/windows/desktop/api/setupapi/nf-setupapi-setupdigetselecteddevice)"><strong>SetupDiGetSelectedDevice</strong></a></p></td>
<td align="left"><p>检索指定的设备信息设置的当前所选设备。</p></td>
</tr>
<tr class="even">
<td align="left"><p><a href="https://docs.microsoft.com/windows/desktop/api/setupapi/nf-setupapi-setupdiregisterdeviceinfo" data-raw-source="[&lt;strong&gt;SetupDiRegisterDeviceInfo&lt;/strong&gt;](https://docs.microsoft.com/windows/desktop/api/setupapi/nf-setupapi-setupdiregisterdeviceinfo)"><strong>SetupDiRegisterDeviceInfo</strong></a></p></td>
<td align="left"><p>在插管理器注册一个新创建的设备实例。</p></td>
</tr>
<tr class="odd">
<td align="left"><p><a href="https://docs.microsoft.com/windows/desktop/api/setupapi/nf-setupapi-setupdideletedeviceinfo" data-raw-source="[&lt;strong&gt;SetupDiDeleteDeviceInfo&lt;/strong&gt;](https://docs.microsoft.com/windows/desktop/api/setupapi/nf-setupapi-setupdideletedeviceinfo)"><strong>SetupDiDeleteDeviceInfo</strong></a></p></td>
<td align="left"><p>从指定的设备信息组中删除成员。 此函数不会删除实际的设备。</p></td>
</tr>
<tr class="even">
<td align="left"><p><a href="https://docs.microsoft.com/windows/desktop/api/setupapi/nf-setupapi-setupdidestroydeviceinfolist" data-raw-source="[&lt;strong&gt;SetupDiDestroyDeviceInfoList&lt;/strong&gt;](https://docs.microsoft.com/windows/desktop/api/setupapi/nf-setupapi-setupdidestroydeviceinfolist)"><strong>SetupDiDestroyDeviceInfoList</strong></a></p></td>
<td align="left"><p>销毁设备信息集并释放所有关联的内存。</p></td>
</tr>
</tbody>
</table>

 

### <a href="" id="ddk-setupdi-driver-information-functions-dg"></a>驱动程序信息函数

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td align="left"><p><a href="https://docs.microsoft.com/windows/desktop/api/setupapi/nf-setupapi-setupdibuilddriverinfolist" data-raw-source="[&lt;strong&gt;SetupDiBuildDriverInfoList&lt;/strong&gt;](https://docs.microsoft.com/windows/desktop/api/setupapi/nf-setupapi-setupdibuilddriverinfolist)"><strong>SetupDiBuildDriverInfoList</strong></a></p></td>
<td align="left"><p>生成与指定的设备实例或设备信息设置的全局类驱动程序列表关联的驱动程序的列表。</p></td>
</tr>
<tr class="even">
<td align="left"><p><a href="https://docs.microsoft.com/windows/desktop/api/setupapi/nf-setupapi-setupdienumdriverinfoa" data-raw-source="[&lt;strong&gt;SetupDiEnumDriverInfo&lt;/strong&gt;](https://docs.microsoft.com/windows/desktop/api/setupapi/nf-setupapi-setupdienumdriverinfoa)"><strong>SetupDiEnumDriverInfo</strong></a></p></td>
<td align="left"><p>枚举驱动程序的信息列表中的成员。</p></td>
</tr>
<tr class="odd">
<td align="left"><p><a href="https://docs.microsoft.com/windows/desktop/api/setupapi/nf-setupapi-setupdigetdriverinfodetaila" data-raw-source="[&lt;strong&gt;SetupDiGetDriverInfoDetail&lt;/strong&gt;](https://docs.microsoft.com/windows/desktop/api/setupapi/nf-setupapi-setupdigetdriverinfodetaila)"><strong>SetupDiGetDriverInfoDetail</strong></a></p></td>
<td align="left"><p>检索指定的驱动程序信息元素的详细的信息。</p></td>
</tr>
<tr class="even">
<td align="left"><p><a href="https://docs.microsoft.com/windows/desktop/api/setupapi/nf-setupapi-setupdisetselecteddrivera" data-raw-source="[&lt;strong&gt;SetupDiSetSelectedDriver&lt;/strong&gt;](https://docs.microsoft.com/windows/desktop/api/setupapi/nf-setupapi-setupdisetselecteddrivera)"><strong>SetupDiSetSelectedDriver</strong></a></p></td>
<td align="left"><p>将驱动程序列表的指定的成员设置为当前所选的驱动程序。 此外可以用于重置驱动程序列表，以便任何当前所选驱动程序。</p></td>
</tr>
<tr class="odd">
<td align="left"><p><a href="https://docs.microsoft.com/windows/desktop/api/setupapi/nf-setupapi-setupdigetselecteddrivera" data-raw-source="[&lt;strong&gt;SetupDiGetSelectedDriver&lt;/strong&gt;](https://docs.microsoft.com/windows/desktop/api/setupapi/nf-setupapi-setupdigetselecteddrivera)"><strong>SetupDiGetSelectedDriver</strong></a></p></td>
<td align="left"><p>检索被选为驱动程序安装的驱动程序列表的成员。</p></td>
</tr>
<tr class="even">
<td align="left"><p><a href="https://docs.microsoft.com/windows/desktop/api/setupapi/nf-setupapi-setupdicanceldriverinfosearch" data-raw-source="[&lt;strong&gt;SetupDiCancelDriverInfoSearch&lt;/strong&gt;](https://docs.microsoft.com/windows/desktop/api/setupapi/nf-setupapi-setupdicanceldriverinfosearch)"><strong>SetupDiCancelDriverInfoSearch</strong></a></p></td>
<td align="left"><p>取消当前正在不同线程中的驱动程序列表中搜索。</p></td>
</tr>
<tr class="odd">
<td align="left"><p><a href="https://docs.microsoft.com/windows/desktop/api/setupapi/nf-setupapi-setupdidestroydriverinfolist" data-raw-source="[&lt;strong&gt;SetupDiDestroyDriverInfoList&lt;/strong&gt;](https://docs.microsoft.com/windows/desktop/api/setupapi/nf-setupapi-setupdidestroydriverinfolist)"><strong>SetupDiDestroyDriverInfoList</strong></a></p></td>
<td align="left"><p>销毁驱动程序的信息列表。</p></td>
</tr>
</tbody>
</table>

 

### <a href="" id="ddk-setupdi-driver-selection-functions-dg"></a>驱动程序选择函数

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td align="left"><p><a href="https://docs.microsoft.com/windows/desktop/api/setupapi/nf-setupapi-setupdiaskforoemdisk" data-raw-source="[&lt;strong&gt;SetupDiAskForOEMDisk&lt;/strong&gt;](https://docs.microsoft.com/windows/desktop/api/setupapi/nf-setupapi-setupdiaskforoemdisk)"><strong>SetupDiAskForOEMDisk</strong></a></p></td>
<td align="left"><p>显示一个对话框，要求用户提供 OEM 安装磁盘的路径。</p></td>
</tr>
<tr class="even">
<td align="left"><p><a href="https://docs.microsoft.com/windows/desktop/api/setupapi/nf-setupapi-setupdiselectoemdrv" data-raw-source="[&lt;strong&gt;SetupDiSelectOEMDrv&lt;/strong&gt;](https://docs.microsoft.com/windows/desktop/api/setupapi/nf-setupapi-setupdiselectoemdrv)"><strong>SetupDiSelectOEMDrv</strong></a></p></td>
<td align="left"><p>选择通过使用 OEM 路径的用户提供的设备的驱动程序。</p></td>
</tr>
<tr class="odd">
<td align="left"><p><a href="https://docs.microsoft.com/windows/desktop/api/setupapi/nf-setupapi-setupdiselectdevice" data-raw-source="[&lt;strong&gt;SetupDiSelectDevice&lt;/strong&gt;](https://docs.microsoft.com/windows/desktop/api/setupapi/nf-setupapi-setupdiselectdevice)"><strong>SetupDiSelectDevice</strong></a></p></td>
<td align="left"><p>DIF_SELECTDEVICE 请求的默认处理程序。</p></td>
</tr>
</tbody>
</table>

 

### <a href="" id="ddk-setupdi-device-installation-handlers-dg"></a>设备安装处理程序

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td align="left"><p><a href="https://docs.microsoft.com/windows/desktop/api/setupapi/nf-setupapi-setupdicallclassinstaller" data-raw-source="[&lt;strong&gt;SetupDiCallClassInstaller&lt;/strong&gt;](https://docs.microsoft.com/windows/desktop/api/setupapi/nf-setupapi-setupdicallclassinstaller)"><strong>SetupDiCallClassInstaller</strong></a></p></td>
<td align="left"><p>调用适当的类安装程序，以及任何注册与指定的安装请求的共同安装程序。</p></td>
</tr>
<tr class="even">
<td align="left"><p><a href="https://docs.microsoft.com/windows/desktop/api/setupapi/nf-setupapi-setupdichangestate" data-raw-source="[&lt;strong&gt;SetupDiChangeState&lt;/strong&gt;](https://docs.microsoft.com/windows/desktop/api/setupapi/nf-setupapi-setupdichangestate)"><strong>SetupDiChangeState</strong></a></p></td>
<td align="left"><p>DIF_PROPERTYCHANGE 请求默认处理程序。 它可以用于更改已安装的设备的状态。</p></td>
</tr>
<tr class="odd">
<td align="left"><p><a href="https://docs.microsoft.com/windows/desktop/api/setupapi/nf-setupapi-setupdiregistercodeviceinstallers" data-raw-source="[&lt;strong&gt;SetupDiRegisterCoDeviceInstallers&lt;/strong&gt;](https://docs.microsoft.com/windows/desktop/api/setupapi/nf-setupapi-setupdiregistercodeviceinstallers)"><strong>SetupDiRegisterCoDeviceInstallers</strong></a></p></td>
<td align="left"><p>注册指定的设备 INF 文件中列出的特定于设备的共同安装程序。 此函数是 DIF_REGISTER_COINSTALLERS 的默认处理程序。</p></td>
</tr>
<tr class="even">
<td align="left"><p><a href="https://docs.microsoft.com/windows/desktop/api/setupapi/nf-setupapi-setupdiinstalldevice" data-raw-source="[&lt;strong&gt;SetupDiInstallDevice&lt;/strong&gt;](https://docs.microsoft.com/windows/desktop/api/setupapi/nf-setupapi-setupdiinstalldevice)"><strong>SetupDiInstallDevice</strong></a></p></td>
<td align="left"><p>DIF_INSTALLDEVICE 请求默认处理程序。</p></td>
</tr>
<tr class="odd">
<td align="left"><p><a href="https://docs.microsoft.com/windows/desktop/api/setupapi/nf-setupapi-setupdiinstalldriverfiles" data-raw-source="[&lt;strong&gt;SetupDiInstallDriverFiles&lt;/strong&gt;](https://docs.microsoft.com/windows/desktop/api/setupapi/nf-setupapi-setupdiinstalldriverfiles)"><strong>SetupDiInstallDriverFiles</strong></a></p></td>
<td align="left"><p>DIF_INSTALLDEVICEFILES 请求默认处理程序。</p></td>
</tr>
<tr class="even">
<td align="left"><p><a href="https://docs.microsoft.com/windows/desktop/api/setupapi/nf-setupapi-setupdiinstalldeviceinterfaces" data-raw-source="[&lt;strong&gt;SetupDiInstallDeviceInterfaces&lt;/strong&gt;](https://docs.microsoft.com/windows/desktop/api/setupapi/nf-setupapi-setupdiinstalldeviceinterfaces)"><strong>SetupDiInstallDeviceInterfaces</strong></a></p></td>
<td align="left"><p>DIF_INSTALLINTERFACES 请求默认处理程序。 它将安装中列出的接口<em>DDInstall</em>。<strong>接口</strong>设备 INF 文件部分。</p></td>
</tr>
<tr class="odd">
<td align="left"><p><a href="https://docs.microsoft.com/windows-hardware/drivers/install/setupdimoveduplicatedevice" data-raw-source="[&lt;strong&gt;SetupDiMoveDuplicateDevice&lt;/strong&gt;](https://docs.microsoft.com/windows-hardware/drivers/install/setupdimoveduplicatedevice)"><strong>SetupDiMoveDuplicateDevice</strong></a></p></td>
<td align="left"><p>此函数已过时，不能在任何版本的 Microsoft Windows 中使用。</p></td>
</tr>
<tr class="even">
<td align="left"><p><a href="https://docs.microsoft.com/windows/desktop/api/setupapi/nf-setupapi-setupdiremovedevice" data-raw-source="[&lt;strong&gt;SetupDiRemoveDevice&lt;/strong&gt;](https://docs.microsoft.com/windows/desktop/api/setupapi/nf-setupapi-setupdiremovedevice)"><strong>SetupDiRemoveDevice</strong></a></p></td>
<td align="left"><p>DIF_REMOVEDEVICE 请求默认处理程序。</p></td>
</tr>
<tr class="odd">
<td align="left"><p><a href="https://docs.microsoft.com/windows/desktop/api/setupapi/nf-setupapi-setupdiunremovedevice" data-raw-source="[&lt;strong&gt;SetupDiUnremoveDevice&lt;/strong&gt;](https://docs.microsoft.com/windows/desktop/api/setupapi/nf-setupapi-setupdiunremovedevice)"><strong>SetupDiUnremoveDevice</strong></a></p></td>
<td align="left"><p>DIF_UNREMOVE 请求默认处理程序。</p></td>
</tr>
<tr class="even">
<td align="left"><p><a href="https://docs.microsoft.com/windows/desktop/api/setupapi/nf-setupapi-setupdiregisterdeviceinfo" data-raw-source="[&lt;strong&gt;SetupDiRegisterDeviceInfo&lt;/strong&gt;](https://docs.microsoft.com/windows/desktop/api/setupapi/nf-setupapi-setupdiregisterdeviceinfo)"><strong>SetupDiRegisterDeviceInfo</strong></a></p></td>
<td align="left"><p>DIF_REGISTERDEVICE 请求默认处理程序。</p></td>
</tr>
<tr class="odd">
<td align="left"><p><a href="https://docs.microsoft.com/windows/desktop/api/setupapi/nf-setupapi-setupdiselectdevice" data-raw-source="[&lt;strong&gt;SetupDiSelectDevice&lt;/strong&gt;](https://docs.microsoft.com/windows/desktop/api/setupapi/nf-setupapi-setupdiselectdevice)"><strong>SetupDiSelectDevice</strong></a></p></td>
<td align="left"><p>DIF_SELECTDEVICE 请求默认处理程序。</p></td>
</tr>
<tr class="even">
<td align="left"><p><a href="https://docs.microsoft.com/windows/desktop/api/setupapi/nf-setupapi-setupdiselectbestcompatdrv" data-raw-source="[&lt;strong&gt;SetupDiSelectBestCompatDrv&lt;/strong&gt;](https://docs.microsoft.com/windows/desktop/api/setupapi/nf-setupapi-setupdiselectbestcompatdrv)"><strong>SetupDiSelectBestCompatDrv</strong></a></p></td>
<td align="left"><p>DIF_SELECTBESTCOMPATDRV 请求默认处理程序。</p></td>
</tr>
</tbody>
</table>

 

### <a href="" id="ddk-setupdi-device-installation-customization-functions-dg"></a>设备安装自定义函数

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td align="left"><p><a href="https://docs.microsoft.com/windows/desktop/api/setupapi/nf-setupapi-setupdigetclassinstallparamsa" data-raw-source="[&lt;strong&gt;SetupDiGetClassInstallParams&lt;/strong&gt;](https://docs.microsoft.com/windows/desktop/api/setupapi/nf-setupapi-setupdigetclassinstallparamsa)"><strong>SetupDiGetClassInstallParams</strong></a></p></td>
<td align="left"><p>检索设备信息集或特定设备信息元素的类安装参数。</p></td>
</tr>
<tr class="even">
<td align="left"><p><a href="https://docs.microsoft.com/windows/desktop/api/setupapi/nf-setupapi-setupdisetclassinstallparamsa" data-raw-source="[&lt;strong&gt;SetupDiSetClassInstallParams&lt;/strong&gt;](https://docs.microsoft.com/windows/desktop/api/setupapi/nf-setupapi-setupdisetclassinstallparamsa)"><strong>SetupDiSetClassInstallParams</strong></a></p></td>
<td align="left"><p>设置或清除的设备信息集或特定设备信息元素的类安装参数。</p></td>
</tr>
<tr class="odd">
<td align="left"><p><a href="https://docs.microsoft.com/windows/desktop/api/setupapi/nf-setupapi-setupdigetdeviceinstallparamsa" data-raw-source="[&lt;strong&gt;SetupDiGetDeviceInstallParams&lt;/strong&gt;](https://docs.microsoft.com/windows/desktop/api/setupapi/nf-setupapi-setupdigetdeviceinstallparamsa)"><strong>SetupDiGetDeviceInstallParams</strong></a></p></td>
<td align="left"><p>检索设备信息集或特定设备信息元素的设备安装参数。</p></td>
</tr>
<tr class="even">
<td align="left"><p><a href="https://docs.microsoft.com/windows/desktop/api/setupapi/nf-setupapi-setupdisetdeviceinstallparamsa" data-raw-source="[&lt;strong&gt;SetupDiSetDeviceInstallParams&lt;/strong&gt;](https://docs.microsoft.com/windows/desktop/api/setupapi/nf-setupapi-setupdisetdeviceinstallparamsa)"><strong>SetupDiSetDeviceInstallParams</strong></a></p></td>
<td align="left"><p>设置设备的信息集或特定设备信息元素的设备安装参数。</p></td>
</tr>
<tr class="odd">
<td align="left"><p><a href="https://docs.microsoft.com/windows/desktop/api/setupapi/nf-setupapi-setupdigetdriverinstallparamsa" data-raw-source="[&lt;strong&gt;SetupDiGetDriverInstallParams&lt;/strong&gt;](https://docs.microsoft.com/windows/desktop/api/setupapi/nf-setupapi-setupdigetdriverinstallparamsa)"><strong>SetupDiGetDriverInstallParams</strong></a></p></td>
<td align="left"><p>检索安装参数指定的驱动程序。</p></td>
</tr>
<tr class="even">
<td align="left"><p><a href="https://docs.microsoft.com/windows/desktop/api/setupapi/nf-setupapi-setupdisetdriverinstallparamsa" data-raw-source="[&lt;strong&gt;SetupDiSetDriverInstallParams&lt;/strong&gt;](https://docs.microsoft.com/windows/desktop/api/setupapi/nf-setupapi-setupdisetdriverinstallparamsa)"><strong>SetupDiSetDriverInstallParams</strong></a></p></td>
<td align="left"><p>设置指定的驱动程序的安装参数。</p></td>
</tr>
</tbody>
</table>

 

### <a href="" id="ddk-setupdi-setup-class-functions-dg"></a>安装程序类函数

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td align="left"><p><a href="https://docs.microsoft.com/windows/desktop/api/setupapi/nf-setupapi-setupdibuildclassinfolist" data-raw-source="[&lt;strong&gt;SetupDiBuildClassInfoList&lt;/strong&gt;](https://docs.microsoft.com/windows/desktop/api/setupapi/nf-setupapi-setupdibuildclassinfolist)"><strong>SetupDiBuildClassInfoList</strong></a></p></td>
<td align="left"><p>返回安装程序的列表包含在系统上安装的每个类的类 Guid。</p></td>
</tr>
<tr class="even">
<td align="left"><p><a href="https://docs.microsoft.com/windows/desktop/api/setupapi/nf-setupapi-setupdibuildclassinfolistexa" data-raw-source="[&lt;strong&gt;SetupDiBuildClassInfoListEx&lt;/strong&gt;](https://docs.microsoft.com/windows/desktop/api/setupapi/nf-setupapi-setupdibuildclassinfolistexa)"><strong>SetupDiBuildClassInfoListEx</strong></a></p></td>
<td align="left"><p>返回安装程序的列表包括本地系统或远程系统上安装的每个类的类 Guid。</p></td>
</tr>
<tr class="odd">
<td align="left"><p><a href="https://docs.microsoft.com/windows/desktop/api/setupapi/nf-setupapi-setupdigetclassdescriptiona" data-raw-source="[&lt;strong&gt;SetupDiGetClassDescription&lt;/strong&gt;](https://docs.microsoft.com/windows/desktop/api/setupapi/nf-setupapi-setupdigetclassdescriptiona)"><strong>SetupDiGetClassDescription</strong></a></p></td>
<td align="left"><p>检索与指定的安装程序类 GUID 关联的类说明。</p></td>
</tr>
<tr class="even">
<td align="left"><p><a href="https://docs.microsoft.com/windows/desktop/api/setupapi/nf-setupapi-setupdigetclassdescriptionexa" data-raw-source="[&lt;strong&gt;SetupDiGetClassDescriptionEx&lt;/strong&gt;](https://docs.microsoft.com/windows/desktop/api/setupapi/nf-setupapi-setupdigetclassdescriptionexa)"><strong>SetupDiGetClassDescriptionEx</strong></a></p></td>
<td align="left"><p>检索本地或远程计算机上安装的安装程序类的说明。</p></td>
</tr>
<tr class="odd">
<td align="left"><p><a href="https://docs.microsoft.com/windows/desktop/api/setupapi/nf-setupapi-setupdigetinfclassa" data-raw-source="[&lt;strong&gt;SetupDiGetINFClass&lt;/strong&gt;](https://docs.microsoft.com/windows/desktop/api/setupapi/nf-setupapi-setupdigetinfclassa)"><strong>SetupDiGetINFClass</strong></a></p></td>
<td align="left"><p>检索指定的设备 INF 文件的类。</p></td>
</tr>
<tr class="even">
<td align="left"><p><a href="https://docs.microsoft.com/windows/desktop/api/setupapi/nf-setupapi-setupdiclassguidsfromnamea" data-raw-source="[&lt;strong&gt;SetupDiClassGuidsFromName&lt;/strong&gt;](https://docs.microsoft.com/windows/desktop/api/setupapi/nf-setupapi-setupdiclassguidsfromnamea)"><strong>SetupDiClassGuidsFromName</strong></a></p></td>
<td align="left"><p>检索与指定的类名称相关联的 Guid。 此列表是基于生成系统上当前安装哪些类。</p></td>
</tr>
<tr class="odd">
<td align="left"><p><a href="https://docs.microsoft.com/windows/desktop/api/setupapi/nf-setupapi-setupdiclassguidsfromnameexa" data-raw-source="[&lt;strong&gt;SetupDiClassGuidsFromNameEx&lt;/strong&gt;](https://docs.microsoft.com/windows/desktop/api/setupapi/nf-setupapi-setupdiclassguidsfromnameexa)"><strong>SetupDiClassGuidsFromNameEx</strong></a></p></td>
<td align="left"><p>检索与指定的类名称相关联的 Guid。 此生成的列表包含当前安装在本地或远程计算机上的类。</p></td>
</tr>
<tr class="even">
<td align="left"><p><a href="https://docs.microsoft.com/windows/desktop/api/setupapi/nf-setupapi-setupdiclassnamefromguida" data-raw-source="[&lt;strong&gt;SetupDiClassNameFromGuid&lt;/strong&gt;](https://docs.microsoft.com/windows/desktop/api/setupapi/nf-setupapi-setupdiclassnamefromguida)"><strong>SetupDiClassNameFromGuid</strong></a></p></td>
<td align="left"><p>检索与类 GUID 关联的类名称。</p></td>
</tr>
<tr class="odd">
<td align="left"><p><a href="https://docs.microsoft.com/windows/desktop/api/setupapi/nf-setupapi-setupdiclassnamefromguidexa" data-raw-source="[&lt;strong&gt;SetupDiClassNameFromGuidEx&lt;/strong&gt;](https://docs.microsoft.com/windows/desktop/api/setupapi/nf-setupapi-setupdiclassnamefromguidexa)"><strong>SetupDiClassNameFromGuidEx</strong></a></p></td>
<td align="left"><p>检索与类 GUID 关联的类名称。 类可以安装在本地或远程计算机上。</p></td>
</tr>
<tr class="even">
<td align="left"><p><a href="https://docs.microsoft.com/windows/desktop/api/setupapi/nf-setupapi-setupdiinstallclassa" data-raw-source="[&lt;strong&gt;SetupDiInstallClass&lt;/strong&gt;](https://docs.microsoft.com/windows/desktop/api/setupapi/nf-setupapi-setupdiinstallclassa)"><strong>SetupDiInstallClass</strong></a></p></td>
<td align="left"><p>将安装<strong>ClassInstall32</strong>部分指定的 INF 文件。</p></td>
</tr>
<tr class="odd">
<td align="left"><p><a href="https://docs.microsoft.com/windows/desktop/api/setupapi/nf-setupapi-setupdiinstallclassexa" data-raw-source="[&lt;strong&gt;SetupDiInstallClassEx&lt;/strong&gt;](https://docs.microsoft.com/windows/desktop/api/setupapi/nf-setupapi-setupdiinstallclassexa)"><strong>SetupDiInstallClassEx</strong></a></p></td>
<td align="left"><p>安装类安装程序或接口类。</p></td>
</tr>
<tr class="even">
<td align="left"><p><a href="https://docs.microsoft.com/windows/desktop/api/setupapi/nf-setupapi-setupdiopenclassregkey" data-raw-source="[&lt;strong&gt;SetupDiOpenClassRegKey&lt;/strong&gt;](https://docs.microsoft.com/windows/desktop/api/setupapi/nf-setupapi-setupdiopenclassregkey)"><strong>SetupDiOpenClassRegKey</strong></a></p></td>
<td align="left"><p>此时将打开<a href="device-setup-classes.md" data-raw-source="[device setup class](device-setup-classes.md)">设备安装程序类</a>注册表项或类的特定子项。</p></td>
</tr>
<tr class="odd">
<td align="left"><p><a href="https://docs.microsoft.com/windows/desktop/api/setupapi/nf-setupapi-setupdiopenclassregkeyexa" data-raw-source="[&lt;strong&gt;SetupDiOpenClassRegKeyEx&lt;/strong&gt;](https://docs.microsoft.com/windows/desktop/api/setupapi/nf-setupapi-setupdiopenclassregkeyexa)"><strong>SetupDiOpenClassRegKeyEx</strong></a></p></td>
<td align="left"><p>打开设备安装程序类注册表项、 设备接口的类注册表项或类的特定子项。 此函数将打开指定的键在本地计算机或远程计算机上。</p></td>
</tr>
</tbody>
</table>

 

### <a href="" id="ddk-setupdi-class-bitmap-and-icon-functions-dg"></a>位图和图标函数

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td align="left"><p><a href="https://docs.microsoft.com/windows/desktop/api/setupapi/nf-setupapi-setupdigetclassimagelist" data-raw-source="[&lt;strong&gt;SetupDiGetClassImageList&lt;/strong&gt;](https://docs.microsoft.com/windows/desktop/api/setupapi/nf-setupapi-setupdigetclassimagelist)"><strong>SetupDiGetClassImageList</strong></a></p></td>
<td align="left"><p>生成图像列表包含已安装的每个类的位图，并返回一种数据结构中的列表。</p></td>
</tr>
<tr class="even">
<td align="left"><p><a href="https://docs.microsoft.com/windows/desktop/api/setupapi/nf-setupapi-setupdigetclassimagelistexa" data-raw-source="[&lt;strong&gt;SetupDiGetClassImageListEx&lt;/strong&gt;](https://docs.microsoft.com/windows/desktop/api/setupapi/nf-setupapi-setupdigetclassimagelistexa)"><strong>SetupDiGetClassImageListEx</strong></a></p></td>
<td align="left"><p>生成本地或远程计算机上安装的每个类的位图图像的列表。</p></td>
</tr>
<tr class="odd">
<td align="left"><p><a href="https://docs.microsoft.com/windows/desktop/api/setupapi/nf-setupapi-setupdigetclassimageindex" data-raw-source="[&lt;strong&gt;SetupDiGetClassImageIndex&lt;/strong&gt;](https://docs.microsoft.com/windows/desktop/api/setupapi/nf-setupapi-setupdigetclassimageindex)"><strong>SetupDiGetClassImageIndex</strong></a></p></td>
<td align="left"><p>检索指定类的类图像列表中的索引。</p></td>
</tr>
<tr class="even">
<td align="left"><p><a href="https://docs.microsoft.com/windows/desktop/api/setupapi/nf-setupapi-setupdigetclassbitmapindex" data-raw-source="[&lt;strong&gt;SetupDiGetClassBitmapIndex&lt;/strong&gt;](https://docs.microsoft.com/windows/desktop/api/setupapi/nf-setupapi-setupdigetclassbitmapindex)"><strong>SetupDiGetClassBitmapIndex</strong></a></p></td>
<td align="left"><p>检索指定的类提供的最小化图标的索引。</p></td>
</tr>
<tr class="odd">
<td align="left"><p><a href="https://docs.microsoft.com/windows/desktop/api/setupapi/nf-setupapi-setupdidrawminiicon" data-raw-source="[&lt;strong&gt;SetupDiDrawMiniIcon&lt;/strong&gt;](https://docs.microsoft.com/windows/desktop/api/setupapi/nf-setupapi-setupdidrawminiicon)"><strong>SetupDiDrawMiniIcon</strong></a></p></td>
<td align="left"><p>在请求的位置绘制指定的最小化图标。</p></td>
</tr>
<tr class="even">
<td align="left"><p><a href="https://docs.microsoft.com/windows/desktop/api/setupapi/nf-setupapi-setupdiloadclassicon" data-raw-source="[&lt;strong&gt;SetupDiLoadClassIcon&lt;/strong&gt;](https://docs.microsoft.com/windows/desktop/api/setupapi/nf-setupapi-setupdiloadclassicon)"><strong>SetupDiLoadClassIcon</strong></a></p></td>
<td align="left"><p>加载这两个大和最小化图标为指定的类。</p></td>
</tr>
<tr class="odd">
<td align="left"><p><a href="https://docs.microsoft.com/windows/desktop/api/setupapi/nf-setupapi-setupdiloaddeviceicon" data-raw-source="[&lt;strong&gt;SetupDiLoadDeviceIcon&lt;/strong&gt;](https://docs.microsoft.com/windows/desktop/api/setupapi/nf-setupapi-setupdiloaddeviceicon)"><strong>SetupDiLoadDeviceIcon</strong></a></p></td>
<td align="left"><p>加载指定的设备的设备图标。 （Windows Vista 和更高版本的 Windows）</p></td>
</tr>
<tr class="even">
<td align="left"><p><a href="https://docs.microsoft.com/windows/desktop/api/setupapi/nf-setupapi-setupdidestroyclassimagelist" data-raw-source="[&lt;strong&gt;SetupDiDestroyClassImageList&lt;/strong&gt;](https://docs.microsoft.com/windows/desktop/api/setupapi/nf-setupapi-setupdidestroyclassimagelist)"><strong>SetupDiDestroyClassImageList</strong></a></p></td>
<td align="left"><p>销毁类图像列表。</p></td>
</tr>
</tbody>
</table>

 

### <a href="" id="ddk-setupdi-device-interface-functions-dg"></a>设备接口函数

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td align="left"><p><a href="https://docs.microsoft.com/windows/desktop/api/setupapi/nf-setupapi-setupdicreatedeviceinterfacea" data-raw-source="[&lt;strong&gt;SetupDiCreateDeviceInterface&lt;/strong&gt;](https://docs.microsoft.com/windows/desktop/api/setupapi/nf-setupapi-setupdicreatedeviceinterfacea)"><strong>SetupDiCreateDeviceInterface</strong></a></p></td>
<td align="left"><p>注册设备的设备功能 （设备接口）。</p></td>
</tr>
<tr class="even">
<td align="left"><p><a href="https://docs.microsoft.com/windows/desktop/api/setupapi/nf-setupapi-setupdiopendeviceinterfacea" data-raw-source="[&lt;strong&gt;SetupDiOpenDeviceInterface&lt;/strong&gt;](https://docs.microsoft.com/windows/desktop/api/setupapi/nf-setupapi-setupdiopendeviceinterfacea)"><strong>SetupDiOpenDeviceInterface</strong></a></p></td>
<td align="left"><p>检索有关现有设备接口的信息，并将其添加到指定的设备信息设置。</p></td>
</tr>
<tr class="odd">
<td align="left"><p><a href="https://docs.microsoft.com/windows/desktop/api/setupapi/nf-setupapi-setupdigetdeviceinterfacealias" data-raw-source="[&lt;strong&gt;SetupDiGetDeviceInterfaceAlias&lt;/strong&gt;](https://docs.microsoft.com/windows/desktop/api/setupapi/nf-setupapi-setupdigetdeviceinterfacealias)"><strong>SetupDiGetDeviceInterfaceAlias</strong></a></p></td>
<td align="left"><p>返回指定的设备接口的别名。</p></td>
</tr>
<tr class="even">
<td align="left"><p><a href="https://docs.microsoft.com/windows/desktop/api/setupapi/nf-setupapi-setupdigetclassdevsexa" data-raw-source="[&lt;strong&gt;SetupDiGetClassDevs&lt;/strong&gt;](https://docs.microsoft.com/windows/desktop/api/setupapi/nf-setupapi-setupdigetclassdevsexa)"><strong>SetupDiGetClassDevs</strong></a></p></td>
<td align="left"><p>返回包含指定类的所有设备的设备信息集。</p></td>
</tr>
<tr class="odd">
<td align="left"><p><a href="https://docs.microsoft.com/windows/desktop/api/setupapi/nf-setupapi-setupdigetclassdevsexa" data-raw-source="[&lt;strong&gt;SetupDiGetClassDevsEx&lt;/strong&gt;](https://docs.microsoft.com/windows/desktop/api/setupapi/nf-setupapi-setupdigetclassdevsexa)"><strong>SetupDiGetClassDevsEx</strong></a></p></td>
<td align="left"><p>返回包含指定类的本地或远程计算机上的所有设备的设备信息集。</p></td>
</tr>
<tr class="even">
<td align="left"><p><a href="https://docs.microsoft.com/windows/desktop/api/setupapi/nf-setupapi-setupdienumdeviceinterfaces" data-raw-source="[&lt;strong&gt;SetupDiEnumDeviceInterfaces&lt;/strong&gt;](https://docs.microsoft.com/windows/desktop/api/setupapi/nf-setupapi-setupdienumdeviceinterfaces)"><strong>SetupDiEnumDeviceInterfaces</strong></a></p></td>
<td align="left"><p>返回设备信息设置的设备界面元素的上下文结构。 每次调用返回一个设备接口的信息。</p>
<p>可以重复调用该函数，以获取有关多个接口公开一个或多个设备的信息。</p></td>
</tr>
<tr class="odd">
<td align="left"><p><a href="https://docs.microsoft.com/windows/desktop/api/setupapi/nf-setupapi-setupdigetdeviceinterfacedetaila" data-raw-source="[&lt;strong&gt;SetupDiGetDeviceInterfaceDetail&lt;/strong&gt;](https://docs.microsoft.com/windows/desktop/api/setupapi/nf-setupapi-setupdigetdeviceinterfacedetaila)"><strong>SetupDiGetDeviceInterfaceDetail</strong></a></p></td>
<td align="left"><p>返回有关特定设备接口的详细信息。</p></td>
</tr>
<tr class="even">
<td align="left"><p><a href="https://docs.microsoft.com/windows/desktop/api/setupapi/nf-setupapi-setupdicreatedeviceinterfaceregkeya" data-raw-source="[&lt;strong&gt;SetupDiCreateDeviceInterfaceRegKey&lt;/strong&gt;](https://docs.microsoft.com/windows/desktop/api/setupapi/nf-setupapi-setupdicreatedeviceinterfaceregkeya)"><strong>SetupDiCreateDeviceInterfaceRegKey</strong></a></p></td>
<td align="left"><p>创建一个用于存储设备接口实例的信息的注册表子项，并返回的句柄的密钥。</p></td>
</tr>
<tr class="odd">
<td align="left"><p><a href="https://docs.microsoft.com/windows/desktop/api/setupapi/nf-setupapi-setupdiopendeviceinterfaceregkey" data-raw-source="[&lt;strong&gt;SetupDiOpenDeviceInterfaceRegKey&lt;/strong&gt;](https://docs.microsoft.com/windows/desktop/api/setupapi/nf-setupapi-setupdiopendeviceinterfaceregkey)"><strong>SetupDiOpenDeviceInterfaceRegKey</strong></a></p></td>
<td align="left"><p>将打开由应用程序和驱动程序来存储特定于设备接口实例，返回的句柄密钥的信息的注册表子项。</p></td>
</tr>
<tr class="even">
<td align="left"><p><a href="https://docs.microsoft.com/windows/desktop/api/setupapi/nf-setupapi-setupdideletedeviceinterfaceregkey" data-raw-source="[&lt;strong&gt;SetupDiDeleteDeviceInterfaceRegKey&lt;/strong&gt;](https://docs.microsoft.com/windows/desktop/api/setupapi/nf-setupapi-setupdideletedeviceinterfaceregkey)"><strong>SetupDiDeleteDeviceInterfaceRegKey</strong></a></p></td>
<td align="left"><p>删除应用程序和驱动程序中用于存储特定于设备接口实例的信息的注册表子项。</p></td>
</tr>
<tr class="odd">
<td align="left"><p><a href="https://docs.microsoft.com/windows/desktop/api/setupapi/nf-setupapi-setupdiinstalldeviceinterfaces" data-raw-source="[&lt;strong&gt;SetupDiInstallDeviceInterfaces&lt;/strong&gt;](https://docs.microsoft.com/windows/desktop/api/setupapi/nf-setupapi-setupdiinstalldeviceinterfaces)"><strong>SetupDiInstallDeviceInterfaces</strong></a></p></td>
<td align="left"><p>是 DIF_INSTALLINTERFACES 请求的默认处理程序。 它将安装中列出的接口<em>DDInstall</em>。<strong>接口</strong>设备 INF 文件部分。</p></td>
</tr>
<tr class="even">
<td align="left"><p><a href="https://docs.microsoft.com/windows/desktop/api/setupapi/nf-setupapi-setupdiremovedeviceinterface" data-raw-source="[&lt;strong&gt;SetupDiRemoveDeviceInterface&lt;/strong&gt;](https://docs.microsoft.com/windows/desktop/api/setupapi/nf-setupapi-setupdiremovedeviceinterface)"><strong>SetupDiRemoveDeviceInterface</strong></a></p></td>
<td align="left"><p>从系统中删除已注册的设备接口。</p></td>
</tr>
<tr class="odd">
<td align="left"><p><a href="https://docs.microsoft.com/windows/desktop/api/setupapi/nf-setupapi-setupdideletedeviceinterfacedata" data-raw-source="[&lt;strong&gt;SetupDiDeleteDeviceInterfaceData&lt;/strong&gt;](https://docs.microsoft.com/windows/desktop/api/setupapi/nf-setupapi-setupdideletedeviceinterfacedata)"><strong>SetupDiDeleteDeviceInterfaceData</strong></a></p></td>
<td align="left"><p>从设备信息组中删除设备接口。</p></td>
</tr>
<tr class="even">
<td align="left"><p><a href="https://docs.microsoft.com/windows/desktop/api/setupapi/nf-setupapi-setupdisetdeviceinterfacedefault" data-raw-source="[&lt;strong&gt;SetupDiSetDeviceInterfaceDefault&lt;/strong&gt;](https://docs.microsoft.com/windows/desktop/api/setupapi/nf-setupapi-setupdisetdeviceinterfacedefault)"><strong>SetupDiSetDeviceInterfaceDefault</strong></a></p></td>
<td align="left"><p>将指定的设备接口设置为设备类的默认接口。</p></td>
</tr>
<tr class="odd">
<td align="left"><p><a href="https://docs.microsoft.com/windows/desktop/api/setupapi/nf-setupapi-setupdiinstallclassexa" data-raw-source="[&lt;strong&gt;SetupDiInstallClassEx&lt;/strong&gt;](https://docs.microsoft.com/windows/desktop/api/setupapi/nf-setupapi-setupdiinstallclassexa)"><strong>SetupDiInstallClassEx</strong></a></p></td>
<td align="left"><p>安装类安装程序或接口类。</p></td>
</tr>
<tr class="even">
<td align="left"><p><a href="https://docs.microsoft.com/windows/desktop/api/setupapi/nf-setupapi-setupdiopenclassregkeyexa" data-raw-source="[&lt;strong&gt;SetupDiOpenClassRegKeyEx&lt;/strong&gt;](https://docs.microsoft.com/windows/desktop/api/setupapi/nf-setupapi-setupdiopenclassregkeyexa)"><strong>SetupDiOpenClassRegKeyEx</strong></a></p></td>
<td align="left"><p>此时将打开<a href="device-setup-classes.md" data-raw-source="[device setup class](device-setup-classes.md)">设备安装程序类</a>注册表项、 设备接口的类注册表项或类的特定子项。 此函数将打开指定的键在本地计算机或远程计算机上。</p></td>
</tr>
</tbody>
</table>

 

### <a href="" id="ddk-setupdi-device-property-functions-dg"></a>设备属性函数 (Windows Vista 及更高版本)

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td align="left"><p><a href="https://docs.microsoft.com/windows/desktop/api/setupapi/nf-setupapi-setupdigetclasspropertyw" data-raw-source="[&lt;strong&gt;SetupDiGetClassProperty&lt;/strong&gt;](https://docs.microsoft.com/windows/desktop/api/setupapi/nf-setupapi-setupdigetclasspropertyw)"><strong>SetupDiGetClassProperty</strong></a></p></td>
<td align="left"><p>检索为设备安装程序类或设备接口类设置的设备属性。</p></td>
</tr>
<tr class="even">
<td align="left"><p><a href="https://docs.microsoft.com/windows/desktop/api/setupapi/nf-setupapi-setupdigetclasspropertyexw" data-raw-source="[&lt;strong&gt;SetupDiGetClassPropertyEx&lt;/strong&gt;](https://docs.microsoft.com/windows/desktop/api/setupapi/nf-setupapi-setupdigetclasspropertyexw)"><strong>SetupDiGetClassPropertyEx</strong></a></p></td>
<td align="left"><p>检索设备安装程序类或在本地或远程计算机上的设备接口类的类属性。</p></td>
</tr>
<tr class="odd">
<td align="left"><p><a href="https://docs.microsoft.com/windows/desktop/api/setupapi/nf-setupapi-setupdigetclasspropertykeys" data-raw-source="[&lt;strong&gt;SetupDiGetClassPropertyKeys&lt;/strong&gt;](https://docs.microsoft.com/windows/desktop/api/setupapi/nf-setupapi-setupdigetclasspropertykeys)"><strong>SetupDiGetClassPropertyKeys</strong></a></p></td>
<td align="left"><p>检索表示为设备安装程序类或设备接口类设置的设备属性的设备属性键的数组。</p></td>
</tr>
<tr class="even">
<td align="left"><p><a href="https://docs.microsoft.com/windows/desktop/api/setupapi/nf-setupapi-setupdigetclasspropertykeysexw" data-raw-source="[&lt;strong&gt;SetupDiGetClassPropertyKeysEx&lt;/strong&gt;](https://docs.microsoft.com/windows/desktop/api/setupapi/nf-setupapi-setupdigetclasspropertykeysexw)"><strong>SetupDiGetClassPropertyKeysEx</strong></a></p></td>
<td align="left"><p>检索表示为设备安装程序类或设备接口类上本地或远程计算机设置的设备属性的设备属性键的数组。</p></td>
</tr>
<tr class="odd">
<td align="left"><p><a href="https://docs.microsoft.com/windows/desktop/api/setupapi/nf-setupapi-setupdigetdeviceinterfacepropertyw" data-raw-source="[&lt;strong&gt;SetupDiGetDeviceInterfaceProperty&lt;/strong&gt;](https://docs.microsoft.com/windows/desktop/api/setupapi/nf-setupapi-setupdigetdeviceinterfacepropertyw)"><strong>SetupDiGetDeviceInterfaceProperty</strong></a></p></td>
<td align="left"><p>检索为设备接口设置的设备属性。</p></td>
</tr>
<tr class="even">
<td align="left"><p><a href="https://docs.microsoft.com/windows/desktop/api/setupapi/nf-setupapi-setupdigetdeviceinterfacepropertykeys" data-raw-source="[&lt;strong&gt;SetupDiGetDeviceInterfacePropertyKeys&lt;/strong&gt;](https://docs.microsoft.com/windows/desktop/api/setupapi/nf-setupapi-setupdigetdeviceinterfacepropertykeys)"><strong>SetupDiGetDeviceInterfacePropertyKeys</strong></a></p></td>
<td align="left"><p>检索表示为设备接口设置的设备属性的设备属性键的数组。</p></td>
</tr>
<tr class="odd">
<td align="left"><p><a href="https://docs.microsoft.com/windows/desktop/api/setupapi/nf-setupapi-setupdigetdevicepropertyw" data-raw-source="[&lt;strong&gt;SetupDiGetDeviceProperty&lt;/strong&gt;](https://docs.microsoft.com/windows/desktop/api/setupapi/nf-setupapi-setupdigetdevicepropertyw)"><strong>SetupDiGetDeviceProperty</strong></a></p></td>
<td align="left"><p>检索设备实例属性。</p></td>
</tr>
<tr class="even">
<td align="left"><p><a href="https://docs.microsoft.com/windows/desktop/api/setupapi/nf-setupapi-setupdigetdevicepropertykeys" data-raw-source="[&lt;strong&gt;SetupDiGetDevicePropertyKeys&lt;/strong&gt;](https://docs.microsoft.com/windows/desktop/api/setupapi/nf-setupapi-setupdigetdevicepropertykeys)"><strong>SetupDiGetDevicePropertyKeys</strong></a></p></td>
<td align="left"><p>检索表示为设备实例设置的设备属性的设备属性键的数组。</p></td>
</tr>
<tr class="odd">
<td align="left"><p><a href="https://docs.microsoft.com/windows/desktop/api/setupapi/nf-setupapi-setupdisetclasspropertyw" data-raw-source="[&lt;strong&gt;SetupDiSetClassProperty&lt;/strong&gt;](https://docs.microsoft.com/windows/desktop/api/setupapi/nf-setupapi-setupdisetclasspropertyw)"><strong>SetupDiSetClassProperty</strong></a></p></td>
<td align="left"><p>设置设备安装程序类或设备接口类的类属性。</p></td>
</tr>
<tr class="even">
<td align="left"><p><a href="https://docs.microsoft.com/windows/desktop/api/setupapi/nf-setupapi-setupdisetclasspropertyexw" data-raw-source="[&lt;strong&gt;SetupDiSetClassPropertyEx&lt;/strong&gt;](https://docs.microsoft.com/windows/desktop/api/setupapi/nf-setupapi-setupdisetclasspropertyexw)"><strong>SetupDiSetClassPropertyEx</strong></a></p></td>
<td align="left"><p>在本地或远程计算机上设置设备安装程序类或设备接口类的设备的属性。</p></td>
</tr>
<tr class="odd">
<td align="left"><p><a href="https://docs.microsoft.com/windows/desktop/api/setupapi/nf-setupapi-setupdisetdeviceinterfacepropertyw" data-raw-source="[&lt;strong&gt;SetupDiSetDeviceInterfaceProperty&lt;/strong&gt;](https://docs.microsoft.com/windows/desktop/api/setupapi/nf-setupapi-setupdisetdeviceinterfacepropertyw)"><strong>SetupDiSetDeviceInterfaceProperty</strong></a></p></td>
<td align="left"><p>设置设备接口的设备属性。</p></td>
</tr>
<tr class="even">
<td align="left"><p><a href="https://docs.microsoft.com/windows/desktop/api/setupapi/nf-setupapi-setupdisetdevicepropertyw" data-raw-source="[&lt;strong&gt;SetupDiSetDeviceProperty&lt;/strong&gt;](https://docs.microsoft.com/windows/desktop/api/setupapi/nf-setupapi-setupdisetdevicepropertyw)"><strong>SetupDiSetDeviceProperty</strong></a></p></td>
<td align="left"><p>设置设备实例属性。</p></td>
</tr>
</tbody>
</table>

 

### <a href="" id="ddk-setupdi-registry-functions-dg"></a>注册表函数

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td align="left"><p><a href="https://docs.microsoft.com/windows/desktop/api/setupapi/nf-setupapi-setupdicreatedevregkeya" data-raw-source="[&lt;strong&gt;SetupDiCreateDevRegKey&lt;/strong&gt;](https://docs.microsoft.com/windows/desktop/api/setupapi/nf-setupapi-setupdicreatedevregkeya)"><strong>SetupDiCreateDevRegKey</strong></a></p></td>
<td align="left"><p>创建特定于设备的配置信息的注册表存储密钥，并返回的句柄的密钥。</p></td>
</tr>
<tr class="even">
<td align="left"><p><a href="https://docs.microsoft.com/windows/desktop/api/setupapi/nf-setupapi-setupdiopendevregkey" data-raw-source="[&lt;strong&gt;SetupDiOpenDevRegKey&lt;/strong&gt;](https://docs.microsoft.com/windows/desktop/api/setupapi/nf-setupapi-setupdiopendevregkey)"><strong>SetupDiOpenDevRegKey</strong></a></p></td>
<td align="left"><p>打开注册表存储项特定于设备的配置信息并返回一个句柄的键。</p></td>
</tr>
<tr class="odd">
<td align="left"><p><a href="https://docs.microsoft.com/windows/desktop/api/setupapi/nf-setupapi-setupdideletedevregkey" data-raw-source="[&lt;strong&gt;SetupDiDeleteDevRegKey&lt;/strong&gt;](https://docs.microsoft.com/windows/desktop/api/setupapi/nf-setupapi-setupdideletedevregkey)"><strong>SetupDiDeleteDevRegKey</strong></a></p></td>
<td align="left"><p>删除与设备信息元素相关联的指定的用户可访问的注册表密钥。</p></td>
</tr>
<tr class="even">
<td align="left"><p><a href="https://docs.microsoft.com/windows/desktop/api/setupapi/nf-setupapi-setupdiopenclassregkey" data-raw-source="[&lt;strong&gt;SetupDiOpenClassRegKey&lt;/strong&gt;](https://docs.microsoft.com/windows/desktop/api/setupapi/nf-setupapi-setupdiopenclassregkey)"><strong>SetupDiOpenClassRegKey</strong></a></p></td>
<td align="left"><p>打开安装程序类注册表项或类的特定子项。</p></td>
</tr>
<tr class="odd">
<td align="left"><p><a href="https://docs.microsoft.com/windows/desktop/api/setupapi/nf-setupapi-setupdiopenclassregkeyexa" data-raw-source="[&lt;strong&gt;SetupDiOpenClassRegKeyEx&lt;/strong&gt;](https://docs.microsoft.com/windows/desktop/api/setupapi/nf-setupapi-setupdiopenclassregkeyexa)"><strong>SetupDiOpenClassRegKeyEx</strong></a></p></td>
<td align="left"><p>打开设备安装程序类注册表项、 设备接口的类注册表项或类的特定子项。</p>
<p>此函数将打开指定的键在本地计算机或远程计算机上。</p></td>
</tr>
<tr class="even">
<td align="left"><p><a href="https://docs.microsoft.com/windows/desktop/api/setupapi/nf-setupapi-setupdicreatedeviceinterfaceregkeya" data-raw-source="[&lt;strong&gt;SetupDiCreateDeviceInterfaceRegKey&lt;/strong&gt;](https://docs.microsoft.com/windows/desktop/api/setupapi/nf-setupapi-setupdicreatedeviceinterfaceregkeya)"><strong>SetupDiCreateDeviceInterfaceRegKey</strong></a></p></td>
<td align="left"><p>创建一个用于存储设备接口实例的信息的非易失性的注册表子项，并返回的句柄密钥。</p></td>
</tr>
<tr class="odd">
<td align="left"><p><a href="https://docs.microsoft.com/windows/desktop/api/setupapi/nf-setupapi-setupdiopendeviceinterfaceregkey" data-raw-source="[&lt;strong&gt;SetupDiOpenDeviceInterfaceRegKey&lt;/strong&gt;](https://docs.microsoft.com/windows/desktop/api/setupapi/nf-setupapi-setupdiopendeviceinterfaceregkey)"><strong>SetupDiOpenDeviceInterfaceRegKey</strong></a></p></td>
<td align="left"><p>将打开由应用程序和驱动程序来存储特定于设备接口实例，返回的句柄密钥的信息的注册表子项。</p></td>
</tr>
<tr class="even">
<td align="left"><p><a href="https://docs.microsoft.com/windows/desktop/api/setupapi/nf-setupapi-setupdideletedeviceinterfaceregkey" data-raw-source="[&lt;strong&gt;SetupDiDeleteDeviceInterfaceRegKey&lt;/strong&gt;](https://docs.microsoft.com/windows/desktop/api/setupapi/nf-setupapi-setupdideletedeviceinterfaceregkey)"><strong>SetupDiDeleteDeviceInterfaceRegKey</strong></a></p></td>
<td align="left"><p>删除应用程序和驱动程序中用于存储特定于设备接口实例的信息的注册表子项。</p></td>
</tr>
<tr class="odd">
<td align="left"><p><a href="https://docs.microsoft.com/windows/desktop/api/setupapi/nf-setupapi-setupdisetdeviceregistrypropertya" data-raw-source="[&lt;strong&gt;SetupDiSetDeviceRegistryProperty&lt;/strong&gt;](https://docs.microsoft.com/windows/desktop/api/setupapi/nf-setupapi-setupdisetdeviceregistrypropertya)"><strong>SetupDiSetDeviceRegistryProperty</strong></a></p></td>
<td align="left"><p>设置指定即插即用设备属性。</p></td>
</tr>
<tr class="even">
<td align="left"><p><a href="https://docs.microsoft.com/windows/desktop/api/setupapi/nf-setupapi-setupdigetdeviceregistrypropertya" data-raw-source="[&lt;strong&gt;SetupDiGetDeviceRegistryProperty&lt;/strong&gt;](https://docs.microsoft.com/windows/desktop/api/setupapi/nf-setupapi-setupdigetdeviceregistrypropertya)"><strong>SetupDiGetDeviceRegistryProperty</strong></a></p></td>
<td align="left"><p>检索指定即插即用设备属性。</p></td>
</tr>
<tr class="odd">
<td align="left"><p><a href="https://docs.microsoft.com/windows/desktop/api/setupapi/nf-setupapi-setupdigetclassregistrypropertya" data-raw-source="[&lt;strong&gt;SetupDiGetClassRegistryProperty&lt;/strong&gt;](https://docs.microsoft.com/windows/desktop/api/setupapi/nf-setupapi-setupdigetclassregistrypropertya)"><strong>SetupDiGetClassRegistryProperty</strong></a></p></td>
<td align="left"><p>从注册表检索指定的设备类属性。</p></td>
</tr>
<tr class="even">
<td align="left"><p><a href="https://docs.microsoft.com/windows/desktop/api/setupapi/nf-setupapi-setupdisetclassregistrypropertya" data-raw-source="[&lt;strong&gt;SetupDiSetClassRegistryProperty&lt;/strong&gt;](https://docs.microsoft.com/windows/desktop/api/setupapi/nf-setupapi-setupdisetclassregistrypropertya)"><strong>SetupDiSetClassRegistryProperty</strong></a></p></td>
<td align="left"><p>在注册表中设置指定的设备类属性。</p></td>
</tr>
</tbody>
</table>

 

### <a href="" id="ddk-other-setupdi-functions-dg"></a>其他函数

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td align="left"><p><a href="https://docs.microsoft.com/windows/desktop/api/setupapi/nf-setupapi-setupdigetactualmodelssectiona" data-raw-source="[&lt;strong&gt;SetupDiGetActualModelsSection&lt;/strong&gt;](https://docs.microsoft.com/windows/desktop/api/setupapi/nf-setupapi-setupdigetactualmodelssectiona)"><strong>SetupDiGetActualModelsSection</strong></a></p></td>
<td align="left"><p>检索相应的修饰<a href="inf-models-section.md" data-raw-source="[&lt;strong&gt;INF Models section&lt;/strong&gt;](inf-models-section.md)"> <strong>INF 模型部分</strong></a>从设备 INF 文件安装设备时要使用。</p></td>
</tr>
<tr class="even">
<td align="left"><p><a href="https://docs.microsoft.com/windows/desktop/api/setupapi/nf-setupapi-setupdigetactualsectiontoinstalla" data-raw-source="[&lt;strong&gt;SetupDiGetActualSectionToInstall&lt;/strong&gt;](https://docs.microsoft.com/windows/desktop/api/setupapi/nf-setupapi-setupdigetactualsectiontoinstalla)"><strong>SetupDiGetActualSectionToInstall</strong></a></p></td>
<td align="left"><p>检索相应<em>DDInstall</em>从设备 INF 文件安装设备时要使用的部分。</p></td>
</tr>
<tr class="odd">
<td align="left"><p><a href="https://docs.microsoft.com/windows/desktop/api/setupapi/nf-setupapi-setupdigetactualsectiontoinstallexa" data-raw-source="[&lt;strong&gt;SetupDiGetActualSectionToInstallEx&lt;/strong&gt;](https://docs.microsoft.com/windows/desktop/api/setupapi/nf-setupapi-setupdigetactualsectiontoinstallexa)"><strong>SetupDiGetActualSectionToInstallEx</strong></a></p></td>
<td align="left"><p>检索名称 INF <em>DDInstall</em>安装指定的操作系统和处理器体系结构的设备的部分。</p></td>
</tr>
<tr class="even">
<td align="left"><p><a href="https://docs.microsoft.com/windows/desktop/api/setupapi/nf-setupapi-setupdigethwprofilefriendlynamea" data-raw-source="[&lt;strong&gt;SetupDiGetHwProfileFriendlyName&lt;/strong&gt;](https://docs.microsoft.com/windows/desktop/api/setupapi/nf-setupapi-setupdigethwprofilefriendlynamea)"><strong>SetupDiGetHwProfileFriendlyName</strong></a></p></td>
<td align="left"><p>检索硬件配置文件 id。 与关联的友好名称</p></td>
</tr>
<tr class="odd">
<td align="left"><p><a href="https://docs.microsoft.com/windows/desktop/api/setupapi/nf-setupapi-setupdigethwprofilefriendlynameexa" data-raw-source="[&lt;strong&gt;SetupDiGetHwProfileFriendlyNameEx&lt;/strong&gt;](https://docs.microsoft.com/windows/desktop/api/setupapi/nf-setupapi-setupdigethwprofilefriendlynameexa)"><strong>SetupDiGetHwProfileFriendlyNameEx</strong></a></p></td>
<td align="left"><p>检索与本地或远程计算机上的硬件配置文件 ID 关联的友好名称。</p></td>
</tr>
<tr class="even">
<td align="left"><p><a href="https://docs.microsoft.com/windows/desktop/api/setupapi/nf-setupapi-setupdigethwprofilelist" data-raw-source="[&lt;strong&gt;SetupDiGetHwProfileList&lt;/strong&gt;](https://docs.microsoft.com/windows/desktop/api/setupapi/nf-setupapi-setupdigethwprofilelist)"><strong>SetupDiGetHwProfileList</strong></a></p></td>
<td align="left"><p>检索所有当前定义的硬件配置文件 Id 的列表。</p></td>
</tr>
<tr class="odd">
<td align="left"><p><a href="https://docs.microsoft.com/windows/desktop/api/setupapi/nf-setupapi-setupdigethwprofilelistexa" data-raw-source="[&lt;strong&gt;SetupDiGetHwProfileListEx&lt;/strong&gt;](https://docs.microsoft.com/windows/desktop/api/setupapi/nf-setupapi-setupdigethwprofilelistexa)"><strong>SetupDiGetHwProfileListEx</strong></a></p></td>
<td align="left"><p>检索本地或远程计算机上的所有当前定义的硬件配置文件 Id 的列表。</p></td>
</tr>
<tr class="even">
<td align="left"><p><a href="https://docs.microsoft.com/windows/desktop/api/setupapi/nf-setupapi-setupdirestartdevices" data-raw-source="[&lt;strong&gt;SetupDiRestartDevices&lt;/strong&gt;](https://docs.microsoft.com/windows/desktop/api/setupapi/nf-setupapi-setupdirestartdevices)"><strong>SetupDiRestartDevices</strong></a></p></td>
<td align="left"><p>重新启动指定的设备，或如有必要，将启动由同一个函数和筛选器驱动程序为指定的设备操作的所有设备。</p></td>
</tr>
</tbody>
</table>

 

 

 





