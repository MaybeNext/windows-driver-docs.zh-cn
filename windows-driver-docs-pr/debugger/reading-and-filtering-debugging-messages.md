---
title: 读取和筛选调试消息
description: 读取和筛选调试消息
ms.assetid: 785469d2-30b8-4f73-b397-80bf89ed20ea
keywords:
- 读取和筛选调试消息
- 调试消息，读取和筛选
ms.date: 05/23/2017
ms.localizationpriority: medium
ms.openlocfilehash: 9f2c96f433ada8feb655e06b4f5a5089eded1bd4
ms.sourcegitcommit: d30691c8276f7dddd3f8333e84744ddeea1e1020
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/19/2019
ms.locfileid: "75209801"
---
# <a name="reading-and-filtering-debugging-messages"></a>读取和筛选调试消息


## <span id="ddk_reading_and_filtering_debugging_messages_dbg"></span><span id="DDK_READING_AND_FILTERING_DEBUGGING_MESSAGES_DBG"></span>


内核模式代码可以使用**DbgPrintEx**和**KdPrintEx**例程将消息发送到仅在某些情况下传输的内核调试器。 这允许你筛选出你不感兴趣的消息。

**请注意**   在 windows Server 2003 和更早版本的 windows 中， **DbgPrint**和**KdPrint**无条件地将消息发送到内核调试器。 在 Windows Vista 和更高版本的 Windows 中，这些例程有条件地发送消息，例如**DbgPrintEx**和**KdPrintEx**。 无论使用哪种 Windows 版本，建议使用**DbgPrintEx**和**KdPrintEx**，因为它们允许您控制将消息发送到的条件。

 

有关这些例程的完整文档，请参阅 Windows 驱动程序工具包。

基本过程如下所示：

**筛选调试消息**

1.  对于要发送到调试器的每个消息，请在驱动程序的代码中使用函数**DbgPrintEx**或**KdPrintEx** 。 将相应的组件名称传递给*组件类参数，* 并向*Level*参数传递一个值，用于反映此消息的严重性或性质。 消息本身传递到带有**printf**的*格式*和*参数*参数。

2.  设置相应的 "*组件筛选器掩码*" 的值。 每个组件都有不同的掩码;掩码值指示将显示该组件的哪些消息。 可以使用注册表编辑器或使用内核调试器在内存中设置组件筛选器掩码。

3.  将内核调试器附加到计算机。 每次你的驱动程序将消息传递到**DbgPrintEx**或**KdPrintEx**时，传递*给组件器和**级别*的值将与相应的组件筛选器掩码的值进行比较。 如果这些值满足特定条件，则会将消息发送到内核调试器并显示。 否则，将不会发送任何消息。

完整的详细信息如下。 此页面上到**DbgPrintEx**的所有引用同样适用于**KdPrintEx**。

### <a name="span-ididentifying-the-component-namespanspan-ididentifying_the_component_namespanidentifying-the-component-name"></a><span id="identifying-the-component-name"></span><span id="IDENTIFYING_THE_COMPONENT_NAME"></span>标识组件名称

每个组件都有单独的筛选器掩码。 这允许调试器单独配置每个组件的筛选器。

每个组件都以不同的方式引用，具体取决于上下文。 在**DbgPrintEx***的组件名称参数中*，组件名称以 "DPFLTR\_" 作为前缀，并带有后缀 "\_ID"。 在注册表中，组件筛选器掩码与组件本身具有相同的名称。 在调试器中，组件筛选器掩码以 "Kd\_" 作为前缀，并带有后缀 "\_掩码"。

Microsoft Windows 驱动程序工具包（WDK）标头 ntddk 中的所有组件名称（DPFLTR\_*XXXX*\_ID 格式）的完整列表以及 Windows SDK 标头 ntrtl。 其中的大多数组件名称都是为 Windows 和 Microsoft 编写的驱动程序保留的。

为独立硬件供应商保留了六个组件名称。 若要避免使用 Windows 组件的输出混合使用驱动程序的输出，应使用以下组件名称之一：

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">组件名称</th>
<th align="left">驱动程序类型</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p><strong>IHVVIDEO</strong></p></td>
<td align="left"><p>视频驱动程序</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>IHVAUDIO</strong></p></td>
<td align="left"><p>音频驱动程序</p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>IHVNETWORK</strong></p></td>
<td align="left"><p>网络驱动程序</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>IHVSTREAMING</strong></p></td>
<td align="left"><p>内核流式处理驱动程序</p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>IHVBUS</strong></p></td>
<td align="left"><p>总线驱动程序</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>IHVDRIVER</strong></p></td>
<td align="left"><p>任何其他类型的驱动程序</p></td>
</tr>
</tbody>
</table>

 

例如，如果你正在编写视频驱动程序，你将使用 DPFLTR\_IHVVIDEO\_ID 作为**DbgPrintEx**的项*id 参数，* 使用注册表中的值名称**IHVVIDEO** ，并在调试器中引用**Kd\_IHVVIDEO\_掩码**。

在 Windows Vista 和更高版本的 Windows 中， **DbgPrint**和**KdPrint**发送的所有消息都与**默认**组件相关联。

