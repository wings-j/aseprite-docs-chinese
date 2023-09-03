# 链接的赛璐珞

当两个赛璐珞共享它们的图像和*xy*坐标时，它们就被链接起来了。链接的赛璐珞在[时间线](timeline.md)中如此显示：

![Linked Cels](linked-cels/linked-cels.png)

当你修改其中一个这些赛璐珞时，所有链接的赛璐珞都会被修改。用这种方法，你可以传递同一个改变到好几个帧。比如，如果你有一个静态的背景，你会更喜欢链接的赛璐珞，这样你可以在一个赛璐珞中修改，而影响整个动画。

想要创建链接赛璐珞，你需要在一个[连续图层](continuous-layers.md)中[复制赛璐珞](copy-cels.md)（也就是有连续标志![Continuous icon](continuous-layers/continuous-layer.png)的图层）。

## 取消链接赛璐珞

使用右键和*Unlink*选项可以取消时间线中的赛璐珞：

![Unlink Cels](linked-cels/unlink-cels.gif)

被取消链接的赛璐珞会包含它们自己的图像副本。所以现在如果你修改它们，变更不会传递到其它赛璐珞。

---

**参见**

[连续图层](continuous-layers.md)
