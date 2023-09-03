# 透明色

在[RGB](color-mode.md#rgb)和[灰度](color-mode.md#grayscale)精灵中，透明像素是`Alpha=0`的颜色，但是在[索引](color-mode.md#indexed)颜色模式中，有一个特殊的索引，代表了[透明图层](layers.md#transparent-layers)中的透明色。

![Transparent Color](transparent-color/transparent-color-property.png)

这意味着指向这个特殊索引的像素不可见（并且只有背景图层可以将“透明色”显示为一个固定颜色）。

你可以在[颜色工具栏](color-bar.md)使用鼠标中键改变透明颜色，或者使用[_Sprite > Properties_](sprite-properties.md)菜单选项。

---

**参见**

[颜色]](color.md) | [颜色模式](color-mode.md) | [精灵属性](sprite-properties.md)