### <a name="span-idchoosing_the_correct_levelspanspan-idchoosing_the_correct_levelspanchoosing-the-correct-level"></a><span id="choosing_the_correct_level"></span><span id="CHOOSING_THE_CORRECT_LEVEL"></span>选择正确的级别

**DbgPrintEx**例程的*Level*参数的类型为 DWORD。 它用于确定*重要性位域*。 *Level*参数和此位字段之间的连接取决于*级别*的大小：

-   如果*Level*等于0到31（含）之间的数字，则将其解释为移位。 "重要性位域" 设置为值 1 &lt;&lt;*级别*。 因此，为*级别*选择0到31之间的值会导致位域中只有一个位集。 如果*level*为0，则位域等效于 0x00000001; 如果*level*为31，则位域等效于0x80000000。

-   如果*Level*是介于32和0xffffffff 之间的数字，则将重要性位域设置为*Level*本身的值。

因此，如果您希望将位域设置为0x00004000，则可以指定*Level*作为0x00004000，或只指定为14。 请注意，此系统不能实现某些位字段值-包括完全为零的位域。

以下常量可用于设置*级别*的值。 它们在 Microsoft Windows 驱动程序工具包（WDK）标头 ntddk 和 Windows SDK 标头 ntrtl 中定义：

```cpp
#define   DPFLTR_ERROR_LEVEL     0
#define   DPFLTR_WARNING_LEVEL   1
#define   DPFLTR_TRACE_LEVEL     2
#define   DPFLTR_INFO_LEVEL      3
#define   DPFLTR_MASK    0x8000000
```

使用*Level*参数的一种简单方法是始终使用0到31之间的值--使用位0，1，2，3，使用 DPFLTR 指定的含义\_*XXXX*\_Level，并使用其他位表示所选的任何内容。

使用*Level*参数的另一种简单方法是始终使用显式位域。 如果选择此方法，你可能希望或值 DPFLTR\_掩码与位域相同;这可以确保不会意外使用小于32的值。

若要使您的驱动程序与 Windows 使用消息级别的方式兼容，只应在出现严重错误时设置重要性位域的最小位（0x1）。 如果使用的*级别*值小于32，则此值对应于 DPFLTR\_错误\_级别。 如果设置了此位，则每当有人将内核调试器附加到运行你的驱动程序的计算机时，你将会看到你的消息。

应在适当的情况下使用警告、跟踪和信息级别。 其他位可以自由地用于您认为有用的任何目的。 这使您可以有选择地查看或隐藏各种消息类型。

在 Windows Vista 和更高版本的 Windows 中， **DbgPrint**和**KdPrint**发送的所有消息的行为类似于**DbgPrintEx**和**KdPrintEx**消息，其*级别*等于 DPFLTR\_INFO\_级别。 换句话说，这些消息的重要性位域集的第三位。

### <a name="span-idsetting-the-component-filter-maskspanspan-idsetting_the_component_filter_maskspansetting-the-component-filter-mask"></a><span id="setting-the-component-filter-mask"></span><span id="SETTING_THE_COMPONENT_FILTER_MASK"></span>设置组件筛选器掩码

可以通过两种方法设置组件筛选器掩码：

- 可以在注册表项 HKEY 中访问组件筛选器掩码， **\_本地\_计算机\\系统\\CurrentControlSet\\控制\\会话管理器\\调试打印筛选器**。 使用注册表编辑器创建或打开此项。 在此项下，创建一个值，其中包含所需组件的名称（以大写形式）。 将其设置为要用作组件筛选器掩码的 DWORD 值。

- 如果内核调试程序处于活动状态，则它可以通过取消引用符号 Kd 中存储的地址来访问组件筛选器掩码值**\_** <em>xxxx</em> **\_掩码**，其中*XXXX*是所需的组件名称。 可以使用**dd （显示 dword）** 命令在 WINDBG 或 KD 中显示此掩码的值，也可以使用**ED （enter dword）** 命令输入新的组件筛选器掩码。 如果存在符号多义性的危险，你可能希望将此符号指定为**nt！Kd\_** <em>XXXX</em> **\_掩码**。

在启动过程中，存储在注册表中的筛选器掩码会生效。 调试器创建的筛选器掩码会立即生效，并且在重新启动 Windows 之前持久保存。 注册表中设置的值可以由调试器重写，但如果重新启动系统，则组件筛选器掩码将返回到注册表中指定的值。

还存在一个称为**WIN2000**的系统范围掩码。 默认情况下，这等于0x1，不过，它可以通过注册表或调试器（与所有其他组件）更改。 执行筛选时，每个组件筛选器掩码首先与**WIN2000**掩码运算。 具体而言，这意味着其掩码从未指定为0x1 的组件默认为0x1。

### <a name="span-idcriteria-for-displaying_the_messagespanspan-idcriteria_for_displaying_the_messagespancriteria-for-displaying-the-message"></a><span id="criteria-for-displaying_the_message"></span><span id="CRITERIA_FOR_DISPLAYING_THE_MESSAGE"></span>用于显示消息的条件

