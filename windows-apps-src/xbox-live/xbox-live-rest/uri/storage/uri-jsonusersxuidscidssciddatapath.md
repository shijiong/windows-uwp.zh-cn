---
title: /json/users/xuid({xuid}) /scids/ {scid} /data/ {路径}
assetID: c2745955-5e52-ea2b-7389-cb85202e01c3
permalink: en-us/docs/xboxlive/rest/uri-jsonusersxuidscidssciddatapath.html
author: KevinAsgari
description: " /json/users/xuid({xuid}) /scids/ {scid} /data/ {路径}"
ms.author: kevinasg
ms.date: 20-12-2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: xbox live, xbox, 游戏, uwp, windows 10, xbox one
ms.localizationpriority: medium
ms.openlocfilehash: 1ad40749e2ef4ab19ba8ef181f9f39c1196b4682
ms.sourcegitcommit: 2a63ee6770413bc35ace09b14f56b60007be7433
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/12/2018
ms.locfileid: "3931637"
---
# <a name="jsonusersxuidxuidscidssciddatapath"></a>/json/users/xuid({xuid}) /scids/ {scid} /data/ {路径}
列出了在指定路径的文件信息。 这些 Uri 的域是`titlestorage.xboxlive.com`。
 
  * [URI 参数](#ID4EV)
 
<a id="ID4EV"></a>

 
## <a name="uri-parameters"></a>URI 参数
 
| 参数| 类型| 说明| 
| --- | --- | --- | 
| xuid| 64 位无符号的整数| Xbox 用户 ID (XUID) 的玩家用户发出请求。| 
| scid| guid| 要查找的服务配置 ID。| 
| path| 字符串| 要返回的数据项路径。 获取返回所有匹配的目录和子目录。 有效字符包括大写字母 (A-Z)、 小写字母 (a-z)、 数字 (0-9)、 下划线 (_) 和正斜杠 （/）。 可能为空。 256 的最大长度。| 
  
<a id="ID4EFC"></a>

 
## <a name="valid-methods"></a>有效的方法

[GET](uri-jsonusersxuidscidssciddatapath-get.md)

&nbsp;&nbsp;列出了在指定路径的文件信息。
 
<a id="ID4EPC"></a>

 
## <a name="see-also"></a>另请参阅
 
<a id="ID4ERC"></a>

 
##### <a name="parent"></a>Parent 的子磁盘） 

[标题存储 Uri](atoc-reference-storagev2.md)

   