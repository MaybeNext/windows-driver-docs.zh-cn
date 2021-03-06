---
title: C （Windows 调试器术语表）
description: 词汇表页-C
ms.asseti: 295b05a3-e27f-4761-a562-7e87e25bfd3b
ms.date: 12/17/2019
ms.localizationpriority: medium
ms.openlocfilehash: 59a373ee3195d2717d7b6577894a99104355693e
ms.sourcegitcommit: d30691c8276f7dddd3f8333e84744ddeea1e1020
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/19/2019
ms.locfileid: "75209453"
---
# <a name="c"></a>C


<span id="c___expression"></span><span id="C___EXPRESSION"></span>**C++表达式**  
可以通过C++表达式计算器计算的表达式。

<span id="c_call_stack"></span><span id="C_CALL_STACK"></span>**C 调用堆栈**  
请参阅调用堆栈。

<span id="call_stack"></span><span id="CALL_STACK"></span>**调用堆栈**  
每个线程的堆栈帧集，其中包含表示线程所做的函数调用。 每次调用函数时，新的堆栈帧就会被推送到堆栈的顶部。 当该函数返回时，堆栈帧将从堆栈中弹出。

有时也称为或。

<span id="callback_object"></span><span id="CALLBACK_OBJECT"></span>**回调对象**  
请参阅事件回调、输入回调和输出回调。

<span id="checked_build"></span><span id="CHECKED_BUILD"></span>**已检查生成**  

不再为 Windows 提供已检查的生成。 使用驱动程序验证程序和 GFlags 等工具检查驱动程序代码。

选中版本包含了额外的错误检查、参数验证和不能用于免费生成的调试信息。

尽管该检查生成提供额外的保护，但它消耗的内存和磁盘空间超出了免费版本。 系统和驱动程序性能较慢，因为附加的代码路径由于诊断消息的参数检查和输出而执行，并使用内核函数的一些替代实现。

Windows 的检查内部版本不应与内置于 Windows 驱动程序工具包（WDK）的某个已检查版本环境中的驱动程序混淆。

<span id="child_symbol"></span><span id="CHILD_SYMBOL"></span>**子符号**  
包含在另一个符号中的符号。 例如，结构中成员的符号是该结构的符号的子元素。

<span id="client"></span><span id="CLIENT"></span>**机**  
请参阅客户端对象。

<span id="client_object"></span><span id="CLIENT_OBJECT"></span>**客户端对象**  
客户端对象用于与调试器引擎交互。 它保存每个客户端的状态，并在调试器引擎 API 中提供顶层接口的实现。

<span id="client_thread"></span><span id="CLIENT_THREAD"></span>**客户端线程**  
在其中创建客户端对象的线程。 通常，只能从此线程调用客户端的方法。 调试器引擎使用此线程对注册到客户端的回调对象进行所有调用。

<span id="code_breakpoint"></span><span id="CODE_BREAKPOINT"></span>**代码断点**  
请参阅软件断点。

<span id="crash_dump_file"></span><span id="CRASH_DUMP_FILE"></span>**故障转储文件**  
一个文件，其中包含特定内存区域的快照以及与应用程序或操作系统相关的其他数据。 崩溃转储文件可以存储，然后用于稍后调试应用程序或操作系统。

当应用程序崩溃时，Windows 可能会创建用户模式故障转储文件，并且当 Windows 自身崩溃时，特殊 Windows 例程可以创建内核模式故障转储文件。 有几种不同类型的故障转储文件。

<span id="current_process"></span><span id="CURRENT_PROCESS"></span>**当前进程**  
调试器引擎当前正在控制的进程。 事件发生时，当前进程设置为事件进程。

<span id="current_target"></span><span id="CURRENT_TARGET"></span>**当前目标**  
调试器引擎当前正在控制的目标。 事件发生时，当前目标设置为事件目标。

<span id="current_thread"></span><span id="CURRENT_THREAD"></span>**当前线程**  
调试器引擎当前正在控制的线程。 事件发生时，当前线程设置为事件线程。

 

 





