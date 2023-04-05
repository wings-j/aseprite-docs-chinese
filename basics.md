# 基础

在这里，您可以了解 Aseprite 背后的基本原则。

在 Aseprite 中，[精灵](sprite.md)由一系列帧和堆叠的图层组成。帧和图层的交集创造了一组可编辑的图形[赛璐珞](cel.md)，其图像或者像素可以使用精灵编辑器进行[编辑](drawing.md)。图层、帧和赛璐珞在[时间轴](timeline.md)中都是可见的：

![时间轴概述](sprite/sprite-components.png)

## 精灵的基本元素

帧是精灵中的单个静止图像，添加和更改帧所创建的图像序列称为[动画](animation.md)。Aseprite 如何循环帧，在[动画章节](animation.md)中有更详细的描述。帧在时间轴从左到右水平排列。

每个帧的图像都是由一个或多个[图层](layers.md)的堆叠而成的，在时间轴中以从底到顶的顺序表示。时间轴底部的图层先绘制，然后每个后续图层将添加到其顶部。图层通过划分单个复杂图像为单独的图形组件，来帮助你绘画。

每个帧和图层交集称为[赛璐珞](cel.md)。任何特定赛璐珞的内容都可以移动、编辑和删除，且不会影响其它赛璐珞。这使它们成为隔离和编辑图形的特定元素同时保留不更改的部分的理想方法。

## 工作流

基本[工作流](workflow.md)：

- 从*文件 > 新建*菜单[创建一个新精灵](new-sprite.md)。
- 点击<kbd>左键</kbd>或者<kbd>右键</kbd>，使用铅笔工具[绘图](drawing.md)![铅笔工具图标](tools/pencil-tool.png), 点击相同的按钮从[颜色条](color-bar.md)选择颜色。
- 使用*File > Save*菜单[保存工作](save.md)为
  `.ase` 文件，保留所有图像信息（图层，帧等等，还有当前[工作空间](workspace.md)设置）。
- [导出精灵](exporting.md)为`.gif`文件，发布图片到网站；导出为一系列单独的`.png`文件（1 个文件表示 1 帧）；导出为一个`.png`文件，包含排列在一行或一列的所有帧；或者导出为 2-D [精灵表](sprite-sheet.md)。

另见[工作空间](workspace.md)以了解更多关于窗口元素的信息。另见[工作流](workflow.md)节以了解更多细节。

## 一只手放在键盘上

您应该将左手放在键盘上（或右手，如果你是左撇子）。 由于有一些方便的键盘快捷键, 您可以从一开始就利用它们来更好地使用 Aseprite：

- 按键<kbd>1</kbd>、<kbd>2</kbd>、<kbd>3</kbd>、<kbd>4</kbd>、<kbd>5</kbd>和<kbd>6</kbd>可以用来变更[缩放](zoom.md)（你也可以用鼠标滚轮缩放）。
- <kbd>B</kbd> 按键是铅笔工具，<kbd>M</kbd>是矩形选取, 可能是你最常使用的工具。
- <kbd>Alt+点击</kbd>允许你使用吸管工具![吸管工具颜色](tools/eyedropper-tool.png)从活动的图像上选择颜色：
  - <kbd>Alt+左键</kbd>采样前景色
  - <kbd>Alt+右键</kbd>采样背景色
- <kbd>Ctrl</kbd>按键（或者 macOS 中的<kbd>⌘</kbd>）可以用来选择[移动工具](move-tool.md)![Move Tool Icon](tools/move-tool.png)，通过它你可以轻松地选择和移动图层。
- <kbd>Tab</kbd>按键隐藏和显示[时间线](timeline.md)。如果你的时间线不见了，这是显示它的最快方法。
- 按住<kbd>Space</kbd>同时<kbd>左键+拖拽</kbd> 会拖动你正在编辑的精灵的视口。如果你正在绘制一张大图或编辑放大了的图，这会很有用。

## 右键的可选功能

默认情况下，<kbd>右键</kbd>用[背景色](color-bar.md#background-color)绘图，但你也可以在[_Edit > Preferences > Editor_](right-click.md)修改配置。

---

**参见**

[工作空间](workspace.md) | [工作流](workflow.md) | [精灵](sprite.md)
