---
Description: 当用户移动对象时，使用拖放动画，例如在列表中移动项目，或将项目放在其他列表顶部。
title: 在 UWP 应用中拖动动画
ms.assetid: 6064755F-6E24-4901-A4FF-263F05F0DFD6
label: Motion--Drag and drop
template: detail.hbs
ms.date: 05/19/2017
ms.topic: article
keywords: windows 10, uwp
ms.localizationpriority: medium
ms.openlocfilehash: d4aa6b0b1a7d0e4d805e43ba308730ee483927aa
ms.sourcegitcommit: 6f32604876ed480e8238c86101366a8d106c7d4e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/21/2019
ms.locfileid: "67320903"
---
# <a name="drag-animations"></a>拖动动画




当用户移动对象时，使用拖放动画，例如在列表中移动项目，或将项目放在其他列表顶部。

> **重要的 API**：[**DragItemThemeAnimation 类**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.media.animation.dragitemthemeanimation)


## <a name="dos-and-donts"></a>应做事项和禁止事项


**拖动启动动画**

-   在用户开始移动对象时使用拖动开始动画。
-   当且仅当有其他对象可能受到拖放操作影响时，才在动画中包括这些受影响的对象。
-   使用拖动结束动画可完成以拖动开始动画开始的任何动画序列。 它将恢复由拖动开始动画引起的拖动对象的大小更改。

**拖动结束动画**

-   在用户放下拖动的对象时使用拖动结束动画。
-   将拖动结束动画与列表的添加和删除动画结合使用。
-   当且仅当拖动开始动画中包括了受影响的对象时，才应在拖动结束动画中包括这些受影响的对象。
-   如果没有首先使用拖动开始动画，则不要使用拖动结束动画。 你需要使用这两个动画，才能在完成拖动序列之后，让对象还原为其原始大小。

**拖动之间输入动画**

-   当用户将拖动源拖入可以放在两个其他对象之间的放置区域时，使用在进入间拖动动画。
-   选择一个合理的目标拖放区域。 此区域不应该太小，否则用户难以放置拖放源。
-   移动受影响的对象以显示放置区域的建议方向是直接相互分开。 垂直移动还是水平移动取决于受影响的对象彼此的方向。
-   如果拖放源无法放入某个区域，请不要使用在进入间拖动动画。 在进入间拖动动画告诉用户可以将拖动源放入受影响的对象之间。

**保留动画之间拖动**

-   当用户将对象从放置它的两个其他对象之间的区域拖开时，使用在离开间拖动动画。
-   如果没有首先使用在进入间拖动动画，则不要使用在离开间拖动动画。


## <a name="related-articles"></a>相关文章

**面向开发人员**
* [动画概述](https://docs.microsoft.com/windows/uwp/graphics/animations-overview)
* [拖放序列进行动画处理](https://docs.microsoft.com/previous-versions/windows/apps/jj649427(v=win.10))
* [快速入门：对 UI 使用库动画进行动画处理](https://docs.microsoft.com/previous-versions/windows/apps/hh452703(v=win.10))
* [**DragItemThemeAnimation 类**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.media.animation.dragitemthemeanimation)
* [**DropTargetItemThemeAnimation 类**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.media.animation.droptargetitemthemeanimation)
* [**DragOverThemeAnimation 类**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.media.animation.dragoverthemeanimation)


 




