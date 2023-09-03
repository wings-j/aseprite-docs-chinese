# 键盘快捷键

你可以自定义键盘快捷键或按键和[鼠标滚轮](mouse-wheel.md)（或[鼠标移动](drag-value.md)），使用*Edit > [键盘快捷键](keyboard-shortcuts.md)*菜单选项或 kbd>Ctrl+Alt+Shift+K</kbd>按键（或者 macOS<kbd>⌥⇧⌘K</kbd>）

在[快捷参考](/quickref/)中有一个默认键盘快捷键的常用概览。

## 菜单 & 命令

在这些章节中，你可以找到设置每一个[菜单栏](menu-bar.md)操作/命令或不在菜单栏的高级命令的快捷键的方法。（比如“设置墨水类型”无法在任何菜单中找到也没有默认键盘快捷键，但是你可以设置一个“命令”章节中的按键。）

## 工具

在工具章节你能找到一个改变[工具栏](tool-bar.md)中每个工具相关联的按键的方法。主要考虑两点：

1. 两个或更多的工具可以共享一个按键。在这种情况下，按下按键会切换/遍历所有拥有相同按键的工具。比如，默认情况下<kbd>U</kbd>被分配到![Rectangle icon](tools/rectangle-tool.png)矩形和![Filled Rectangle icon](tools/filled-rectangle-tool.png)填充矩形，所以按下一次这个按键会激活矩形工具，按第二次会切换到填充矩形。
2. 有两种选择工具的方法：

- 一种改变激活工具的常规方法，就是当你按下一个键，然后接下来所有的鼠标操作都是用这个工具。比如，按下<kbd>H</kbd>键切换到![Pencil icon](tools/pencil-tool.png)铅笔工具，或者按下<kbd>H</kbd>键选中![Hand icon](tools/hand-tool.png)手型工具，这样你可以用鼠标右键 + 移动的方式来拖动[精灵编辑器](sprite-editor.md)，不用按其它的键。
- 还有一种可选的便捷方法（在*Keyboard Shortcuts*对话框中以“(quick)”标识），让你在按住某个键不放时激活一个工具（当你松开这个键时， Aseprite 会回到前一个工具）。这可以用在临时用<kbd>Alt</kbd>键选择![Eyedropper icon](tools/eyedropper-tool.png)滴管工具或<kbd>空格</kbd>选择![Hand icon](tools/hand-tool.png)手型工具时。在配置中![Hand icon](tools/hand-tool.png)手型工具长这样：

![Hand tool example](keyboard-shortcuts/hand-shortcuts.png)

## 操作修饰器

这些操作依赖于 Aseprite 中的一个特定上下文，比如当你使用选区工具或者缩放一个选区时。给定的键时默认选项。

以下时上下文和可能上下文中可能的操作的列表：

- **手绘工具**: 当![Pencil icon](tools/pencil-tool.png)铅笔工具激活时。
  - **从前一个点开始的直线**：使用<kbd>Shift</kbd>键创建一条从前一个用笔刷创建的像素开始的直线。
  - **从前一个点捕获角度**：使用<kbd>Ctrl</kbd>键捕获直线的角度。
- **移动工具**：当你使用![Move Tool Icon](tools/move-tool.png)移动工具。
  - **自动选择图层**：如果你按<kbd>Ctrl</kbd>（或者 macOS 中的<kbd>⌘</kbd>），当你单击时你会选中就在指针下面的图层。
- **形状工具**：这些键（鼠标按下后或松开前）可以在你使用矩形或椭圆类工具（比如![Rectangle Icon](tools/rectangle-tool.png)矩形、![Ellipse Icon](tools/ellipse-tool.png)椭圆、![Rectangular Marquee Icon](tools/marquee-tool.png)矩形选框等）画画时一起使用。
  - **方形比例**：你可以使用<kbd>Shift</kbd>键创建一个正方形或圆。
  - **从中心绘画**：当按下<kbd>Ctrl</kbd>键时，你可以将鼠标按下的点作为形状的中心，比如创建一个指定中心（而不是两个角）的椭圆。
  - **旋转形状**：按下<kbd>Alt</kbd>你可以开始旋转形状。
  - **移动原点**：在原点没有正确指定的情况下，你可以按下<kbd>空格</kbd>键并在松开鼠标前移动整个形状。
- **选区**：当我们使用选区工具时，可以用一些键来改变控制选区的行为。
  - **加/减/交叉选区**：这些选项在[选区](selecting.md#add/subtract/intersect)章节中有提及。
- **平移选区**：当你移动选区时。
  - **吸附到网格**：按下<kbd>Alt</kbd>选区会吸附到网格。
  - **锁定轴**：你可以按下<kbd>Shift</kbd>锁定移动只在 X 或 Y 方向进行。
  - **复制选区**：在你开始移动选区*之前*，按下<kbd>Ctrl</kbd>键你可以复制选区。
  - **精细平移**：当你移动选区时，按下<kbd>Ctrl</kbd>会开始精细调节的移动（不只像素级，而是次像素级）。
- **缩放选区**：当你缩放选区时。
  - **保持比例**：按下<kbd>Shift</kbd>键保持高宽不变。
  - **从中心缩放**：使用<kbd>Alt</kbd>从中心（或当前锚点）缩放。
  - **精细缩放**： 当你缩放选区时，按下<kbd>Ctrl</kbd>会开始精细调节的缩放（不只像素级，而是次像素级）。
- **旋转选区**：当你旋转选区时。
  - **角度吸附**：你可以使用<kbd>Shift</kbd>键来吸附角度为 26.6°, 45°, 90° 等等。
- **出发鼠标左/右键**：你可以在[精灵编辑器](sprite-editor.md)中配置一个特定的按键来模拟鼠标左/右键。

## 键盘 + 鼠标

你可以配置当键盘按下并滚动鼠标滚轮（或鼠标在特定轴上移动）时出啊发的特定操作。

- [鼠标滚轮](mouse-wheel.md)
- [拖动值](drag-value.md)

---

**参见**

[偏好](preferences.md) | [自定义](customization.md)
