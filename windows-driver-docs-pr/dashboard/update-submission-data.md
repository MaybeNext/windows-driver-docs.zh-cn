---
title: 更新提交数据
description: Microsoft 硬件 API 中的此方法可更新提交的详细信息。
author: balapv
ms.author: balapv
ms.topic: article
ms.date: 04/05/2018
ms.localizationpriority: medium
ms.openlocfilehash: 1c8bb7598480e7c98802afc8b42e4e5aa4ed65cb
ms.sourcegitcommit: dabd74b55ce26f2e1c99c440cea2da9ea7d8b62c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/13/2019
ms.locfileid: "63334886"
---
# <a name="update-submission-data"></a>更新提交数据 

使用 Microsoft 硬件 API 中的此方法可更新提交的详细信息。 使用此方法之前，请确保已创建了提交。 有关详细信息，请参阅[创建新提交](create-a-new-hardware-submission.md)。


## <a name="prerequisites"></a>必备条件
如果尚未开始操作，请先完成 Microsoft 硬件 API 的所有[先决条件](dashboard-api.md)，然后再尝试使用其中任何方法。

## <a name="request"></a>请求
此方法具有以下语法。 请参阅以下部分，获取标头和请求正文的使用示例和描述。

| 方法 | 请求 URI |
|:--|:--|
| 修补程序 | `https://manage.devcenter.microsoft.com/v1.0/my/hardware/products/{productID}/submissions/{submissionId}`

### <a name="request-header"></a>请求头

| 标头 | 在任务栏的搜索框中键入 | 描述 |
|:--|:--|:--|
|授权 | 字符串 | 必需。 Azure AD 访问令牌的格式为 **Bearer** \<token\>。 |
| accept | 字符串 | 可选。 指定内容的类型。 允许的值是“application/json” |

### <a name="request-parameters"></a>请求参数

请勿为此方法提供请求参数。

### <a name="request-body"></a>请求正文

以下示例演示了用于更新产品的 JSON 请求正文。 只能对提交进行名称更改。

```json
{
  "name": "updatedSubmissionName"
}
```

有关请求中的字段的详细信息，请参阅[提交资源](get-product-data.md#submission-resource)。

### <a name="request-examples"></a>请求示例
以下示例演示了如何更新产品。

```json 
PATCH https://manage.devcenter.microsoft.com/v1.0/my/hardware/products/14631253285588838/submissions/1152921504627422408 HTTP/1.1
Authorization: Bearer <your access token>
```

## <a name="response"></a>响应

响应将为空并且 HTTP 状态为 204。

完成此步骤后，请使用[获取提交详细信息](get-a-submission.md)方法来获取更新的产品详细信息。

## <a name="error-codes"></a>错误代码
有关详细信息，请参阅[错误代码](get-product-data.md#error-codes)。

## <a name="see-also"></a>另请参阅

- [硬件仪表板 API 示例 (GitHub)](https://aka.ms/hpc_async_api_samples)
