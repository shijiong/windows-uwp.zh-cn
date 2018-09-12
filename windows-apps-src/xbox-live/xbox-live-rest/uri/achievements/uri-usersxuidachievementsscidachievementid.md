---
title: / 用户/xuid ({xuid}) /achievements/ {scid} / {achievementid}
assetID: 656a6d63-1a11-b0a5-63d2-2b010abd62e7
permalink: en-us/docs/xboxlive/rest/uri-usersxuidachievementsscidachievementid.html
author: KevinAsgari
description: " / 用户/xuid ({xuid}) /achievements/ {scid} / {achievementid}"
ms.author: kevinasg
ms.date: 20-12-2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: xbox live, xbox, 游戏, uwp, windows 10, xbox one
ms.localizationpriority: medium
ms.openlocfilehash: f58b4b5f8cf135aaaad5e23095c4c00278dcec83
ms.sourcegitcommit: 2a63ee6770413bc35ace09b14f56b60007be7433
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/12/2018
ms.locfileid: "3929668"
---
# <a name="usersxuidxuidachievementsscidachievementid"></a>/ 用户/xuid ({xuid}) /achievements/ {scid} / {achievementid}
返回关于该成就，包括其配置的元数据和特定于用户的数据的详细信息。 

> [!NOTE] 
> 仅支持平台。 

 
这些 Uri 的域是`achievements.xboxlive.com`。
 
  * [URI 参数](#ID4E2)
 
<a id="ID4E2"></a>

 
## <a name="uri-parameters"></a>URI 参数
 
| 参数| 类型| 说明| 
| --- | --- | --- | --- | 
| xuid| 64 位无符号的整数| Xbox 用户 ID (XUID) 在访问其资源的用户。 必须匹配的身份验证的用户的 XUID。| 
| scid| GUID| 正在访问其成就的服务配置的唯一标识符。| 
| achievementid| 32 位无符号的整数| 正在访问的成就的 （中指定的 SCID) 的唯一标识符。| 
  
<a id="ID4EMC"></a>

 
## <a name="valid-methods"></a>有效的方法

[获取 (/users/xuid({xuid})/achievements/{scid}/{achievementid})](uri-usersxuidachievementsscidachievementidget.md)

&nbsp;&nbsp;获取在成就的详细信息。
 
<a id="ID4EWC"></a>

 
## <a name="see-also"></a>另请参阅
 
<a id="ID4EYC"></a>

 
##### <a name="parent"></a>Parent 的子磁盘） 

[成就 Uri](atoc-reference-achievementsv2.md)

   