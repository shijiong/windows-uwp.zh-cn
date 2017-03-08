---
title: "可用于流式资源的地址空间"
description: "本部分指定了可用于流式资源的虚拟地址空间。"
ms.assetid: 145EB4A3-3910-4126-BC7E-A4CF53E2A098
keywords:
- "可用于流式资源的地址空间"
author: PeterTurcan
ms.author: pettur
ms.date: 02/08/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
translationtype: Human Translation
ms.sourcegitcommit: c6b64cff1bbebc8ba69bc6e03d34b69f85e798fc
ms.openlocfilehash: c120e79518abfed35cbb6b0da6fc659b13602a3f
ms.lasthandoff: 02/07/2017

---

# <a name="address-space-available-for-streaming-resources"></a>可用于流式资源的地址空间


本部分指定了可用于流式资源的虚拟地址空间。

在 64 位操作系统上，至少要有 40 位的虚拟地址空间 (1TB)。

对于 32 位操作系统，地址空间是 32 位 (4 GB)。 对于 32 位 ARM 系统，如果分配使用超过 27 位的地址空间 (128 MB)，创建单个流式资源可能会失败。 这包括地址空间中的任意隐藏填充，硬件可能将其用于 mipmap、打包的磁贴填充并可能将表面尺寸填充至 2 的幂。

在图形处理单元 (GPU) 具有单独页表的图形系统中，大部分此地址空间可用于由应用程序生成的 GPU 资源，尽管由显示驱动程序分配的 GPU 适合于相同的空间。

在具有在 CPU 和 GPU 之间共享页表的未来系统中，可用地址空间可在进程中的所有 CPU 和 GPU 分配之间共享。

## <a name="span-idrelated-topicsspanrelated-topics"></a><span id="related-topics"></span>相关主题


[流式资源创建参数](streaming-resource-creation-parameters.md)

 

 




