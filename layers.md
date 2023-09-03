# 图层

一个精灵可以被细分成多层。你可以在[时间线](timeline.md)中看到它们：

![Layer in timeline](layers/layer-in-timeline.png)

每个层都有几个选项：

![Layer icons](layers/layer-options.png)

- _图层名称（Layer Name）_：标志图层的文本。你可以通过双击图层变更图层名称，或者从*Layer > Properties*菜单（<kbd>Shift+P</kbd>）。
- _赛璐珞（Cels）_：一组赛璐珞[赛璐珞](cel.md)，在特定的图层和帧中的可见内容。
- _可见（Visible）_：表示图层是否可见![可见图层图标](layers/visible-layer.png)或隐藏![隐藏图层图标](layers/hidden-layer.png)。你可以用*Layer > Visible*菜单或<kbd>Shift+X</kbd>按键切换图层的可见性。
- _锁定（Locked）_：如果图层被锁定![锁定图层图标](layers/locked-layer.png)，你就不能在上面绘图。默认情况下，所有图层都是未锁定或可编辑的![可编辑图层图标](layers/editable-layer.png)。
- _连续（Continuous）_：这个选项用于表示给这个图层创建哪种[赛璐珞](cel.md)。参见[连续图层](continuous-layers.md)以获得更多信息。

### 常见操作

- [添加新图层](new-layer.md)
- [移动图层](move-layers.md)
- [复制图层](copy-layers.md)

## 背景图层

背景图层时一个无法移动的不透明图层（没有 Alpha 或透明组分）。当你在*File > New*窗口里选择一个不透明色，或者当你打开一个不包含 Alpha 组分的文件（比如一个`.png`文件），它会默认被创建。

一个精灵只能包含一个背景图层，并且总是在[时间线](timeline.md)中图层栈的底部。

当你选择背景图层的一部分并（使用*Edit > Clear*菜单）清除它时，选区会被清除并填充激活的[背景色](color-bar.md)。

## 透明涂层

虽有拥有 Alpha 通道的图层称为透明涂层。一个精灵可以有多个透明涂层，你可以随心所欲地在[时间线](timeline.md)中堆叠它们。并且，你可以用[移动工具](move-tool.md)![移动工具图标](tools/move-tool.png)替换这些图层。

当你选择了透明涂层的一部分并且（使用*Edit > Clear*菜单）清除它时，选区会被清除并被填充[透明色](transparent-color.md)。

你可以使用*Layer > New > New Layer*菜单或者<kbd>Shift+N</kbd>按键来创建一个新透明涂层。

## 图层背景

如果没有背景图层，你可以使用*Layer > Convert To > Background*菜单来将任何透明涂层转换为背景图层。所有的透明像素会被填充为激活的[背景色](color-bar.md#background-color)。

> 以前，在 Aseprite V1.2 中，选项位于*Layer > Layer from Background*。

## Layer from Background

如果你想转换背景为一个透明图层（比如因为你想用[移动工具](move-tool.md)![Move tool icon](tools/move-tool.png)移动它），你可以使用*Layer > Convert To > Layer*菜单。

> 以前，在 Aseprite V1.2 中，选项位于*Layer > Layer from Background*。

## 图层组

你可以将[图层分组](layer-group.md)以将图层处理为一个单元。

## 从选区创建图层

- <kbd>Ctrl+J</kbd>或<kbd>⌘J</kbd>：复制[选区](selecting.md)并以此创建一个新图层。
- <kbd>Ctrl+Shift+J</kbd>或<kbd>⇧⌘J</kbd>：剪切[选区](selecting.md) 并以此创建一个新图层。

---

**参见**

[时间线](timeline.md) | [连续图层](continuous-layers.md) | [移动工具](move-tool.md)
