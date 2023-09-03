# 重置偏好

Aseprite 偏好被存储在[配置文件夹](preferences-folder.md)的一个`aseprite.ini`文件中。你可以从*Edit > Preferences > Locate Configuration File*到达文件夹。想要重置配置，你可以关闭 Aseprite 并删除所有`aseprite.ini`所在位置额文件：

![Files in Preferences Folder](preferences/preffiles.png)

以防你无法打开程序，这里有各个平台手动重置配置的方法。

## Windows

1. 关闭 Aseprite。
2. 按下`Windows key + R`（或者`Start menu > Run...`）。这会显示一个运行程序的对话框，然后输入：
   %AppData%\Aseprite
   再按`Enter`键。
3. 删除文件夹中的文件（主要是`aseprite.ini`）。
4. 重启 Aseprite。

## macOS

1. 关闭 Aseprite。
2. 打开交掉搜索（⌘Space）
3. 用 ⌘V 粘贴这个文本`~/Library/Application Support/Aseprite`，再按回车：
   ![Spotlight Search](preferences/spotlight.png)
4. 删除
5. 删除文件夹中的文件（主要是`aseprite.ini`）。
6. 重启 Aseprite。

## Linux

1. 关闭 Aseprite。
2. 打开一个终端
3. 输入：
   xdg-open ~/.config/aseprite
4. 删除文件夹中的文件（主要是`aseprite.ini`）。
5. 重启 Aseprite。

---

**参见**

[故障排除](troubleshooting.md) | [偏好](preferences.md) | [偏好文件夹](preferences-folder.md)
