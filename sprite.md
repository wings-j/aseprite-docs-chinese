# 精灵

在 Aseprite 中，文档、文件或精灵有以下属性：

1. 它的[尺寸](sprite-size.md)以像素为单位（宽和高）。
2. 它有一个[颜色模式](color-mode.md)，告诉你图像可以处理的颜色的数量。精灵中的所有图像都有一个特定模式，你不能在一个精灵中混合 RGB 模式图像和索引模式图像。
3. [颜色配置](color-profile.md)表示 RGB 所处的色彩空间。
4. 它包含一组图层。你可以在[时间线](timeline.md)里看到它们。很重要的一点是这里有两种图层：不透明精灵的[背景图层](layers.md#background-layer)和[透明图层](layers.md#transparent-layers)。一个精灵只能有一个背景图层，但是可以有几个透明图层。
5. 它包含动画帧。每个帧有一个周期，即动画播放时帧在屏幕上存在的时间。
6. 每个图层和帧的交集成为[赛璐珞](cel.md)，它包含了你最终[绘制](drawing.md)的图像。

[时间线](timeline.md)以网格的形式给你展示了精灵的整体结构。行表示图层，列表示帧，矩阵的单元格表示[赛璐珞](cel.md)：![](sprite/sprite-components.png)。

你会看到一些额外的元素，比如[标签](tags.md)和[链接赛璐珞](linked-cels.md)。它们对于组织一个精灵中的几个动画和复用一个动画（或不同动画）的帧很有用。

---

**SEE ALSO**

[色彩模式](color-mode.md) | [保存](save.md) | [精灵尺寸](sprite-size.md)
