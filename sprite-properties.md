# 精灵属性

你可以从*Sprite > Properties*菜单（<kbd>Ctrl+P</kbd>或者<kbd>⌘P</kbd>）改变精灵的一些属性。

![Sprite Properties dialog](sprite-properties/sprite-properties.png)

你可以：

- 改变[透明颜色](transparent-color.md)（对于[索引颜色模式](color-mode.md#indexed)）。
- 改变像素比例。
- 设置或转换[颜色配置](color-profile.md)。

## 颜色配置

在*Sprite Properties*对话框中，你可以看到两个，一个是**设置**其它颜色模式，另一个是**转换**其它颜色模式：

- 如果你**设置**精灵为一个新的颜色模式，像素值不会变化，只有精灵的颜色模式被设置。你会发现图片颜色变了因为虽然现在 RGB 值一样但[色彩空间](color-profile.md)变了。比如，“纯红色”值是 (255, 0, 0)，会和之前的“纯红色”不同。
- 如果你**转换**颜色配置，像素值会被从一个色彩空间转换为另一个色彩空间，所以颜色在视觉上没有变化，但是每个 RGB 值会被调整为新的色彩空间中的值（所以几乎所有像素都会改变）。

---

**参见**

[新精灵](new-sprite.md) | [颜色配置](color-profile.md) | [透明色](transparent-color.md)