当在内核模式代码中调用**DbgPrintEx**时，Windows 会将由*Level*指定的消息重要性位域与组件*id*指定的组件的筛选器掩码进行比较。

**请注意**   请注意，*当 level*参数介于0和31之间时，重要性位域等于 1 &lt;&lt;*级别*，但当*level*参数为32或更高级别时，"重要性位" 字段只相当于*Level*。

 

Windows 对重要性位域和组件筛选器掩码执行 AND 运算。 如果结果为非零值，则将消息发送到调试器。

### <a name="span-idexamplespanspan-idexamplespanexample"></a><span id="example"></span><span id="EXAMPLE"></span>实例

下面是一个示例。

假设在上次启动之前，在 "**调试" 打印筛选器**键中创建了以下值：

-   **IHVVIDEO**，其值等于 DWORD 0x2

-   **IHVBUS**，等于 DWORD 0x7FF

现在，在内核调试器中发出以下命令：

```dbgcmd
kd> ed Kd_IHVVIDEO_Mask 0x8 
kd> ed Kd_IHVAUDIO_Mask 0x7 
```

此时， **IHVVIDEO**组件的筛选器掩码为0X8， **IHVAUDIO**组件的筛选器掩码为0x7， **IHVBUS**组件的筛选器掩码为0x7FF。

但是，由于这些掩码会自动与**WIN2000**系统范围掩码（通常等于0X1）运算，因此**IHVVIDEO**掩码有效地等于0x9。 事实上，根本没有设置筛选器掩码的组件（例如， **IHVSTREAMING**或**默认值**）的筛选器掩码为0x1。

现在假设以下函数调用发生在各种驱动程序中：

```cpp
DbgPrintEx( DPFLTR_IHVVIDEO_ID,  DPFLTR_INFO_LEVEL,   "First message.\n");
DbgPrintEx( DPFLTR_IHVAUDIO_ID,  7,                   "Second message.\n");
DbgPrintEx( DPFLTR_IHVBUS_ID,    DPFLTR_MASK | 0x10,  "Third message.\n");
DbgPrint( "Fourth message.\n");
```

第一条消息的*级别*参数等于 DPFLTR\_INFO\_Level，后者为3。 由于此小于32，因此将其视为一个移位，并产生一个重要性位域0x8。 然后，此值将与 IHVVIDEO 的有效组件筛选器掩码 and，提供非零结果。 因此，第一条消息会传输到调试器。

第二条消息的*级别*参数等于7。 同样，这被视为一个移位，这会产生一个重要性位字段0x80。 然后，使用0x7 的**IHVAUDIO**组件筛选器掩码 and，结果为零。 因此不会传输第二条消息。

第三条消息的*级别*参数等于 DPFLTR\_掩码 |0x10. 此值大于31，因此，将 "重要性位域" 设置为等于 "*级别*" 的值（即0x80000010）。 然后，使用0x7FF 的**IHVBUS**组件筛选器掩码 and，提供一个非零结果。 因此，第三条消息会传输到调试器。

第四条消息传递到**DbgPrint**而不是**DbgPrintEx**。 在 Windows Server 2003 和更早版本的 Windows 中，将始终传输传递到此例程的消息。 在 Windows Vista 和更高版本的 Windows 中，传递到此例程的消息始终被赋予默认筛选器。 重要性位域等于 1 &lt;&lt; DPFLTR\_信息\_级别为0x00000008。 此例程的组件为**默认值**。 由于尚未设置**默认**的组件筛选器掩码，因此它的值为0x1。 如果这与重要性位域 And，则结果为零。 因此，第四条消息不会传输。

### <a name="span-idthe-dbgprint-bufferspanspan-idthe_dbgprint_bufferspanthe-dbgprint-buffer"></a><span id="the-dbgprint-buffer"></span><span id="THE_DBGPRINT_BUFFER"></span>DbgPrint 缓冲区

当**DbgPrint**、 **DbgPrintEx**、 **KdPrint**或**KdPrintEx**向调试器传输消息时，将带格式的字符串发送到*DbgPrint 缓冲区*。 在大多数情况下，此缓冲区的内容会立即显示在调试器命令窗口中。 此显示可以通过使用全局标志实用程序（gflags）的**Buffer DbgPrint Output**选项来禁用。 此显示不会在本地内核调试期间自动出现。

在本地内核调试过程中，以及此显示已禁用的任何其他时间，只能使用[**！ DbgPrint**](-dbgprint.md)扩展命令查看 DbgPrint 缓冲区的内容。

对**DbgPrint**、 **DbgPrintEx**、 **KdPrint**或**KdPrintEx**的任何单个调用将仅传输512个字节的信息。 超出此长度的任何输出都将丢失。 DbgPrint 缓冲区本身最多可以在 Windows 的免费版本中保存 4 KB 的数据。 在 Windows Server 2003 及更高版本的 Windows 上，可以使用 KDbgCtrl 工具来更改 DbgPrint 缓冲区的大小。 有关详细信息，请参阅[使用 KDbgCtrl](using-kdbgctrl.md) 。

如果消息因其*组件 id*和*级别*值而被筛选掉，则不会通过调试连接进行传输。 因此，无法在调试器中显示此消息。
