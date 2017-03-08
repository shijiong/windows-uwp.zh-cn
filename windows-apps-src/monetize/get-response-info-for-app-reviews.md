---
author: mcleanbyron
ms.assetid: fb6bb856-7a1b-4312-a602-f500646a3119
description: "在 Windows 应用商店评价 API 中使用此方法可以确定是否可以回复特定评价，或者是否可以回复针对给定应用的任何评价。"
title: "获取应用评价的回复信息"
ms.author: mcleans
ms.date: 02/08/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: "windows 10, uwp, 应用商店服务, Windows 应用商店评价 API, 回复信息"
translationtype: Human Translation
ms.sourcegitcommit: 5645eee3dc2ef67b5263b08800b0f96eb8a0a7da
ms.openlocfilehash: 88e6158bfc5df23e5c2056624e353b38b39c7331
ms.lasthandoff: 02/08/2017

---

# <a name="get-response-info-for-app-reviews"></a>获取应用评价的回复信息

如果你想以编程方式回复客户对你的应用的评价，可以在 Windows 应用商店评价 API 中使用此方法，以首先确定你是否有回复评价的权限。 你无法回复由选择不接收评价回复的客户提交的评价。 确认你可以回复评价后，你可以使用[提交对应用评价的回复](submit-responses-to-app-reviews.md)方法以编程方式回复评价。


## <a name="prerequisites"></a>先决条件

若要使用此方法，首先需要执行以下操作：

* 如果尚未开始操作，请先完成 Windows 应用商店分析 API 的所有[先决条件](respond-to-reviews-using-windows-store-services.md#prerequisites)。
* [获取 Azure AD 访问令牌](respond-to-reviews-using-windows-store-services.md#obtain-an-azure-ad-access-token)，以供在此方法的请求标头中使用。 获取访问令牌后，在它到期前，你有 60 分钟的使用时间。 该令牌到期后，可以获取新的令牌。
* 获取要检查的评价的 ID，以确定是否可以对其进行回复。 评价 ID 位于 Windows 应用商店分析 API 中的[获取应用评价](get-app-reviews.md)方法的回复数据中，以及[评价报告](../publish/reviews-report.md)的[脱机下载](../publish/download-analytic-reports.md)中。

## <a name="request"></a>请求


### <a name="request-syntax"></a>请求语法

| 方法 | 请求 URI                                                      |
|--------|------------------------------------------------------------------|
| GET    | ```https://manage.devcenter.microsoft.com/v1.0/my/reviews/{reviewId}/apps/{applicationId}/responses/info``` |

<span/> 

### <a name="request-header"></a>请求标头

| 标头        | 类型   | 说明                                                                 |
|---------------|--------|-----------------------------------------------------------------------------|
| 授权 | 字符串 | 必需。 Azure AD 访问令牌的格式为 **Bearer** &lt;*token*&gt;。 |

<span/> 

### <a name="request-parameters"></a>请求参数

| 参数        | 类型   | 描述                                     |  必需  |
|---------------|--------|--------------------------------------------------|--------------|
| applicationId | 字符串 | 其中的应用包含要确定是否可以回复的评价的应用商店 ID。 应用商店 ID 在开发人员中心仪表板的[应用标识页](../publish/view-app-identity-details.md)上提供。 应用商店 ID 的一个示例是 9WZDNCRFJ3Q8。 |  是  |
| reviewId | 字符串 | 要回复的评价 ID（这是一个 GUID）。 评价 ID 位于 Windows 应用商店分析 API 中的[获取应用评价](get-app-reviews.md)方法的回复数据中，以及[评价报告](../publish/reviews-report.md)的[脱机下载](../publish/download-analytic-reports.md)中。 <br/>如果忽略此参数，此方法的回复正文将指示你是否有回复指定应用的任何评价的权限。 |  否  |

<span/>

### <a name="request-example"></a>请求示例

以下示例演示如何使用此方法来确定是否可以回复给定的评价。

```syntax
GET https://manage.devcenter.microsoft.com/v1.0/my/reviews/6be543ff-1c9c-4534-aced-af8b4fbe0316/apps/9WZDNCRFJ3Q8/responses/info HTTP/1.1
Authorization: Bearer <your access token>
```

## <a name="response"></a>回复


### <a name="response-body"></a>回复正文

| 值      | 类型   | 描述    |  
|------------|--------|-----------------------|
| CanRespond      | 布尔值  | 值为 **true** 表示你可以回复指定的评价，或者你有回复指定应用的任何评价的权限。 否则，此值将为 **false**。       |
| DefaultSupportEmail  | 字符串 |  应用的[支持电子邮件地址](../publish/create-app-store-listings.md#support-contact-info)，其在应用的应用商店一览中有所指定。 如果未指定支持电子邮件地址，则此字段为空。    |

<span/>
 
### <a name="response-example"></a>回复示例

以下示例展示了此请求的 JSON 回复正文。

```json
{
  "CanRespond": true,
  "DefaultSupportEmail": "support@contoso.com"
}
```

## <a name="related-topics"></a>相关主题

* [使用 Windows 应用商店分析 API 提交对评价的回复](submit-responses-to-app-reviews.md)
* [使用开发人员中心仪表板回复客户评价](../publish/respond-to-customer-reviews.md)
* [使用 Windows 应用商店服务回复评价](respond-to-reviews-using-windows-store-services.md)
* [获取应用评价](get-app-reviews.md)
