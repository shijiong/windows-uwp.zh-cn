---
author: serenaz
Description: A button gives the user a way to trigger an immediate action.
title: 按钮
label: Buttons
template: detail.hbs
ms.author: sezhen
ms.date: 05/19/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows 10, uwp
ms.assetid: f04d1a3c-7dcd-4bc8-9586-3396923b312e
pm-contact: kisai
design-contact: kimsea
dev-contact: mitra
doc-status: Published
ms.localizationpriority: medium
ms.openlocfilehash: f0bf7731a8480fb4f6d81368227ad6259780381b
ms.sourcegitcommit: 753dfcd0f9fdfc963579dd0b217b445c4b110a18
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/27/2018
ms.locfileid: "2860479"
---
# <a name="buttons"></a>按钮

> [!IMPORTANT]
> 本文介绍的功能尚未发布，在商业发行之前可能发生实质性修改。 Microsoft 对于此处提供的信息不作任何明示或默示的担保。 预览功能需要的[最新的 Windows 10 内幕预览版和 SDK](https://insider.windows.com/for-developers/)或[Windows 用户界面库](https://docs.microsoft.com/uwp/toolkits/winui/)。

按钮为用户提供了触发即时操作的方法。 某些按钮都专用于特定任务，如导航、 重复的操作或演示菜单。

![按钮示例](images/controls/button.png)

XAML 框架提供的标准按钮控件，以及几个专用的按钮控件。

控件 | 描述
------- | -----------
[按钮](/uwp/api/windows.ui.xaml.controls.button) | 启动即时操作。 可用于 Click 事件或命令绑定。
[RepeatButton](/uwp/api/windows.ui.xaml.controls.primitives.repeatbutton) | 引发一个单击事件连续按下时按钮。
[HyperlinkButton](/uwp/api/windows.ui.xaml.controls.hyperlinkbutton) | 一个按钮的样式类似的超链接，用于导航。 有关详细信息，请参阅[超链接](hyperlinks.md)。
[DropDownButton](/uwp/api/windows.ui.xaml.controls.dropdownbutton) | （预览）具有下方的 v 形以打开附加的弹出的按钮。
[拆分按钮](/uwp/api/windows.ui.xaml.controls.splitbutton) | （预览）具有两个方面的按钮。 一方启动某项操作，并另一侧打开菜单。
[ToggleSplitButton](/uwp/api/windows.ui.xaml.controls.togglesplitbutton) | （预览）具有两个方面的切换按钮。 切换/关闭的一侧，另一侧打开菜单。

| **获取 Windows UI 库** |
| - |
| DropDownButton、 拆分按钮和 ToggleSplitButton 是作为 Windows UI 库，NuGet 程序包包含新控件和 UWP 应用程序的 UI 功能的一部分包含。 有关详细信息，包括安装说明，请参阅[Windows UI 库概述](https://docs.microsoft.com/uwp/toolkits/winui/)。 |

| **平台 Api** | **Windows UI 库 Api** |
| - | - |
| [单击事件](/uwp/api/windows.ui.xaml.controls.primitives.buttonbase.click)， [Command 属性](/uwp/api/windows.ui.xaml.controls.primitives.buttonbase.command) | [DropDownButton 类](/uwp/api/microsoft.ui.xaml.controls.dropdownbutton)， [SplitButton 类](/uwp/api/microsoft.ui.xaml.controls.splitbutton)， [ToggleSplitButton 类](/uwp/api/microsoft.ui.xaml.controls.togglesplitbutton) |

## <a name="is-this-the-right-control"></a>这是正确的控件吗？

使用**按钮**，使用户可以启动即时操作，如提交表单。

导航到另一页; 操作时不使用按钮请改用[超链接按钮](/uwp/api/windows.ui.xaml.controls.hyperlinkbutton)。 有关详细信息，请参阅[超链接](hyperlinks.md)。
> 例外：对于向导导航，请使用标记为“上一步”和“下一步”的按钮。 对于其他类型的向后导航或导航到较高的级别，使用[后退按钮](../basics/navigation-history-and-backwards-navigation.md)。

用户可能想要重复触发操作时，请使用**RepeatButton** 。 例如，使用 RepeatButton 增加或减少计数器中的值。

在按钮获得包含更多选项的弹出窗口时，请使用**DropDownButton** 。 默认下方的 v 形提供直观的指示按钮，包括弹出。

当您希望用户能够启动即时操作或独立选择其他选项，请使用**拆分按钮**。

## <a name="examples"></a>示例

<table>
<th align="left">XAML 控件库<th>
<tr>
<td><img src="images/xaml-controls-gallery-sm.png" alt="XAML controls gallery"></img></td>
<td>
    <p>如果已安装 <strong style="font-weight: semi-bold">XAML 控件库</strong>应用，请单击此处<a href="xamlcontrolsgallery:/item/Button">打开此应用，了解 Button 的实际应用</a>。</p>
    <ul>
    <li><a href="https://www.microsoft.com/store/productId/9MSVH128X2ZT">获取 XAML 控件库应用 (Microsoft Store)</a></li>
    <li><a href="https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/XamlUIBasics">获取源代码 (GitHub)</a></li>
    </ul>
</td>
</tr>
</table>

此示例在请求位置访问权限的对话框中使用两个按钮，即 Allow 和 Block。

![在对话框中使用的按钮示例](images/dialogs/dialog_RS2_two_button.png)

## <a name="create-a-button"></a>创建按钮

此示例显示一个响应单击操作的按钮。

在 XAML 中创建按钮。

```xaml
<Button Content="Subscribe" Click="SubscribeButton_Click"/>
```

或在代码中创建按钮。

```csharp
Button subscribeButton = new Button();
subscribeButton.Content = "Subscribe";
subscribeButton.Click += SubscribeButton_Click;

// Add the button to a parent container in the visual tree.
stackPanel1.Children.Add(subscribeButton);
```

处理 Click 事件。

```csharp
private async void SubscribeButton_Click(object sender, RoutedEventArgs e)
{
    // Call app specific code to subscribe to the service. For example:
    ContentDialog subscribeDialog = new ContentDialog
    {
        Title = "Subscribe to App Service?",
        Content = "Listen, watch, and play in high definition for only $9.99/month. Free to try, cancel anytime.",
        CloseButtonText = "Not Now",
        PrimaryButtonText = "Subscribe",
        SecondaryButtonText = "Try it"
    };

    ContentDialogResult result = await subscribeDialog.ShowAsync();
}
```

### <a name="button-interaction"></a>按钮交互

当你用手指或触笔点击某个按钮或在指针位于其上时按鼠标左键时，按钮会引发 [Click](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.primitives.buttonbase.click.aspx) 事件。 如果按钮具有键盘焦点，则按 Enter 键或空格键也会引发 Click 事件。

你通常无法处理按钮上的低级别 [PointerPressed](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.uielement.pointerpressed.aspx) 事件，因为它具有 Click 行为。 有关详细信息，请参阅[事件和路由事件概述](https://msdn.microsoft.com/library/windows/apps/mt185584.aspx)。

你可以通过更改 [ClickMode](https://docs.microsoft.com/en-us/uwp/api/windows.ui.xaml.controls.clickmode) 属性来更改按钮引发 Click 事件的方式。 ClickMode 默认值为 **Release**，但你也可以将按钮的 ClickMode 设置为 **Hover** 或 **Press**。 如果 ClickMode 为 **Hover**，则无法通过键盘或触摸引发 Click 事件。


### <a name="button-content"></a>按钮内容

按钮是 [ContentControl](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.contentcontrol.aspx)。 它的 XAML 内容属性为 [Content](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.contentcontrol.content.aspx)，这对于 XAML 支持如下所示的语法：`<Button>A button's content</Button>`。 可以将任何对象设置为按钮的内容。 如果内容是一个 [UIElement](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.uielement.aspx)，则会在按钮中呈现它。 如果该内容是另一种类型的对象，则会在按钮中显示其字符串表示形式。

按钮内容通常为文本。 下面是对具有文本内容的按钮的设计建议：
-   使用简洁具体而又明晰易懂的文本来清楚地描述按钮可以执行的操作。 通常，按钮文本内容是一个字词（动词）。
-   请使用默认字体，除非你的品牌指南告诉你使用不同的字体。
-   对于较短的文本，通过使用最小按钮宽度 120px 避免命令按钮过窄。
- 对于较长的文本，通过将文本最大长度限制为 26 个字符避免命令按钮过宽。
-   如果按钮的文本内容是动态的（例如，它已[本地化](../globalizing/globalizing-portal.md)），应考虑按钮大小将如何调整以及其周围控件将有哪些影响。

<table>
<tr>
<td> <b>需要修复：</b><br> 具有溢出文本的按钮。 </td>
<td> <img src="images/button-wraptext.png"/> </td>
</tr>
<tr>
<td> <b>选项 1：</b><br> 如果文本长度大于 26 个字符，请增加按钮宽度、堆叠按钮和换行。 </td>
<td> <img src="images/button-wraptext1.png"> </td>
</tr>
<tr>
<td> <b>选项 2：</b><br> 增加按钮高度并对文本换行。 </td>
<td> <img src="images/button-wraptext2.png"> </td>
</tr>
</table>

你还可以自定义构成按钮外观的视觉效果。 例如，可以将文本替换为图标，或使用图标加文本。

在这里，我们将一个包含图像和文本的 **StackPanel** 设置为按钮内容。

```xaml
<Button Click="Button_Click"
        Background="LightGray"
        Height="100" Width="80">
    <StackPanel>
        <Image Source="Assets/Photo.png" Height="62"/>
        <TextBlock Text="Photos" Foreground="Black"
                   HorizontalAlignment="Center"/>
    </StackPanel>
</Button>
```

按钮如下所示。

![包含图像和文本内容的按钮](images/button-orange.png)

## <a name="create-a-repeat-button"></a>创建重复按钮

[RepeatButton](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.primitives.repeatbutton.aspx) 是一个从按下到释放为止重复引发 [Click](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.primitives.buttonbase.click.aspx) 事件的按钮。 设置 [Delay](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.primitives.repeatbutton.delay.aspx) 属性来指定 RepeatButton 在其被按下后和开始重复单击操作之间等待的时间。 设置 [Interval](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.primitives.repeatbutton.interval.aspx) 属性来指定重复单击操作之间的时间。 两个属性的时间都以毫秒为单位指定。

以下示例显示两个 RepeatButton 控件，两者各自的 Click 事件用于增加和减少文本块中显示的值。

```xaml
<StackPanel>
    <RepeatButton Width="100" Delay="500" Interval="100" Click="Increase_Click">Increase</RepeatButton>
    <RepeatButton Width="100" Delay="500" Interval="100" Click="Decrease_Click">Decrease</RepeatButton>
    <TextBlock x:Name="clickTextBlock" Text="Number of Clicks:" />
</StackPanel>
```

```csharp
private static int _clicks = 0;
private void Increase_Click(object sender, RoutedEventArgs e)
{
    _clicks += 1;
    clickTextBlock.Text = "Number of Clicks: " + _clicks;
}

private void Decrease_Click(object sender, RoutedEventArgs e)
{
    if(_clicks > 0)
    {
        _clicks -= 1;
        clickTextBlock.Text = "Number of Clicks: " + _clicks;
    }
}
```

## <a name="create-a-drop-down-button"></a>创建一个下拉按钮

> **预览**： DropDownButton 需要[最新的 Windows 10 内幕预览版和 SDK](https://insider.windows.com/for-developers/)或[Windows 用户界面库](https://docs.microsoft.com/uwp/toolkits/winui/)。

[DropDownButton](/uwp/api/windows.ui.xaml.controls.dropdownbutton)是显示下方的 v 形为可视的指示它具有包含更多选项附加的弹出一个按钮。 它具有相同的行为与弹出; 标准按钮仅不同外观。

下拉按钮继承 Click 事件，但您通常不使用它。 相反，您可以使用弹出属性附加弹出和调用操作使用中弹出菜单选项。 单击该按钮时，此弹出窗口将自动打开。

> [!TIP]
> 有关弹出项目的详细信息，请参阅[菜单和上下文菜单](menus.md)。

### <a name="example---drop-down-button"></a>示例-下拉按钮

本示例显示如何使用包含 RichEditBox 中的段落对齐方式的命令弹出创建下拉按钮。 （有关详细信息和代码，请参阅[富编辑框](rich-edit-box.md)）。

![下拉列表具有对齐命令按钮](images/drop-down-button-align.png)

```xaml
<DropDownButton ToolTipService.ToolTip="Alignment">
    <TextBlock FontFamily="Segoe MDL2 Assets" FontSize="16" Text="&#xE8E4;"/>
    <DropDownButton.Flyout>
        <MenuFlyout Placement="BottomEdgeAlignedLeft">
            <MenuFlyoutItem Text="Left" Icon="AlignLeft" Tag="left"
                            Click="AlignmentMenuFlyoutItem_Click"/>
            <MenuFlyoutItem Text="Center" Icon="AlignCenter" Tag="center"
                            Click="AlignmentMenuFlyoutItem_Click"/>
            <MenuFlyoutItem Text="Right" Icon="AlignRight" Tag="right"
                            Click="AlignmentMenuFlyoutItem_Click"/>
        </MenuFlyout>
    </DropDownButton.Flyout>
</DropDownButton>
```

```csharp
private void AlignmentMenuFlyoutItem_Click(object sender, RoutedEventArgs e)
{
    var option = ((MenuFlyoutItem)sender).Tag.ToString();

    Windows.UI.Text.ITextSelection selectedText = editor.Document.Selection;
    if (selectedText != null)
    {
        // Apply the alignment to the selected paragraphs.
        var paragraphFormatting = selectedText.ParagraphFormat;
        if (option == "left")
        {
            paragraphFormatting.Alignment = Windows.UI.Text.ParagraphAlignment.Left;
        }
        else if (option == "center")
        {
            paragraphFormatting.Alignment = Windows.UI.Text.ParagraphAlignment.Center;
        }
        else if (option == "right")
        {
            paragraphFormatting.Alignment = Windows.UI.Text.ParagraphAlignment.Right;
        }
    }
}
```

## <a name="create-a-split-button"></a>创建的拆分按钮

> **预览**： SplitButton 需要[最新的 Windows 10 内幕预览版和 SDK](https://insider.windows.com/for-developers/)或[Windows 用户界面库](https://docs.microsoft.com/uwp/toolkits/winui/)。

[SplitButton](/uwp/api/windows.ui.xaml.controls.splitbutton)有两个部分，可以分别调用。 一个部件的行为类似于标准的按钮，调用即时操作。 其他部件调用包含用户可以从选择的其他选项的弹出窗口。

> [!NOTE]
> 当调用与触摸，拆分按钮的行为如下下拉按钮;按钮的两个部分调用弹出。 输入其他方法，用户可以分别调用该按钮任一半部分。

拆分按钮的典型行为是：

- 当用户单击按钮部件时，处理要调用下拉列表中当前所选的选项的 Click 事件。
- 打开下拉列表时，该选项下这两个更改下拉列表中项的句柄调用处于选中状态，然后调用。 非常重要调用弹出项，因为按钮单击事件不会发生时使用触摸。

> [!TIP]
> 有多种方法放下下拉列表中的项目和处理其调用。 如果您使用的列表视图或 GridView，一种方法是用来处理 SelectionChanged 事件。 如果您执行此操作，将[SingleSelectionFollowsFocus](/uwp/api/windows.ui.xaml.controls.listviewbase.singleselectionfollowsfocus)设置为**false**。 这允许用户浏览而无需调用每次更改的项目中使用键盘的选项。

### <a name="example---split-button"></a>示例-拆分按钮

本示例演示如何创建用于更改 RichEditBox 中选定文本的前景色的拆分按钮。 （有关详细信息和代码，请参阅[富编辑框](rich-edit-box.md)）。

![用于选择前景色的拆分按钮](images/split-button-rtb.png)

```xaml
<SplitButton ToolTipService.ToolTip="Foreground color"
             Click="BrushButtonClick">
    <Border x:Name="SelectedColorBorder" Width="20" Height="20"/>
    <SplitButton.Flyout>
        <Flyout x:Name="BrushFlyout" Placement="BottomEdgeAlignedLeft">
            <!-- Set SingleSelectionFollowsFocus="False"
                 so that keyboard navigation works correctly. -->
            <GridView ItemsSource="{x:Bind ColorOptions}" 
                      SelectionChanged="BrushSelectionChanged"
                      SingleSelectionFollowsFocus="False"
                      SelectedIndex="0" Padding="0">
                <GridView.ItemTemplate>
                    <DataTemplate>
                        <Rectangle Fill="{Binding}" Width="20" Height="20"/>
                    </DataTemplate>
                </GridView.ItemTemplate>
                <GridView.ItemContainerStyle>
                    <Style TargetType="GridViewItem">
                        <Setter Property="Margin" Value="2"/>
                        <Setter Property="MinWidth" Value="0"/>
                        <Setter Property="MinHeight" Value="0"/>
                    </Style>
                </GridView.ItemContainerStyle>
            </GridView>
        </Flyout>
    </SplitButton.Flyout>
</SplitButton>
```

```csharp
public sealed partial class MainPage : Page
{
    // Color options that are bound to the grid in the split button flyout.
    private List<SolidColorBrush> ColorOptions = new List<SolidColorBrush>();
    private SolidColorBrush CurrentColorBrush = null;

    public MainPage()
    {
        this.InitializeComponent();

        // Add color brushes to the collection.
        ColorOptions.Add(new SolidColorBrush(Colors.Black));
        ColorOptions.Add(new SolidColorBrush(Colors.Red));
        ColorOptions.Add(new SolidColorBrush(Colors.Orange));
        ColorOptions.Add(new SolidColorBrush(Colors.Yellow));
        ColorOptions.Add(new SolidColorBrush(Colors.Green));
        ColorOptions.Add(new SolidColorBrush(Colors.Blue));
        ColorOptions.Add(new SolidColorBrush(Colors.Indigo));
        ColorOptions.Add(new SolidColorBrush(Colors.Violet));
        ColorOptions.Add(new SolidColorBrush(Colors.White));
    }

    private void BrushButtonClick(object sender, object e)
    {
        // When the button part of the split button is clicked,
        // apply the selected color.
        ChangeColor();
    }

    private void BrushSelectionChanged(object sender, SelectionChangedEventArgs e)
    {
        // When the flyout part of the split button is opened and the user selects
        // an option, set their choice as the current color, apply it, then close the flyout.
        CurrentColorBrush = (SolidColorBrush)e.AddedItems[0];
        SelectedColorBorder.Background = CurrentColorBrush;
        ChangeColor();
        BrushFlyout.Hide();
    }

    private void ChangeColor()
    {
        // Apply the color to the selected text in a RichEditBox.
        Windows.UI.Text.ITextSelection selectedText = editor.Document.Selection;
        if (selectedText != null)
        {
            Windows.UI.Text.ITextCharacterFormat charFormatting = selectedText.CharacterFormat;
            charFormatting.ForegroundColor = CurrentColorBrush.Color;
            selectedText.CharacterFormat = charFormatting;
        }
    }
}
```

## <a name="create-a-toggle-split-button"></a>创建切换拆分按钮

> **预览**： ToggleSplitButton 需要[最新的 Windows 10 内幕预览版和 SDK](https://insider.windows.com/for-developers/)或[Windows 用户界面库](https://docs.microsoft.com/uwp/toolkits/winui/)。

[ToggleSplitButton](/uwp/api/windows.ui.xaml.controls.togglesplitbutton)有两个部分，可以分别调用。 一个部件与切换按钮可打开或关闭的相似之处。 其他部件调用包含用户可以从选择的其他选项的弹出窗口。

启用或禁用功能时为功能的用户可以从选择的多个选项通常用于切换拆分按钮。 例如，在文档编辑器中，它无法用于打开列表，或关闭，同时使用下拉列表选择列表的样式。

> [!NOTE]
> 当调用与触摸，拆分按钮的行为如下下拉按钮。 输入其他方法，用户可以分别调用该按钮任一半部分。 与 touch 按钮的两个部分调用弹出。 因此，您必须在弹出内容以打开或关闭切换按钮中包含的选项。

### <a name="differences-with-togglebutton"></a>使用切换按钮的差异

与[ToggleButton](/uwp/api/windows.ui.xaml.controls.primitives.togglebutton)，不同 ToggleSplitButton 没有确定状态。 因此，您应记住这些差异：

- ToggleSplitButton 没有**IsThreeState**属性或**不确定**事件。
- [ToggleSplitButton.IsChecked](/uwp/api/windows.ui.xaml.controls.togglesplitbutton.ischecked)属性是只需一个**bool**，不**为 null 的布尔值**。
- ToggleSplitButton 具有仅[IsCheckedChanged](/uwp/api/windows.ui.xaml.controls.togglesplitbutton.ischeckedchanged)事件;它不具有单独的**选项处于选中状态**和**未选中**事件。

### <a name="example---toggle-split-button"></a>示例-切换拆分按钮

下面的示例演示如何拆分按钮切换可用于打开列表格式打开或关闭，并更改的列表，RichEditBox 中的样式。 （有关详细信息和代码，请参阅[富编辑框](rich-edit-box.md)）。

![用于选择列表样式切换拆分按钮](images/toggle-split-button-open.png)

```xaml
<ToggleSplitButton x:Name="ListButton"
                   ToolTipService.ToolTip="List style"
                   Click="ListButton_Click"
                   IsCheckedChanged="ListStyleButton_IsCheckedChanged">
    <TextBlock FontFamily="Segoe MDL2 Assets" FontSize="16" Text="&#xE8FD;"/>
    <ToggleSplitButton.Flyout>
        <Flyout Placement="BottomEdgeAlignedLeft">
            <ListView x:Name="ListStylesListView"
                      SelectionChanged="ListStylesListView_SelectionChanged" 
                      SingleSelectionFollowsFocus="False">
                <StackPanel Tag="bullet" Orientation="Horizontal">
                    <FontIcon FontFamily="Segoe MDL2 Assets" Glyph="&#xE7C8;"/>
                    <TextBlock Text="Bullet" Margin="8,0"/>
                </StackPanel>
                <StackPanel Tag="alpha" Orientation="Horizontal">
                    <TextBlock Text="A" FontSize="24" Margin="2,0"/>
                    <TextBlock Text="Alpha" Margin="8"/>
                </StackPanel>
                <StackPanel Tag="numeric" Orientation="Horizontal">
                    <FontIcon FontFamily="Segoe MDL2 Assets" Glyph="&#xF146;"/>
                    <TextBlock Text="Numeric" Margin="8,0"/>
                </StackPanel>
                <TextBlock Tag="none" Text="None" Margin="28,0"/>
            </ListView>
        </Flyout>
    </ToggleSplitButton.Flyout>
</ToggleSplitButton>
```

```csharp
private void ListStyleButton_IsCheckedChanged(ToggleSplitButton sender, ToggleSplitButtonIsCheckedChangedEventArgs args)
{
    // Use the toggle button to turn the selected list style on or off.
    if (((ToggleSplitButton)sender).IsChecked == true)
    {
        // On. Apply the list style selected in the drop down to the selected text.
        var listStyle = ((FrameworkElement)(ListStylesListView.SelectedItem)).Tag.ToString();
        ApplyListStyle(listStyle);
    }
    else
    {
        // Off. Make the selected text not a list,
        // but don't change the list style selected in the drop down.
        ApplyListStyle("none");
    }
}

private void ListStylesListView_SelectionChanged(object sender, SelectionChangedEventArgs e)
{
    var listStyle = ((FrameworkElement)(e.AddedItems[0])).Tag.ToString();

    if (ListButton.IsChecked == true)
    {
        // Toggle button is on. Turn it off...
        if (listStyle == "none")
        {
            ListButton.IsChecked = false;
        }
        else
        {
            // or apply the new selection.
            ApplyListStyle(listStyle);
        }
    }
    else
    {
        // Toggle button is off. Turn it on, which will apply the selection
        // in the IsCheckedChanged event handler.
        ListButton.IsChecked = true;
    }
}

private void ApplyListStyle(string listStyle)
{
    Windows.UI.Text.ITextSelection selectedText = editor.Document.Selection;
    if (selectedText != null)
    {
        // Apply the list style to the selected text.
        var paragraphFormatting = selectedText.ParagraphFormat;
        if (listStyle == "none")
        {  
            paragraphFormatting.ListType = Windows.UI.Text.MarkerType.None;
        }
        else if (listStyle == "bullet")
        {
            paragraphFormatting.ListType = Windows.UI.Text.MarkerType.Bullet;
        }
        else if (listStyle == "numeric")
        {
            paragraphFormatting.ListType = Windows.UI.Text.MarkerType.Arabic;
        }
        else if (listStyle == "alpha")
        {
            paragraphFormatting.ListType = Windows.UI.Text.MarkerType.UppercaseEnglishLetter;
        }
        selectedText.ParagraphFormat = paragraphFormatting;
    }
}
```

## <a name="recommendations"></a>建议

- 请确保用户清楚地了解按钮的目的和状态。
- 有多个按钮用于相同决策时（例如，在确认对话框中），请按以下顺序显示提交按钮，其中，[执行]和[不执行]是对主要说明的具体响应：
    - 确定/[执行]/是
    - [不执行]/否
    - 取消
- 一次仅向用户显示一两个按钮，例如，“接受”和“取消”。 如果你需要为用户显示更多操作，请考虑使用用户可从中选择操作的[复选框](checkbox.md)或[单选按钮](radio-button.md)，并通过一个命令按钮来触发这些操作。
- 对于需要在应用的多个页面上提供的操作，请考虑使用[底部应用栏](app-bars.md)，而不要在多个页面上重复设置按钮。

### <a name="recommended-single-button-layout"></a>推荐单按钮布局

如果布局只需一个按钮，则它应基于其容器上下文进行左对齐或右对齐。

- 只有一个按钮的对话框应使按钮**右对齐**。 如果对话框只包含一个按钮，请确保该按钮执行安全、无破坏性的操作。 如果使用 [ContentDialog](dialogs.md) 并指定单个按钮，则它会自动右对齐。

![对话框中的按钮](images/pushbutton_doc_dialog.png)

- 如果按钮出现在容器 UI 中（例如，在 toast 通知、浮出控件或列表视图项目中），则应在容器中使按钮**右对齐**。

![容器中的按钮](images/pushbutton_doc_container.png)

- 在包含单个按钮的页面中（例如，处于设置页面底部的“应用”按钮），应使按钮**左对齐**。 这会确保按钮与页面内容的其余部分对齐。

![页面上的按钮](images/pushbutton_doc_page.png)

## <a name="back-buttons"></a>后退按钮

后退按钮是一种系统提供的 UI 元素，可支持在后退堆栈或用户导航历史记录中向后导航。 你无需创建自己的后退按钮，但可能必须进行一些工作才能支持良好的后退导航体验。 有关详细信息，请参阅 [历史记录和向后导航](../basics/navigation-history-and-backwards-navigation.md)

## <a name="get-the-sample-code"></a>获取示例代码

- [XAML 控件库示例](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/XamlUIBasics) - 以交互式格式查看所有 XAML 控件。

## <a name="related-articles"></a>相关文章

- [Button 类](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.button.aspx)
- [单选按钮](radio-button.md)
- [复选框](checkbox.md)
- [切换开关](toggles.md)