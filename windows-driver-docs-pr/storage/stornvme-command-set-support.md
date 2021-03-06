---
title: StorNVMe 命令集支持
description: StorNVMe 命令集支持
ms.assetid: c0bcee11-ea66-4726-99a2-ad18256cf616
ms.date: 12/12/2019
ms.localizationpriority: medium
ms.openlocfilehash: ff9ffed8c39469bfc086ebee85b1be55722fd248
ms.sourcegitcommit: d30691c8276f7dddd3f8333e84744ddeea1e1020
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/19/2019
ms.locfileid: "75252078"
---
# <a name="stornvme-command-set-support"></a>StorNVMe 命令集支持

下表列出了 NVMe *Admin*和*NVM*命令集及关联的操作码，并指示**StorNVMe**为每个命令提供的支持。  

## <a name="admin-command-set-support"></a>管理命令集支持

| 操作码  | NVMe 命令                | StorNVMe 支持      | 备注 |
| ------  | --------------------------  | --------------------- | -------- |
| 0       | 删除 i/o 提交队列 | 内部驱动程序使用情况 |    |
| 1       | 创建 i/o 提交队列 | 内部驱动程序使用情况 |    |
| 2       | 获取日志页                | 内部驱动程序使用情况;IOCTL_STORAGE_QUERY_PROPERTY |   |
| 4       | 删除 i/o 完成队列 | 内部驱动程序使用情况 |   |
| 5       | 创建 i/o 完成队列 | 内部驱动程序使用情况 |
| 6       | 指出                    | 内部驱动程序使用情况;IOCTL_STORAGE_QUERY_PROPERTY，IOCTL_STORAGE_FIRMWARE_GET_INFO |   |
| 8       | 中止                       |   | 当前不支持 |
| 9       | 设置功能                | 内部驱动程序使用情况;IOCTL_STORAGE_SET_PROPERTY | 仅对主机控制的热量管理设置了 IOCTL_STORAGE_SET_PROPERTY 的功能 |
| 啊      | 获取功能                | 内部驱动程序使用情况;IOCTL_STORAGE_QUERY_PROPERTY |   |
| 48      | 异步事件请求  | 内部驱动程序使用情况 |   |   |
| Dh      | 命名空间管理        | IOCTL_STORAGE_PROTOCOL_COMMAND | 仅在 Win PE 模式下为 IOCTL_STORAGE_PROTOCOL_COMMAND 启用 |
| 10h     | 固件提交             | IOCTL_STORAGE_FIRMWARE_ACTIVATE | |
| 11h     | 固件映像下载     | IOCTL_STORAGE_FIRMWARE_DOWNLOAD | |
| 14h     | 设备自检            | IOCTL_STORAGE_PROTOCOL_COMMAND  | |
| 15h     | 命名空间附件        | IOCTL_STORAGE_PROTOCOL_COMMAND | 仅在 Win PE 模式下为 IOCTL_STORAGE_PROTOCOL_COMMAND 启用 |
| 19h     | 指令发送              | 内部驱动程序使用情况 |   |
| 1Ah     | 指令接收           | 内部驱动程序使用情况 |   |
| 1Ch     | 虚拟化管理   |   | 当前不支持 |
| 1Dh     | NVMe-英里发送                | IOCTL_STORAGE_PROTOCOL_COMMAND | 仅在 Win PE 模式下为 IOCTL_STORAGE_PROTOCOL_COMMAND 启用 |
| 1Eh     | NVMe-英里接收             | IOCTL_STORAGE_PROTOCOL_COMMAND | 仅在 Win PE 模式下为 IOCTL_STORAGE_PROTOCOL_COMMAND 启用 |
| 7Ch     | Doorbell Buffer Config      |   | 当前不支持 |
| 80h     | 格式 NVM                  | IOCTL_SCSI_PASS_THROUGH、IOCTL_STORAGE_PROTOCOL_COMMAND IOCTL_STORAGE_REINITIALIZE_MEDIA | 仅在 Win PE 模式下为 IOCTL_STORAGE_PROTOCOL_COMMAND 启用。 IOCTL_SCSI_PASS_THROUGH 的 SCSIOP_SANITIZE。 IOCTL_STORAGE_REINITIALIZE_MEDIA 仅支持加密擦除。 |
| 81h     | 安全发送               | IOCTL_SCSI_PASS_THROUGH | IOCTL_SCSI_PASS_THROUGH 的 SCSIOP_SECURITY_PROTOCOL_OUT |
| 82h     | 安全接收            | IOCTL_SCSI_PASS_THROUGH | IOCTL_SCSI_PASS_THROUGH 的 SCSIOP_SECURITY_PROTOCOL_IN |
| 84h     | 净化                    | IOCTL_STORAGE_PROTOCOL_COMMAND | 仅在 Win PE 模式下为 IOCTL_STORAGE_PROTOCOL_COMMAND 启用 |
| 86h     | 获取 LBA 状态              |   | 当前不支持 |
| C0h-FFh | 特定于供应商             | IOCTL_STORAGE_PROTOCOL_COMMAND | 特定于供应商的传递命令。 要求控制器支持命令效果日志，并且供应商命令的命令效果数据应报告为受支持。 |

## <a name="nvm-command-set-support"></a>NVM 命令集支持

| 操作码  | NVMe 命令                | StorNVMe 支持      | 备注 |
| ------  | --------------------------  | --------------------- | -------- |
| 0       | 刷新                       | 内部驱动程序使用情况，IOCTL_SCSI_PASS_THROUGH | IOCTL_SCSI_PASS_THROUGH 的 SCSIOP_SYNCHRONIZE_CACHE |
| 1       | 写入                       | 内部驱动程序使用情况，IOCTL_SCSI_PASS_THROUGH | IOCTL_SCSI_PASS_THROUGH 的 SCSIOP_WRITE/SCSIOP_WRITE16 |
| 2       | 已阅读                        | 内部驱动程序使用情况，IOCTL_SCSI_PASS_THROUGH | IOCTL_SCSI_PASS_THROUGH 的 SCSIOP_READ/SCSIOP_READ16 |
| 4       | 写入无法纠正         |   | 当前不支持 |
| 5       | “比较”                     | IOCTL_STORAGE_PROTOCOL_COMMAND | 仅在 Win PE 模式下为 IOCTL_STORAGE_PROTOCOL_COMMAND 启用 |
| 8       | 写零                |   | 当前不支持 |
| 9       | 数据集管理          | IOCTL_SCSI_PASS_THROUGH | 仅剪裁（解除分配）;IOCTL_SCSI_PASS_THROUGH 的 SCSIOP_UNMAP |
| 48      | 验证                      |   | 当前不支持 |
| Dh      | 预订注册        |   | 当前不支持 |
| 吧      | 预订报表          |   | 当前不支持 |
| 11h     | 预留获取         |   | 当前不支持 |
| 15h     | 保留发布         |   | 当前不支持 |
| 80h-FFh | 特定于供应商             | IOCTL_STORAGE_PROTOCOL_COMMAND | 特定于供应商的传递命令。 要求控制器支持命令效果日志，并且供应商命令的命令效果数据应报告为受支持。 |
