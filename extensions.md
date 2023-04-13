# 扩展

从**[Aseprite v1.2-beta10](https://www.aseprite.org/release-notes/#aseprite-v1-2-beta10)**之后，你可以在 Aseprite 添加和移除扩展。扩展通过`.aseprite-extension`（`.zip`）文件分发，你可以在 *Edit > Preferences > Extensions*管理它们：

![偏好中的扩展](extensions/extensions.png)

## 添加和移除扩展

在*Edit > Preferences > Extensions*有一个“添加扩展”按钮。你可以使用它选择一个`.aseprite-extension`或`.zip`文件。安转了扩展后，它会在[配置文件夹](preferences-folder.md)的`extensions`子文件夹中解压缩。

## 文件内容

一个扩展或插件就是一个`.zip`文件，但是你可以把它的扩展名更改为`.aseprite-extension`，这样用户就可以在 Windows Explorer 或 macOS Finder 中双击它。

`.zip`文件的内容根据你想创建的扩展类型而变更，但它们一定会包含`package.json`文件。

一个`.aseprite-extension`文件的结构取决于扩展种类：

- [按键](extensions/keys.md)
- [调色板](extensions/palettes.md)
- [语言](extensions/languages.md)
- [驻地](extensions/themes.md)
- [抖动矩阵](extensions/dithering-matrices.md)
- [脚本插件](https://github.com/aseprite/api/blob/master/api/plugin.md#plugin)
