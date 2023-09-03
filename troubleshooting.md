# 故障排除

如果你在启动（比如启动并立即关闭） Aseprite 是遇到问题，你可以尝试：

1. [重置偏好](reset-preferences.md)
2. 使用[调试选项](debug.md)，这会生成一个`Aseprite-v1.2-DebugOutput.txt`文件。
3. 仅在 Windows 中：检查生成的`Aseprite-v1.2-DebugOutput.txt`文件的最后一行是否有`PEN: Wintab library loaded`。如果有，尝试[禁用 Wintab](wintab.md)。
4. 其它情况，通过[support@aseprite.org](mailto:support@aseprite.org)联系我们，并发送`Aseprite-v1.2-DebugOutput.txt`文件。

你也可以在这些地方查找你的问题：

- [Aseprite 社区](https://community.aseprite.org)
- [Steam 通用论坛](http://steamcommunity.com/app/431730/discussions/0/)
- [Steam 问题报告论坛](http://steamcommunity.com/app/431730/discussions/2/)
- [GitHub 中关闭的问题](https://github.com/aseprite/aseprite/issues?utf8=%E2%9C%93&q=is%3Aissue%20is%3Aclosed%20%20label%3Abug)

## 崩溃/数据丢失

如果崩溃，你可能需要[恢复精灵](data-recovery.md)。

## 数位板问题

如果你的数位板（或数位板的压力）无效，请查看[tablet](tablet.md)页。

## macOS 渲染问题

在 macOS 中，Aseprite 使用异步渲染（[CALayer's drawsAsynchronously](https://developer.apple.com/documentation/quartzcore/calayer/1410974-drawsasynchronously?language=objc)）。从 Aseprite v1.2.20 开始，如果你遇到问题，比如屏幕中出现黑色矩形（无论如何如果你使用 Display P3 的[颜色配置](color-profile.md)，性能会极大地下降），可以禁用它。

要禁用它：

1. 关闭 Aseprite。
2. 在[偏好文件夹](preferences-folder.md)中打开`aseprite.ini`文件。
3. 搜索`[general]`节并添加选项`osx_async_view = false`。

```
[general]
osx_async_view = false
```

4. 保存文件并启动 Aseprite。

---

**参见**

[重置偏好](reset-preferences.md) | [数据恢复](data-recovery.md) | [调试](debug.md) | [数位板](tablet.md)
