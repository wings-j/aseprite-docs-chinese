# 颜色栏

颜色栏显示激活精灵的调色盘：

![Color bar](color-bar/color-bar.png)

每种颜色都可以通过其索引来识别，从 0 到 255

用<kbd>左键</kbd>选择前景色，用<kbd>右键</kbd>选择背景色，用<kbd>X</kbd>键交换前景色和背景色。

根据激活精灵的[色彩模式](color-mode.md)：

- 在索引图像中，颜色栏显示所有精灵可以使用的颜色。你不能使用不在调色盘中的颜色，除非用`编辑调色板`按钮或者<kbd>F4</kbd>按键修改调色盘。
- RGB 图像中，颜色栏显示可供选择的颜色调色板。但是精灵并不依赖于调色板，你可以任意改变精灵为你想要的颜色，也就是说你可以在精灵中使用并不存在于调色板中的颜色。

## 前景色

<kbd>左键</kbd>使用的颜色。如果你点击了按钮，你会看见一个使用[RGB]（http://en.wikipedia.org/wiki/RGB_color_model）或[HSB]（http://en.wikipedia.org/wiki/HSL_and_HSV）滑块来选择颜色的弹窗：

![Color Popup](color-bar/color-popup.png)

警告图片![warning icon](color-bar/color-warning-icon.png)按下后，调色盘中不存在的颜色会被添加到其中。

![Color Warning](color-bar/color-warning.png)

## 背景色

<kbd>右键</kbd>使用的颜色。

这个颜色也在多个场景下被用于清除`背景`图层：

- 当选区被清除（_Edit > Clear_）
- 当一个空帧被添加（_Frame > New Empty Frame_）
- 当一个透明图层被转换为背景图层（_Layer > Background from Layer_）

---

**参见**

[Color](color.md)
