---
author: mcleanbyron
ms.assetid: AC74B4FA-5554-4C03-9683-86EE48546C05
description: "在 Windows 应用商店提交 API 中使用此方法，向 Windows 开发人员中心确认新的或更新的加载项提交。"
title: "使用 Windows 应用商店提交 API 确认加载项提交"
translationtype: Human Translation
ms.sourcegitcommit: 5f975d0a99539292e1ce91ca09dbd5fac11c4a49
ms.openlocfilehash: f9b9e5801f94101156850086c16311cf567b1e7d

---

# 使用 Windows 应用商店提交 API 确认加载项提交




在 Windows 应用商店提交 API 中使用此方法，向 Windows 开发人员中心确认新的或更新的加载项（也称为应用内产品或 IAP）提交。 确认操作向开发人员中心发送提交数据已上传（包括任何相关图标）的警报。 作为响应，开发人员中心确认对提交数据所做的更改以供引入和发布。 确认操作成功后，对提交所做的更改将显示在开发人员中心仪表板中。

有关确认操作如何适用通过使用 Windows 应用商店提交 API 提交加载项过程的详细信息，请参阅[管理加载项提交](manage-add-on-submissions.md)。

## 先决条件

若要使用此方法，首先需要执行以下操作：

* 如果尚未开始操作，请先完成 Windows 应用商店提交 API 的所有[先决条件](create-and-manage-submissions-using-windows-store-services.md#prerequisites)。
* [获取 Azure AD 访问令牌](create-and-manage-submissions-using-windows-store-services.md#obtain-an-azure-ad-access-token)，以供在此方法的请求标头中使用。 获取访问令牌后，在它到期前，你有 60 分钟的使用时间。 该令牌到期后，可以获取新的令牌。
* [创建加载项提交](create-an-add-on-submission.md)，然后通过对提交数据所做的任何必要更改[更新提交](update-an-add-on-submission.md)。

>**注意**&nbsp;&nbsp;此方法只可以用于授予使用 Windows 应用商店提交 API 权限的 Windows 开发人员中心帐户。 并非所有帐户都已启用此权限。

## 请求

此方法具有以下语法。 请参阅以下部分，获取标头和请求正文的使用示例和描述。

| 方法 | 请求 URI                                                      |
|--------|------------------------------------------------------------------|
| POST    | ```https://manage.devcenter.microsoft.com/v1.0/my/inappproducts/{inAppProductId}/submissions/{submissionId}/commit``` |

<span/>
 

### 请求标头

| 标头        | 类型   | 说明                                                                 |
|---------------|--------|-----------------------------------------------------------------------------|
| 授权 | 字符串 | 必需。 Azure AD 访问令牌的格式为 **Bearer** &lt;*token*&gt;。 |

<span/>

### 请求参数

| 名称        | 类型   | 描述                                                                 |
|---------------|--------|-----------------------------------------------------------------------------|
| inAppProductId | 字符串 | 必需。 加载项（包含要确认的提交）的应用商店 ID。 可通过开发人员中心仪表板获取应用商店 ID，它包含在[获取所有加载项](get-all-add-ons.md)和[创建加载项](create-an-add-on.md)请求的响应数据中。 |
| submissionId | 字符串 | 必需。 要确认的提交的 ID。 可通过开发人员中心仪表板获取此 ID，它包含在[创建加载项提交](create-an-add-on-submission.md)请求的响应数据中。  |

<span/>

### 请求正文

请勿为此方法提供请求正文。

### 请求示例

以下示例演示了如何确认加载项提交。

```
POST https://manage.devcenter.microsoft.com/v1.0/my/inappproducts/9NBLGGH4TNMP/submissions/1152921504621230023/commit HTTP/1.1
Authorization: Bearer <your access token>
```

## 响应

以下示例演示了成功调用此方法的 JSON 响应正文。 有关响应正文中这些值的更多详细信息，请参阅以下部分。

```json
{
  "status": "CommitStarted"
}
```

### 响应正文

| 值      | 类型   | 描述                                                                                                                                                                                                                                                                         |
|------------|--------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| status           | 字符串  | 提交的状态。 这可以是以下值之一： <ul><li>None</li><li>Canceled</li><li>PendingCommit</li><li>CommitStarted</li><li>CommitFailed</li><li>PendingPublication</li><li>Publishing</li><li>Published</li><li>PublishFailed</li><li>PreProcessing</li><li>PreProcessingFailed</li><li>Certification</li><li>CertificationFailed</li><li>Release</li><li>ReleaseFailed</li></ul>  |

<span/>

## 错误代码

如果无法成功完成请求，该响应中会包含以下 HTTP 错误代码之一。

| 错误代码 |  描述   |
|--------|------------------|
| 400  | 请求参数无效。 |
| 404  | 找不到指定提交。 |
| 409  | 指定的提交已找到，但在其当前状态下无法确认；或者加载项使用的开发人员中心仪表板功能[当前不受 Windows 应用商店提交 API 支持](create-and-manage-submissions-using-windows-store-services.md#not_supported)。 |

<span/>


## 相关主题

* [使用 Windows 应用商店服务创建和管理提交](create-and-manage-submissions-using-windows-store-services.md)
* [获取加载项提交](get-an-add-on-submission.md)
* [创建加载项提交](create-an-add-on-submission.md)
* [更新加载项提交](update-an-add-on-submission.md)
* [删除加载项提交](delete-an-add-on-submission.md)
* [获取加载项提交的状态](get-status-for-an-add-on-submission.md)



<!--HONumber=Aug16_HO5-->

