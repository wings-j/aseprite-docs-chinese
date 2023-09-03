# 旋转精灵或选区

任何选区都可以用[手柄](rotate.md#handles)或[菜单选项](rotate.md#menu-options)旋转，两种方法都会用选择的[算法](rotate.md#rotation-algorithms)绕[锚点](rotate.md#rotation-pivot)旋转。

## 旋转锚点

![旋转锚点](rotate/pivot-point-context-bar.png)

选区绕一个定义好的点（![Rotation Pivot](rotate/pivot-point.png)）旋转。默认情况下，锚点设置在选区中央，且在旋转之前不可见。

它的位置和可见性设置可以在任何选区工具的上下文栏变更。旋转锚点也可以用鼠标按住左键并拖动点来设置：

![Rotation Pivot Settings](rotate/pivot-point-settings.gif)
![Moving the Rotation Pivot with the mouse](rotate/pivot-point-mouse-move.gif)

<div style="font-style:italic;text-align:right;">精灵来自<a href="https://twitter.com/ThKasparrr">@ThKasparrr</a></div>

## 手柄

选区可以用在外部的手柄（![Handle](rotate/handle.png)）上移动鼠标来旋转，按住<kbd>左键</kbd>并用鼠标绕着画布拖动：

![Rotate Handles](rotate/rotate-handles.gif)

鼠标指针会自适应变化以显示拖动一个手柄会重新跳帧选区大小还是旋转选区：

|      |                  调整大小                  |                    旋转                    |
| ---- | :----------------------------------------: | :----------------------------------------: |
| 指针 | ![Resize Handle](cursor/resize-handle.png) | ![Rotate Handle](cursor/rotate-handle.png) |

按住<kbd>Shift</kbd>键你可以捕获角度（0º、45º、90º 等等）。

## 菜单选项

![Edit > Rotate](rotate/edit-rotate.png)

选区可以用*Edit > Rotate*下的菜单选项旋转 90º 或者 180º。

![Rotate Menu Options](rotate/rotate-menu-options.gif)

## 旋转算法

![Rotation Algorithms](rotate/rotation-algorithms.png)

有两种旋转算法可选：

- 快速旋转
- [RotSprite](https://en.wikipedia.org/wiki/Pixel-art_scaling_algorithms#RotSprite)

其中 RotSprite 被广泛采用因为它能产生更好的结果，但选择依赖于你的偏好。

![Fast Rotation vs RotSprite](rotate/rotation-algorithm.gif)

---

**参见**

[翻转](flip.md) | [调整大小](resize.md) | [移动](move-selection.md)
