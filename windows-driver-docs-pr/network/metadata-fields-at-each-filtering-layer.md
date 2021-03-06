---
title: 每个筛选层的元数据字段
description: 本部分介绍在每个筛选层上的 Windows 筛选平台标注驱动程序的元数据字段。
ms.assetid: 77152ebe-1721-48b3-9380-7f565931a0e5
keywords:
- 元数据字段在每个筛选层网络驱动程序
ms.date: 11/09/2017
ms.localizationpriority: medium
ms.openlocfilehash: 32a29f1a099572a24d0023a7c1a0200890827d8f
ms.sourcegitcommit: 0cc5051945559a242d941a6f2799d161d8eba2a7
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "63335226"
---
# <a name="metadata-fields-at-each-filtering-layer"></a>每个筛选层的元数据字段

下表列出了可用的层的可能的元数据字段。 某些字段为仅在特定情况下可用。 例如，元数据字段 FWPS_METADATA_FIELD_FRAGMENT_DATA 才可用于入站 IP 数据包层该数据包分为碎片。 表中未列出的层不具有任何可用的元数据字段。

<table>
<tr>
<th>
       运行时筛选层标识符
       
      </th>
<th>
       元数据字段
       
      </th>
</tr>
<tr>
<td>
<p>FWPS_LAYER_INBOUND_IPPACKET_V4</p>
<p>FWPS_LAYER_INBOUND_IPPACKET_V6</p>
</td>
<td>
<p>FWPS_METADATA_FIELD_IP_HEADER_SIZE</p>
<p>FWPS_METADATA_FIELD_COMPARTMENT_ID</p>
<p>FWPS_METADATA_FIELD_FRAGMENT_DATA</p>
</td>
</tr>
<tr>
<td>
<p>FWPS_LAYER_INBOUND_IPPACKET_V4_DISCARD</p>
<p>FWPS_LAYER_INBOUND_IPPACKET_V6_DISCARD</p>
</td>
<td>
<p>FWPS_METADATA_FIELD_DISCARD_REASON</p>
<p>FWPS_METADATA_FIELD_IP_HEADER_SIZE</p>
<p>FWPS_METADATA_FIELD_COMPARTMENT_ID</p>
<p>FWPS_METADATA_FIELD_FRAGMENT_DATA</p>
</td>
</tr>
<tr>
<td>
<p>FWPS_LAYER_OUTBOUND_IPPACKET_V4</p>
<p>FWPS_LAYER_OUTBOUND_IPPACKET_V6</p>
</td>
<td>
<p>FWPS_METADATA_FIELD_IP_HEADER_SIZE</p>
<p>FWPS_METADATA_FIELD_TRANSPORT_HEADER_SIZE</p>
<p>FWPS_METADATA_FIELD_COMPARTMENT_ID</p>
<p>FWPS_METADATA_FIELD_FRAGMENT_DATA</p>
<p>FWPS_METADATA_FIELD_PATH_MTU</p>
</td>
</tr>
<tr>
<td>
<p>FWPS_LAYER_OUTBOUND_IPPACKET_V4_DISCARD</p>
<p>FWPS_LAYER_OUTBOUND_IPPACKET_V6_DISCARD</p>
</td>
<td>
<p>FWPS_METADATA_FIELD_DISCARD_REASON</p>
<p>FWPS_METADATA_FIELD_IP_HEADER_SIZE</p>
<p>FWPS_METADATA_FIELD_TRANSPORT_HEADER_SIZE</p>
<p>FWPS_METADATA_FIELD_COMPARTMENT_ID</p>
<p>FWPS_METADATA_FIELD_FRAGMENT_DATA</p>
<p>FWPS_METADATA_FIELD_PATH_MTU</p>
</td>
</tr>
<tr>
<td>
<p>FWPS_LAYER_IPFORWARD_V4</p>
<p>FWPS_LAYER_IPFORWARD_V6</p>
</td>
<td>
<p>FWPS_METADATA_FIELD_COMPARTMENT_ID</p>
</td>
</tr>
<tr>
<td>
<p>FWPS_LAYER_IPFORWARD_V4_DISCARD</p>
<p>FWPS_LAYER_IPFORWARD_V6_DISCARD</p>
</td>
<td>
<p>FWPS_METADATA_FIELD_DISCARD_REASON</p>
<p>FWPS_METADATA_FIELD_COMPARTMENT_ID</p>
</td>
</tr>
<tr>
<td>
<p>FWPS_LAYER_INBOUND_TRANSPORT_V4</p>
<p>FWPS_LAYER_INBOUND_TRANSPORT_V6</p>
</td>
<td>
<p>FWPS_METADATA_FIELD_FLOW_HANDLE</p>
<p>FWPS_METADATA_FIELD_IP_HEADER_SIZE</p>
<p>FWPS_METADATA_FIELD_SYSTEM_FLAGS</p>
<p>FWPS_METADATA_FIELD_RESERVED</p>
<p>FWPS_METADATA_FIELD_TRANSPORT_HEADER_SIZE</p>
<p>FWPS_METADATA_FIELD_COMPARTMENT_ID</p>
<p>FWPS_METADATA_FIELD_TRANSPORT_ENDPOINT_HANDLE</p>
<p>FWPS_METADATA_FIELD_ALE_CLASSIFY_REQUIRED</p>
<p>FWPS_METADATA_FIELD_ICMP_ID_AND_SEQUENCE</p>
</td>
</tr>
<tr>
<td>
<p>FWPS_LAYER_INBOUND_TRANSPORT_V4_DISCARD</p>
<p>FWPS_LAYER_INBOUND_TRANSPORT_V6_DISCARD</p>
</td>
<td>
<p>FWPS_METADATA_FIELD_DISCARD_REASON</p>
<p>FWPS_METADATA_FIELD_FLOW_HANDLE</p>
<p>FWPS_METADATA_FIELD_IP_HEADER_SIZE</p>
<p>FWPS_METADATA_FIELD_SYSTEM_FLAGS</p>
<p>FWPS_METADATA_FIELD_RESERVED</p>
<p>FWPS_METADATA_FIELD_TRANSPORT_HEADER_SIZE</p>
<p>FWPS_METADATA_FIELD_COMPARTMENT_ID</p>
<p>FWPS_METADATA_FIELD_TRANSPORT_ENDPOINT_HANDLE</p>
<p>FWPS_METADATA_FIELD_ALE_CLASSIFY_REQUIRED</p>
<p>FWPS_METADATA_FIELD_ICMP_ID_AND_SEQUENCE</p>
</td>
</tr>
<tr>
<td>
<p>FWPS_LAYER_OUTBOUND_TRANSPORT_V4</p>
<p>FWPS_LAYER_OUTBOUND_TRANSPORT_V6</p>
</td>
<td>
<p>FWPS_METADATA_FIELD_FLOW_HANDLE</p>
<p>FWPS_METADATA_FIELD_SYSTEM_FLAGS</p>
<p>FWPS_METADATA_FIELD_RESERVED</p>
<p>FWPS_METADATA_FIELD_TRANSPORT_HEADER_SIZE</p>
<p>FWPS_METADATA_FIELD_COMPARTMENT_ID</p>
<p>FWPS_METADATA_FIELD_TRANSPORT_ENDPOINT_HANDLE</p>
<p>FWPS_METADATA_FIELD_TRANSPORT_CONTROL_DATA</p>
<p>FWPS_METADATA_FIELD_REMOTE_SCOPE_ID</p>
<p>FWPS_METADATA_FIELD_ICMP_ID_AND_SEQUENCE</p>
</td>
</tr>
<tr>
<td>
<p>FWPS_LAYER_OUTBOUND_TRANSPORT_V4_DISCARD</p>
<p>FWPS_LAYER_OUTBOUND_TRANSPORT_V6_DISCARD</p>
</td>
<td>
<p>FWPS_METADATA_FIELD_DISCARD_REASON</p>
<p>FWPS_METADATA_FIELD_FLOW_HANDLE</p>
<p>FWPS_METADATA_FIELD_SYSTEM_FLAGS</p>
<p>FWPS_METADATA_FIELD_RESERVED</p>
<p>FWPS_METADATA_FIELD_TRANSPORT_HEADER_SIZE</p>
<p>FWPS_METADATA_FIELD_COMPARTMENT_ID</p>
<p>FWPS_METADATA_FIELD_TRANSPORT_ENDPOINT_HANDLE</p>
<p>FWPS_METADATA_FIELD_TRANSPORT_CONTROL_DATA</p>
<p>FWPS_METADATA_FIELD_REMOTE_SCOPE_ID</p>
<p>FWPS_METADATA_FIELD_ICMP_ID_AND_SEQUENCE</p>
</td>
</tr>
<tr>
<td>
<p>FWPS_LAYER_STREAM_V4</p>
<p>FWPS_LAYER_STREAM_V6</p>
</td>
<td>
<p>FWPS_METADATA_FIELD_FLOW_HANDLE</p>
<p>FWPS_METADATA_FIELD_SYSTEM_FLAGS</p>
</td>
</tr>
<tr>
<td>
<p>FWPS_LAYER_STREAM_V4_DISCARD</p>
<p>FWPS_LAYER_STREAM_V6_DISCARD</p>
</td>
<td>
<p>FWPS_METADATA_FIELD_DISCARD_REASON</p>
<p>FWPS_METADATA_FIELD_FLOW_HANDLE</p>
<p>FWPS_METADATA_FIELD_SYSTEM_FLAGS</p>
</td>
</tr>
<tr>
<td>
<p>FWPS_LAYER_DATAGRAM_DATA_V4</p>
<p>FWPS_LAYER_DATAGRAM_DATA_V6</p>
</td>
<td>
<p>FWPS_METADATA_FIELD_FLOW_HANDLE</p>
<p>FWPS_METADATA_FIELD_IP_HEADER_SIZE</p>
<p>FWPS_METADATA_FIELD_SYSTEM_FLAGS</p>
<p>FWPS_METADATA_FIELD_TRANSPORT_HEADER_SIZE</p>
<p>FWPS_METADATA_FIELD_COMPARTMENT_ID</p>
<p>FWPS_METADATA_FIELD_TRANSPORT_ENDPOINT_HANDLE</p>
<p>FWPS_METADATA_FIELD_TRANSPORT_CONTROL_DATA</p>
<p>FWPS_METADATA_FIELD_REMOTE_SCOPE_ID</p>
<p>FWPS_METADATA_FIELD_ICMP_ID_AND_SEQUENCE</p>
</td>
</tr>
<tr>
<td>
<p>FWPS_LAYER_DATAGRAM_DATA_V4_DISCARD</p>
<p>FWPS_LAYER_DATAGRAM_DATA_V6_DISCARD</p>
</td>
<td>
<p>FWPS_METADATA_FIELD_DISCARD_REASON</p>
<p>FWPS_METADATA_FIELD_FLOW_HANDLE</p>
<p>FWPS_METADATA_FIELD_IP_HEADER_SIZE</p>
<p>FWPS_METADATA_FIELD_SYSTEM_FLAGS</p>
<p>FWPS_METADATA_FIELD_TRANSPORT_HEADER_SIZE</p>
<p>FWPS_METADATA_FIELD_COMPARTMENT_ID</p>
<p>FWPS_METADATA_FIELD_TRANSPORT_ENDPOINT_HANDLE</p>
<p>FWPS_METADATA_FIELD_TRANSPORT_CONTROL_DATA</p>
<p>FWPS_METADATA_FIELD_REMOTE_SCOPE_ID</p>
<p>FWPS_METADATA_FIELD_ICMP_ID_AND_SEQUENCE</p>
</td>
</tr>
<tr>
<td>
<p>FWPS_LAYER_INBOUND_ICMP_ERROR_V4</p>
<p>FWPS_LAYER_INBOUND_ICMP_ERROR_V6</p>
</td>
<td>
<p>FWPS_METADATA_FIELD_IP_HEADER_SIZE</p>
<p>FWPS_METADATA_FIELD_TRANSPORT_HEADER_SIZE</p>
<p>FWPS_METADATA_FIELD_COMPARTMENT_ID</p>
<p>FWPS_METADATA_FIELD_TRANSPORT_ENDPOINT_HANDLE</p>
</td>
</tr>
<tr>
<td>
<p>FWPS_LAYER_INBOUND_ICMP_ERROR_V4_DISCARD</p>
<p>FWPS_LAYER_INBOUND_ICMP_ERROR_V6_DISCARD</p>
</td>
<td>
<p>FWPS_METADATA_FIELD_DISCARD_REASON</p>
<p>FWPS_METADATA_FIELD_IP_HEADER_SIZE</p>
<p>FWPS_METADATA_FIELD_TRANSPORT_HEADER_SIZE</p>
<p>FWPS_METADATA_FIELD_COMPARTMENT_ID</p>
<p>FWPS_METADATA_FIELD_TRANSPORT_ENDPOINT_HANDLE</p>
</td>
</tr>
<tr>
<td>
<p>FWPS_LAYER_OUTBOUND_ICMP_ERROR_V4</p>
<p>FWPS_LAYER_OUTBOUND_ICMP_ERROR_V6</p>
</td>
<td>
<p>FWPS_METADATA_FIELD_SYSTEM_FLAGS</p>
<p>FWPS_METADATA_FIELD_TRANSPORT_HEADER_SIZE</p>
<p>FWPS_METADATA_FIELD_COMPARTMENT_ID</p>
<p>FWPS_METADATA_FIELD_TRANSPORT_ENDPOINT_HANDLE</p>
<p>FWPS_METADATA_FIELD_TRANSPORT_CONTROL_DATA</p>
<p>FWPS_METADATA_FIELD_REMOTE_SCOPE_ID</p>
</td>
</tr>
<tr>
<td>
<p>FWPS_LAYER_OUTBOUND_ICMP_ERROR_V4_DISCARD</p>
<p>FWPS_LAYER_OUTBOUND_ICMP_ERROR_V6_DISCARD</p>
</td>
<td>
<p>FWPS_METADATA_FIELD_DISCARD_REASON</p>
<p>FWPS_METADATA_FIELD_SYSTEM_FLAGS</p>
<p>FWPS_METADATA_FIELD_TRANSPORT_HEADER_SIZE</p>
<p>FWPS_METADATA_FIELD_COMPARTMENT_ID</p>
<p>FWPS_METADATA_FIELD_TRANSPORT_ENDPOINT_HANDLE</p>
<p>FWPS_METADATA_FIELD_TRANSPORT_CONTROL_DATA</p>
<p>FWPS_METADATA_FIELD_REMOTE_SCOPE_ID</p>
</td>
</tr>
<tr>
<td>
<p>FWPS_LAYER_ALE_RESOURCE_ASSIGNMENT_V4</p>
<p>FWPS_LAYER_ALE_RESOURCE_ASSIGNMENT_V6</p>
</td>
<td>
<p>FWPS_METADATA_FIELD_PROCESS_PATH</p>
<p>FWPS_METADATA_FIELD_TOKEN</p>
<p>FWPS_METADATA_FIELD_PROCESS_ID</p>
<p>FWPS_METADATA_FIELD_RESERVED</p>
<p>FWPS_METADATA_FIELD_COMPLETION_HANDLE</p>
<p>FWPS_METADATA_FIELD_TRANSPORT_ENDPOINT_HANDLE</p>
<p>FWPS_METADATA_FIELD_SUB_PROCESS_TAG</p>
</td>
</tr>
<tr>
<td>
<p>FWPS_LAYER_ALE_RESOURCE_ASSIGNMENT_V4_DISCARD</p>
<p>FWPS_LAYER_ALE_RESOURCE_ASSIGNMENT_V6_DISCARD</p>
</td>
<td>
<p>FWPS_METADATA_FIELD_DISCARD_REASON</p>
<p>FWPS_METADATA_FIELD_PROCESS_PATH</p>
<p>FWPS_METADATA_FIELD_TOKEN</p>
<p>FWPS_METADATA_FIELD_PROCESS_ID</p>
<p>FWPS_METADATA_FIELD_RESERVED</p>
<p>FWPS_METADATA_FIELD_COMPLETION_HANDLE</p>
<p>FWPS_METADATA_FIELD_TRANSPORT_ENDPOINT_HANDLE</p>
<p>FWPS_METADATA_FIELD_SUB_PROCESS_TAG</p>
</td>
</tr>
<tr>
<td>
<p>FWPS_LAYER_ALE_AUTH_LISTEN_V4</p>
<p>FWPS_LAYER_ALE_AUTH_LISTEN_V6</p>
</td>
<td>
<p>FWPS_METADATA_FIELD_PROCESS_PATH</p>
<p>FWPS_METADATA_FIELD_TOKEN</p>
<p>FWPS_METADATA_FIELD_PROCESS_ID</p>
<p>FWPS_METADATA_FIELD_RESERVED</p>
<p>FWPS_METADATA_FIELD_COMPLETION_HANDLE</p>
<p>FWPS_METADATA_FIELD_TRANSPORT_ENDPOINT_HANDLE</p>
<p>FWPS_METADATA_FIELD_SUB_PROCESS_TAG</p>
</td>
</tr>
<tr>
<td>
<p>FWPS_LAYER_ALE_AUTH_LISTEN_V4_DISCARD</p>
<p>FWPS_LAYER_ALE_AUTH_LISTEN_V6_DISCARD</p>
</td>
<td>
<p>FWPS_METADATA_FIELD_DISCARD_REASON</p>
<p>FWPS_METADATA_FIELD_PROCESS_PATH</p>
<p>FWPS_METADATA_FIELD_TOKEN</p>
<p>FWPS_METADATA_FIELD_PROCESS_ID</p>
<p>FWPS_METADATA_FIELD_RESERVED</p>
<p>FWPS_METADATA_FIELD_COMPLETION_HANDLE</p>
<p>FWPS_METADATA_FIELD_TRANSPORT_ENDPOINT_HANDLE</p>
<p>FWPS_METADATA_FIELD_SUB_PROCESS_TAG</p>
</td>
</tr>
<tr>
<td>
<p>FWPS_LAYER_ALE_AUTH_RECV_ACCEPT_V4</p>
<p>FWPS_LAYER_ALE_AUTH_RECV_ACCEPT_V6</p>
</td>
<td>
<p>FWPS_METADATA_FIELD_FLOW_HANDLE</p>
<p>FWPS_METADATA_FIELD_IP_HEADER_SIZE</p>
<p>FWPS_METADATA_FIELD_PROCESS_PATH</p>
<p>FWPS_METADATA_FIELD_TOKEN</p>
<p>FWPS_METADATA_FIELD_PROCESS_ID</p>
<p>FWPS_METADATA_FIELD_RESERVED</p>
<p>FWPS_METADATA_FIELD_TRANSPORT_HEADER_SIZE</p>
<p>FWPS_METADATA_FIELD_COMPARTMENT_ID</p>
<p>FWPS_METADATA_FIELD_COMPLETION_HANDLE</p>
<p>FWPS_METADATA_FIELD_TRANSPORT_ENDPOINT_HANDLE</p>
<p>FWPS_METADATA_FIELD_PACKET_DIRECTION</p>
<p>FWPS_METADATA_FIELD_PARENT_ENDPOINT_HANDLE</p>
<p>FWPS_METADATA_FIELD_ICMP_ID_AND_SEQUENCE</p>
<p>FWPS_METADATA_FIELD_SUB_PROCESS_TAG</p>
</td>
</tr>
<tr>
<td>
<p>FWPS_LAYER_ALE_AUTH_RECV_ACCEPT_V4_DISCARD</p>
<p>FWPS_LAYER_ALE_AUTH_RECV_ACCEPT_V6_DISCARD</p>
</td>
<td>
<p>FWPS_METADATA_FIELD_DISCARD_REASON</p>
<p>FWPS_METADATA_FIELD_FLOW_HANDLE</p>
<p>FWPS_METADATA_FIELD_IP_HEADER_SIZE</p>
<p>FWPS_METADATA_FIELD_PROCESS_PATH</p>
<p>FWPS_METADATA_FIELD_TOKEN</p>
<p>FWPS_METADATA_FIELD_PROCESS_ID</p>
<p>FWPS_METADATA_FIELD_RESERVED</p>
<p>FWPS_METADATA_FIELD_TRANSPORT_HEADER_SIZE</p>
<p>FWPS_METADATA_FIELD_COMPARTMENT_ID</p>
<p>FWPS_METADATA_FIELD_COMPLETION_HANDLE</p>
<p>FWPS_METADATA_FIELD_TRANSPORT_ENDPOINT_HANDLE</p>
<p>FWPS_METADATA_FIELD_PACKET_DIRECTION</p>
<p>FWPS_METADATA_FIELD_PARENT_ENDPOINT_HANDLE</p>
<p>FWPS_METADATA_FIELD_ICMP_ID_AND_SEQUENCE</p>
<p>FWPS_METADATA_FIELD_SUB_PROCESS_TAG</p>
</td>
</tr>
<tr>
<td>
<p>FWPS_LAYER_ALE_AUTH_CONNECT_V4</p>
<p>FWPS_LAYER_ALE_AUTH_CONNECT_V6</p>
</td>
<td>
<p>FWPS_METADATA_FIELD_FLOW_HANDLE</p>
<p>FWPS_METADATA_FIELD_PROCESS_PATH</p>
<p>FWPS_METADATA_FIELD_TOKEN</p>
<p>FWPS_METADATA_FIELD_PROCESS_ID</p>
<p>FWPS_METADATA_FIELD_RESERVED</p>
<p>FWPS_METADATA_FIELD_TRANSPORT_HEADER_SIZE</p>
<p>FWPS_METADATA_FIELD_COMPARTMENT_ID</p>
<p>FWPS_METADATA_FIELD_COMPLETION_HANDLE</p>
<p>FWPS_METADATA_FIELD_TRANSPORT_ENDPOINT_HANDLE</p>
<p>FWPS_METADATA_FIELD_REMOTE_SCOPE_ID</p>
<p>FWPS_METADATA_FIELD_PACKET_DIRECTION</p>
<p>FWPS_METADATA_FIELD_PARENT_ENDPOINT_HANDLE</p>
<p>FWPS_METADATA_FIELD_ICMP_ID_AND_SEQUENCE</p>
<p>FWPS_METADATA_FIELD_SUB_PROCESS_TAG</p>
</td>
</tr>
<tr>
<td>
<p>FWPS_LAYER_ALE_AUTH_CONNECT_V4_DISCARD</p>
<p>FWPS_LAYER_ALE_AUTH_CONNECT_V6_DISCARD</p>
</td>
<td>
<p>FWPS_METADATA_FIELD_DISCARD_REASON</p>
<p>FWPS_METADATA_FIELD_FLOW_HANDLE</p>
<p>FWPS_METADATA_FIELD_PROCESS_PATH</p>
<p>FWPS_METADATA_FIELD_TOKEN</p>
<p>FWPS_METADATA_FIELD_PROCESS_ID</p>
<p>FWPS_METADATA_FIELD_RESERVED</p>
<p>FWPS_METADATA_FIELD_TRANSPORT_HEADER_SIZE</p>
<p>FWPS_METADATA_FIELD_COMPARTMENT_ID</p>
<p>FWPS_METADATA_FIELD_COMPLETION_HANDLE</p>
<p>FWPS_METADATA_FIELD_TRANSPORT_ENDPOINT_HANDLE</p>
<p>FWPS_METADATA_FIELD_REMOTE_SCOPE_ID</p>
<p>FWPS_METADATA_FIELD_PACKET_DIRECTION</p>
<p>FWPS_METADATA_FIELD_PARENT_ENDPOINT_HANDLE</p>
<p>FWPS_METADATA_FIELD_ICMP_ID_AND_SEQUENCE</p>
<p>FWPS_METADATA_FIELD_SUB_PROCESS_TAG</p>
</td>
</tr>
<tr>
<td>
<p>FWPS_LAYER_ALE_FLOW_ESTABLISHED_V4</p>
<p>FWPS_LAYER_ALE_FLOW_ESTABLISHED_V6</p>
</td>
<td>
<p>FWPS_METADATA_FIELD_FLOW_HANDLE</p>
<p>FWPS_METADATA_FIELD_PROCESS_PATH</p>
<p>FWPS_METADATA_FIELD_TOKEN</p>
<p>FWPS_METADATA_FIELD_PROCESS_ID</p>
<p>FWPS_METADATA_FIELD_RESERVED</p>
<p>FWPS_METADATA_FIELD_TRANSPORT_ENDPOINT_HANDLE</p>
<p>FWPS_METADATA_FIELD_PARENT_ENDPOINT_HANDLE</p>
<p>FWPS_METADATA_FIELD_ICMP_ID_AND_SEQUENCE</p>
<p>FWPS_METADATA_FIELD_SUB_PROCESS_TAG</p>
</td>
</tr>
<tr>
<td>
<p>FWPS_LAYER_ALE_FLOW_ESTABLISHED_V4_DISCARD</p>
<p>FWPS_LAYER_ALE_FLOW_ESTABLISHED_V6_DISCARD</p>
</td>
<td>
<p>FWPS_METADATA_FIELD_DISCARD_REASON</p>
<p>FWPS_METADATA_FIELD_FLOW_HANDLE</p>
<p>FWPS_METADATA_FIELD_PROCESS_PATH</p>
<p>FWPS_METADATA_FIELD_TOKEN</p>
<p>FWPS_METADATA_FIELD_PROCESS_ID</p>
<p>FWPS_METADATA_FIELD_RESERVED</p>
<p>FWPS_METADATA_FIELD_TRANSPORT_ENDPOINT_HANDLE</p>
<p>FWPS_METADATA_FIELD_PARENT_ENDPOINT_HANDLE</p>
<p>FWPS_METADATA_FIELD_ICMP_ID_AND_SEQUENCE</p>
<p>FWPS_METADATA_FIELD_SUB_PROCESS_TAG</p>
</td>
</tr>
<tr>
<td>
<p>FWPS_LAYER_INBOUND_MAC_FRAME_802_3</p>
</td>
<td>
<p>FWPS_METADATA_FIELD_ETHER_FRAME_LENGTH</p>
</td>
</tr>
<tr>
<td>
<p>FWPS_LAYER_ALE_RESOURCE_RELEASE_V4</p>
<p>FWPS_LAYER_ALE_RESOURCE_RELEASE_V6</p>
</td>
<td>
<p>FWPS_METADATA_FIELD_TOKEN</p>
<p>FWPS_METADATA_FIELD_PROCESS_ID</p>
<p>FWPS_METADATA_FIELD_COMPARTMENT_ID</p>
<p>FWPS_METADATA_FIELD_TRANSPORT_ENDPOINT_HANDLE</p>
<p>FWPS_METADATA_FIELD_SUB_PROCESS_TAG</p>
</td>
</tr>
<tr>
<td>
<p>FWPS_LAYER_ALE_ENDPOINT_CLOSURE_V4</p>
<p>FWPS_LAYER_ALE_ENDPOINT_CLOSURE_V6</p>
</td>
<td>
<p>FWPS_METADATA_FIELD_TOKEN</p>
<p>FWPS_METADATA_FIELD_PROCESS_ID</p>
<p>FWPS_METADATA_FIELD_COMPARTMENT_ID</p>
<p>FWPS_METADATA_FIELD_TRANSPORT_ENDPOINT_HANDLE</p>
<p>FWPS_METADATA_FIELD_PARENT_ENDPOINT_HANDLE</p>
<p>FWPS_METADATA_FIELD_SUB_PROCESS_TAG</p>
</td>
</tr>
<tr>
<td>
<p>FWPS_LAYER_ALE_CONNECT_REDIRECT_V4</p>
<p>FWPS_LAYER_ALE_CONNECT_REDIRECT_V6</p>
</td>
<td>
<p>FWPS_METADATA_FIELD_TOKEN</p>
<p>FWPS_METADATA_FIELD_PROCESS_ID</p>
<p>FWPS_METADATA_FIELD_TRANSPORT_ENDPOINT_HANDLE</p>
<p>FWPS_METADATA_FIELD_PARENT_ENDPOINT_HANDLE</p>
<p>FWPS_METADATA_FIELD_ICMP_ID_AND_SEQUENCE</p>
<p>FWPS_METADATA_FIELD_LOCAL_REDIRECT_TARGET_PID</p>
<p>FWPS_METADATA_FIELD_REDIRECT_RECORD_HANDLE</p>
<p>FWPS_METADATA_FIELD_SUB_PROCESS_TAG</p>
</td>
</tr>
<tr>
<td>
<p>FWPS_LAYER_ALE_BIND_REDIRECT_V4</p>
<p>FWPS_LAYER_ALE_BIND_REDIRECT_V6</p>
</td>
<td>
<p>FWPS_METADATA_FIELD_TOKEN</p>
<p>FWPS_METADATA_FIELD_PROCESS_ID</p>
<p>FWPS_METADATA_FIELD_TRANSPORT_ENDPOINT_HANDLE</p>
<p>FWPS_METADATA_FIELD_LOCAL_REDIRECT_TARGET_PID</p>
<p>FWPS_METADATA_FIELD_SUB_PROCESS_TAG</p>
</td>
</tr>
<tr>
<td>
<p>FWPS_LAYER_STREAM_PACKET_V4</p>
<p>FWPS_LAYER_STREAM_PACKET_V6</p>
</td>
<td>
<p>FWPS_METADATA_FIELD_FLOW_HANDLE</p>
<p>FWPS_METADATA_FIELD_IP_HEADER_SIZE</p>
<p>FWPS_METADATA_FIELD_SYSTEM_FLAGS</p>
<p>FWPS_METADATA_FIELD_TRANSPORT_HEADER_SIZE</p>
<p>FWPS_METADATA_FIELD_COMPARTMENT_ID</p>
<p>FWPS_METADATA_FIELD_TRANSPORT_ENDPOINT_HANDLE</p>
<p>FWPS_METADATA_FIELD_TRANSPORT_CONTROL_DATA</p>
<p>FWPS_METADATA_FIELD_REMOTE_SCOPE_ID</p>
</td>
</tr>
<tr>
<td>
<p>FWPS_LAYER_INGRESS_VSWITCH_ETHERNET</p>
<p>FWPS_LAYER_EGRESS_VSWITCH_ETHERNET</p>
</td>
<td>
<p>FWPS_L2_METADATA_FIELD_ETHERNET_MAC_HEADER_SIZE</p>
<p>FWPS_L2_METADATA_FIELD_WIFI_OPERATION_MODE</p>
<p>FWPS_L2_METADATA_FIELD_VSWITCH_SOURCE_PORT_ID</p>
<p>FWPS_L2_METADATA_FIELD_VSWITCH_SOURCE_NIC_INDEX</p>
<p>FWPS_L2_METADATA_FIELD_VSWITCH_PACKET_CONTEXT</p>
<p>FWPS_L2_METADATA_FIELD_VSWITCH_DESTINATION_PORT_ID</p>
</td>
</tr>
<tr>
<td>
<p>FWPS_LAYER_INGRESS_VSWITCH_TRANSPORT_V4</p>
<p>FWPS_LAYER_INGRESS_VSWITCH_TRANSPORT_V6</p>
<p>FWPS_LAYER_EGRESS_VSWITCH_TRANSPORT_V4</p>
<p>FWPS_LAYER_EGRESS_VSWITCH_TRANSPORT_V6</p>
</td>
<td>
<p>FWPS_L2_METADATA_FIELD_WIFI_OPERATION_MODE</p>
<p>FWPS_L2_METADATA_FIELD_VSWITCH_SOURCE_PORT_ID</p>
<p>FWPS_L2_METADATA_FIELD_VSWITCH_SOURCE_NIC_INDEX</p>
<p>FWPS_L2_METADATA_FIELD_VSWITCH_PACKET_CONTEXT</p>
<p>FWPS_L2_METADATA_FIELD_VSWITCH_DESTINATION_PORT_ID</p>
</td>
</tr>
</table>

