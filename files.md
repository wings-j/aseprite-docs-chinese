# 文件

Aseprite 使用多种文件格式来保存和读取不同的信息。你需要知道的主要事情是，当你用[*File > Save*菜单](save.md)时你的工作保存在计算机本地，不涉及“云”或者远程服务器功能。所以请记得，如果你想保证你的工作安全或在不同计算机之间共享，使用类似云的文件夹服务，比如 Dropbox、Drive、OneDrive 等等，来备份你的工作。

## .aseprite

Aseprite 有自己的文件格式来保存你的工作：`.aseprite`文件（或`.ase`, [两者一样](/faq/#is-there-any-difference-between-ase-and-aseprite-files)）。当你把精灵保存在一个`.aseprite`文件里时，你能够保持所有的信息完好无损（[颜色模式](color-mode.md)，[图层](layers.md)，[帧](frames.md)，调色盘，[标签](tags.md), [切片](slices.md)，等等）。

通常，你会希望能够[导出作品](exporting.md)为其它格式（`.png`，`.gif`，等等），来发布或用作游戏资源。但是请保存好原始的`.aseprite`文件，以便在需要时修改。

这些文件的内部结构可以在[Aseprite 文件格式规范](https://github.com/aseprite/aseprite/blob/main/docs/ase-file-specs.md)查看。

## .aseprite-extension

你可以以`.aseprite-extension`格式创建扩展，它本质上是一个包含许多文件的`.zip`文件，参见[扩展](extensions.md)页[文件内容](extensions.md#file-content)章节。

## .lua

存放在*File > Scripts > Open Scripts Folder*目录的[脚本文件](scripting.md)。

## 偏好

[偏好](preferences.md)保存在[偏好文件夹](preferences-folder.md)的多个文件中：

### aseprite.ini

*Edit > Preferences*对话框声明的主要设置保存在这个文件。

## user.aseprite-brushes

自定义笔刷保存在这里（XML 文件）。未来我们将为在不同的文件之间导入和导出笔刷引入更多的选项。

### user.aseprite-keys

自定义键盘快捷键保存在这个文件中。当你导出和导入键盘快捷键时，会使用相同的`.aseprite-keys`文件格式（XML 文件）。

### 会话

会话文件夹有用于[数据恢复](data-recovery.md)的备份文件。

---

**参见**

[保存](save.md) | [导出](exporting.md) | [偏好](preferences.md) | [Aseprite 文件格式规范](https://github.com/aseprite/aseprite/blob/main/docs/ase-file-specs.md)
