# 导出

通常你会使用*File > Save*来[保存工作](save.md)，[`.aseprite`文件](files.md#aseprite)包含所有信息。然后你可以导出精灵到游戏、网站、应用等。使用*File > Export*菜单选项（<kbd>Ctrl+Alt+Shift+S</kbd>或 macOS 中<kbd>⌥⇧⌘S</kbd>）将精灵转换为`.gif`文件或一系列`.png`文件。

如果你想再一次保存，*File > Export*会记住你上一次使用的选项。

## 导出为一系列图像

你可以保存整个动画为一系列名字中带有数字的静态图像文件。比如`frame1.png`，`1`是表示第一帧的数字，`.png`是存储每帧的静态文件类型。参见如何[载入一系列图像](open.md#loading-image-sequences)。

如果你设定了其它文件名，比如`frame001.png`，那么文件名就是`frame001.png`、`frame002.png`、`frame003.png`等等。

## 只导出一帧

如果在*File > Export*修改*Frames*值为*Selected frames*，你可以导出一帧（一个图层，或一组选择的帧等等）。

![File > Export > Selected Frame](exporting/file-export-sel-frame.png)

## 导出是自动调整大小

*File > Export*包含一个特殊的*Resize*值，所以你可以保存作品为其它尺寸。当你上传动画到社交网络并需要更大尺寸（比如原始尺寸的 400%）时，这个功能非常有用。

![File > Export > Resize](exporting/file-export-resize.png)

## 其它导出选项

*File > Export*其它有用的选项：

![File > Export menu option](exporting/file-export.png)

- _Animation Direction_：你可以以前向、反向或来回模式导出动画。
- _Apply pixel ratio_：如果你的精灵有个特殊的像素比例（比如 2:1），勾选这个选项使得最终结果应用了这个像素比。
- _Export for Twitter_：调整动画来避免 Twitter 以一个无效的延迟来重新生成最后最后一帧的问题。

---

**参见**

[保存](save.md) | [精灵表](sprite-sheet.md) | [命令和接口](cli.md)
