# 调试

如果你在运行 Aseprite 遇到了问题，你可以在命令行中带着`-debug`选项运行 Aseprite。

运行 Aseprite 后，你会看到一个`Aseprite-v1.2-DebugOutput.txt`（或类似名称的）文件在桌面上被创建。你可以把那个文件通过[support@aseprite.org](mailto:support@aseprite.org)发送给我们，这样我们能帮你解决你的特定问题。

如何添加`-debug`参数：

- [Windows](#windows)
- [macOS](#macos)
- [Steam](#steam)

<hr>

## Windows

1. 你可以按 Windows 键来打开开始菜单并输入`Aseprite`，然后展开 Aseprite 的操作：

   ![Aseprite on Start menu](debug/win-1-start-menu.png)

2. 在这个操作列表中点击“Open file location”：

   ![Expand options](debug/win-2-actions.png)

3. 右键点击 Aseprite 快捷方式并选择“Properties”选项：

   ![Right click properties](debug/win-3-right-click-properties.png)

4. 最后在“Target”框中输入`-debug`参数并点击“OK”：

   ![Debug on properties](debug/win-4-debug-option.png)

<hr>

## macOS

1. 首先你需要关闭 Aseprite，然后通过按下 ⌘ 空格或点击菜单栏上的放大镜来打开焦点搜索：

   ![Open Spotlight](debug/macos-1-open-spotlight.png)

2. 在焦点搜索中输入`Terminal`和回车键以打开终端应用：

   ![Terminal on Spotlight](debug/macos-2-open-terminal.png)

3. 在终端中输入下列命令并按下回车：

   open -a Aseprite --args -debug

<hr>

## Steam

在 Steam 中你可以在 Aseprite 启动选项中添加`-debug`选项：

1. 在你的 Steam 库中右键点击 Aseprite（macOS 中为 Ctrl + 点击），打开它的“Properties”：

   ![Open Aseprite Properties](steam/steam-1-open-properties.png)

2. 点击“设置启动选项”按钮：

   ![Open launch options](steam/steam-2-launch-options.png)

3. 添加`-debug`选项并点击“OK”：

   ![Add debug option](steam/steam-3-debug-option.png)

---

**参见**

[故障排除](troubleshooting.md)
