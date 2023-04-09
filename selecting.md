# Selecting

你可以用选区工具，比如框选工具![框选工具图标](tools/marquee-tool.png)（<kbd>M</kbd>），来选择精灵的一部分，然后进行[移动](move-selection.md)和[变换](transformations.md)（[缩放](resize.md)、[旋转](rotate.md)等等）。当你选择了精灵的部分后，你会看到[蚂蚁行军](https://en.wikipedia.org/wiki/Marching_ants)效果。

![蚂蚁行军](selecting/marching-ants.gif)

当你作出选区，你选择的是激活的[赛璐珞](cel.md)，所以所有的变换都只会应用到这个特定的赛璐珞。

## 加/减/交叉

在[上下文栏](context-bar.md)中，你会发现一些影响已选择区域的修饰器：![修饰器](selecting/modifiers.png)。

默认情况下，当你按下鼠标左键，拖动然后释放，它会替换整个选取。但你可以用其它选项（每个选项都有一个键盘快捷键）调整这一行为：

- ![替换选区](selecting/replace-selection.png)：默认行为，用新选区替换整个选区（左键拖动）。
- ![加选区](selecting/add-selection.png): 合并新选区和现有选区（左键拖动 + <kbd>Shift</kbd>）。
- ![减选区](selecting/subtract-selection.png)：现有选区减去新选区（左键拖动 + <kbd>Alt+Shift</kbd> 或者：右键拖动）。
- ![交叉选区](selecting/intersect-selection.png): 交叉新选区和现有选区（左键拖动 + <kbd>Ctrl+Shift</kbd>）。

这些按键可以在[_Edit > Keyboard Shortcuts > Action Modifiers_](keyboard-shortcuts.md#action-modifiers)自定义。

## 选择内容

你可以选择：

- 整个画布，使用*Select > All*（<kbd>Ctrl+A</kbd>或<kbd>⌘A</kbd>）。
- 激活的[赛璐珞](cel.md)边界，使用*Edit > Transform*（<kbd>Ctrl+T</kbd>或<kbd>⌘T</kbd>）。
- 激活的帧内容（非透明内容），在图层上使用<kbd>Ctrl+左键</kbd>（加/减/交叉修饰器的键盘快捷键也可以使用）。

## 取消选择和重新选择

你可以用*Select > Deselect*（<kbd>Ctrl+D</kbd>或<kbd>⌘D</kbd>）隐藏当前选区。然后你可以使用*Select > Reselect*（<kbd>Ctrl+Shift+D</kbd>或<kbd>⇧⌘D</kbd>）让它重新出现。

## 反选

你可以使用*Select > Invert*（<kbd>Ctrl+Shift+I</kbd>或<kbd>⇧⌘I</kbd>）反向选择。

---

**参见**

[变换](transformations.md) | [移动选区](move-selection.md)
