---
Description: 你可以通过编程方式将自己的应用的主要磁铁固定到“开始”菜单，就像固定辅助磁贴一样。 而且可以检查它当前是否固定。
title: 主要磁贴 API
label: Primary tile API's
template: detail.hbs
ms.date: 05/19/2017
ms.topic: article
keywords: windows 10，uwp，StartScreenManager，固定主要磁贴，主要磁贴 api, 检查是否固定了磁贴, 动态磁贴
ms.localizationpriority: medium
ms.openlocfilehash: 04d7c66b358a3a465522ad3b56d8ae926358ae57
ms.sourcegitcommit: b034650b684a767274d5d88746faeea373c8e34f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/06/2019
ms.locfileid: "57596192"
---
# <a name="primary-tile-apis"></a>主要磁贴 API
 

使用主要磁贴 API 可以检查你的应用当前是否已固定到“开始”菜单，并请求固定应用的主要磁贴。

> [!IMPORTANT]
> **需要创意者更新**:必须为目标 SDK 版本 15063 和运行生成 15063 或更高版本才能使用 Api 的主磁贴。

> **重要的 API**：[**StartScreenManager 类**](https://docs.microsoft.com/uwp/api/windows.ui.startscreen.startscreenmanager)， [ContainsAppListEntryAsync](https://docs.microsoft.com/uwp/api/windows.ui.startscreen.startscreenmanager#Windows_UI_StartScreen_StartScreenManager_ContainsAppListEntryAsync_Windows_ApplicationModel_Core_AppListEntry_)， [RequestAddAppListEntryAsync](https://docs.microsoft.com/uwp/api/windows.ui.startscreen.startscreenmanager#Windows_UI_StartScreen_StartScreenManager_RequestAddAppListEntryAsync_Windows_ApplicationModel_Core_AppListEntry_)


## <a name="when-to-use-primary-tile-apis"></a>何时使用主要磁贴 API

你尽了很大努力为你的应用的主要磁贴设计出色的体验，现在你有机会要求用户将其固定到“开始”菜单。 但在我们深入探讨代码之前，你在设计体验时需要牢记以下几点：

* **务必**使用明确的“固定动态磁贴”行动号召在应用中制作无干扰并且可轻松消除的 UX。
* **务必**在要求用户固定磁贴前明确解释你的应用的动态磁贴值。
* 如果你的应用的磁贴已经固定或设备不支持，**不要**要求用户固定它（后面有更多信息）。
* **不要**反复要求用户固定你的应用的磁贴（用户可能会生气）。
* 没有显式用户交互或当你的应用最小化/未打开时**不要**调用固定 API。


## <a name="checking-whether-the-apis-exist"></a>检查 API 是否存在

如果你的应用支持较旧的 Windows 10 版本，则需要检查这些主要磁贴 API 是否可用。 可以使用 ApiInformation 执行此操作。 如果主要磁贴 API 不可用，请避免执行任何 API 调用。

```csharp
if (ApiInformation.IsTypePresent("Windows.UI.StartScreen.StartScreenManager"))
{
    // Primary tile API's supported!
}
else
{
    // Older version of Windows, no primary tile API's
}
```


## <a name="check-if-start-supports-your-app"></a>检查“开始”菜单是否支持你的应用

根据当前“开始”菜单以及你的应用类型，将你的应用固定到当前“开始”屏幕可能不受支持。 只有桌面版和移动版支持将主要磁贴固定到“开始”菜单。 因此，在显示任何固定 UI 或执行任何固定代码前，你需要先检查当前“开始”屏幕是否支持你的应用。 如果不支持，则不要提示用户固定磁贴。

```csharp
// Get your own app list entry
// (which is always the first app list entry assuming you are not a multi-app package)
AppListEntry entry = (await Package.Current.GetAppListEntriesAsync())[0];

// Check if Start supports your app
bool isSupported = StartScreenManager.GetDefault().SupportsAppListEntry(entry);
```


## <a name="check-whether-youre-currently-pinned"></a>检查当前是否已固定

要了解你的主要磁贴当前是否已固定到“开始”菜单，可以使用 [ContainsAppListEntryAsync](https://docs.microsoft.com/uwp/api/windows.ui.startscreen.startscreenmanager#Windows_UI_StartScreen_StartScreenManager_ContainsAppListEntryAsync_Windows_ApplicationModel_Core_AppListEntry_)方法。

```csharp
// Get your own app list entry
AppListEntry entry = (await Package.Current.GetAppListEntriesAsync())[0];

// Check if your app is currently pinned
bool isPinned = await StartScreenManager.GetDefault().ContainsAppListEntryAsync(entry);
```


##  <a name="pin-your-primary-tile"></a>固定你的主要磁贴

如果你的主要磁贴当前未固定，并且“开始”菜单支持它，你可以向用户显示提示，告诉他们可以固定你的主要磁贴。

> [!NOTE]
> 你的应用位于前台，而用户有意请求 （例如，用户单击后是为您提示有关固定磁贴） 固定主磁贴之后，才应调用此 API，必须从 UI 线程调用此 API。

如果用户单击你的按钮固定主要磁贴，你应随后调用 [RequestAddAppListEntryAsync](https://docs.microsoft.com/uwp/api/windows.ui.startscreen.startscreenmanager#Windows_UI_StartScreen_StartScreenManager_RequestAddAppListEntryAsync_Windows_ApplicationModel_Core_AppListEntry_) 方法请求将你的磁贴固定到“开始”菜单。 这会显示一个对话框，要求用户确认他们要将你的磁贴固定到“开始”菜单。

这会返回一个布尔值，该值表示你的磁贴现在是否固定到“开始”菜单。 如果你的磁贴已固定，则会立即返回 true，而不向用户显示对话框。 如果用户在对话框中单击“否”或者不支持将你的磁贴固定到“开始”菜单，则会返回 false。 相反，如果用户单击“是”并且磁贴固定，则 API 将返回 True。

```csharp
// Get your own app list entry
AppListEntry entry = (await Package.Current.GetAppListEntriesAsync())[0];

// And pin it to Start
bool isPinned = await StartScreenManager.GetDefault().RequestAddAppListEntryAsync(entry);
```


## <a name="resources"></a>资源

* [GitHub 上的完整代码示例](https://github.com/WindowsNotifications/quickstart-pin-primary-tile)
* [固定到任务栏](../pin-to-taskbar.md)
* [磁贴、锁屏提醒和通知](index.md)
* [自适应磁贴文档](create-adaptive-tiles.md)
