---
title: 用户 (JSON)
assetID: dbc733e4-0348-0e3d-1f55-17b465e599d6
permalink: en-us/docs/xboxlive/rest/json-user.html
author: KevinAsgari
description: " 用户 (JSON)"
ms.author: kevinasg
ms.date: 20-12-2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: xbox live, xbox, 游戏, uwp, windows 10, xbox one
ms.localizationpriority: medium
ms.openlocfilehash: 7070d829000821cb48d8fcbaa4fde1d6f393b16a
ms.sourcegitcommit: 2a63ee6770413bc35ace09b14f56b60007be7433
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/12/2018
ms.locfileid: "3928500"
---
# <a name="user-json"></a>用户 (JSON)
包含用户排行榜数据。 
<a id="ID4EN"></a>

 
## <a name="user"></a>用户
 
用户对象具有以下规范。
 
| 成员| 类型| 说明| 
| --- | --- | --- | 
| 玩家代号| 字符串| （最多 15 个字符） 的玩家的玩家代号。 在确定玩家时，客户端应在 UI 中使用此值。| 
| 排名| 32 位有符号的整数| 对相对于请求排行榜数据的用户的用户进行分级。| 
| rating| 字符串| 该用户的评分。| 
| xuid| 64 位无符号的整数| Xbox 用户 ID (XUID) 的用户。| 
  
<a id="ID4EMC"></a>

 
## <a name="sample-json-syntax"></a>JSON 语法示例
 

```json
{ 
   "gamertag":"TrueBlue402",
   "rank":2,
   "rating":"2:19:21.17",
   "xuid":1234567890123456 
}
    
```

  
<a id="ID4EVC"></a>

 
## <a name="see-also"></a>另请参阅
 
<a id="ID4EXC"></a>

 
##### <a name="parent"></a>Parent 的子磁盘） 

[JavaScript 对象表示法 (JSON) 对象引用](atoc-xboxlivews-reference-json.md)

   