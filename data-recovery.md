# 数据恢复

当 Aseprite 运行时，它会保存一些临时数据，以便在你的电脑（或 Aseprite）崩溃或你关闭了 Aseprite 但忘记保存精灵时恢复精灵。（即使你保存了精灵，原备份依然会在你的磁盘中保存几个星期。）

## 从上一次会话中打开精灵

想要从上一次会话中恢复精灵，你需要使用“主页”标签中的“恢复文件”选项：

如果 Aseprite 崩溃了（没有正确关闭）并且精灵没有保存，你会看到“恢复文件”按钮。

这个按钮可以打开一个“恢复文件”标签页，在这里，你可以双击一个条目（或者选择它并按下“恢复精灵”）来从上一个会话中恢复一个精灵。

## 偏好

在*Edit > Preferences > Files*中，你可以配置备份数据如何保存和保存多久：

![Data Recovery Preferences](data-recovery/recover-data-preferences.png)

- _每 X 秒/分钟自动保存数据_：表示 Aseprite 应该每 X 秒或分钟自动（在磁盘上）保存备份数据（默认为 2 分钟）。
- _保持编辑过的精灵数据 Y 天/星期/月_：对于每一个被编辑的精灵，Aseprite 会（在磁盘上）保持备份数据持续给定的天/星期/月数（默认为 1 星期）。
- _保持关闭的精灵在内存中 Z 秒/分钟/小时_：如果你意外关闭了一个精灵，Aseprite 会（在内存中，不带撤销信息）保持精灵持续给定的时间（默认为 15 分钟）。你可以用*File > Open Recent > Reopen Closed File*菜单选项（Ctrl+Shift+T or ⇧⌘T）重新打开一个关闭的文件。

## 内部

备份数据储存在你的[首选项文件夹](preferences-folder.md)里名为`sessions`的子文件中：

![Sessions Folder](data-recovery/sessions-folder-focused.png)

`sessions`可能包含以及子文件夹（每一个都代表一次 Aseprite 的运行）：

![Inside Sessions Folder](data-recovery/in-sessions-folder.png)

这些文件夹的名称（比如`20180405-165510-1128`）格式为`YYYYMMDD-HHMMSS-PID`，表示：

- `YYYY`、`MM`、`DD`：会话（Aseprite 启动）的日期（年、月、日）。
- `HH`, `MM`, `SS`：会话启动的时间（时、分、秒）。
- `PID`：处理会话文件夹的 Aseprite 示例的编号/标识符。

每个文件夹都包含用来恢复在崩溃中丢失的精灵的有用数据。

如果你无法用“首页”标签的“恢复文件”选项恢复会话，但是你在[首选项文件夹](preferences-folder.md)里有一个`sessions/YYYYMMDD-HHMMSS-PID`文件夹，你可以压缩这个文件夹为`.zip`文件并发送到[support@aseprite.org](mailto:support@aseprite.org)，我们可以尝试恢复你的数据。

---

**参见**

[故障排除](troubleshooting.md) | [首选项文件夹](preferences-folder.md) | [Blog Article About Data Recovery Internals](https://dev.aseprite.org/2015/06/14/data-recovery/)
