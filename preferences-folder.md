# 偏好文件夹

Aseprite 配置存储在个人配置目录的多个文件中：

![Files in Preferences Folder](preferences/preffiles.png)

你可以用*Edit > Preferences > Locate Configuration File*菜单来到达这个文件夹。

不论如何，根据你的平台，你可以用不同的方法手动定位到这个文件夹：

## Windows

你可以通过按<kbd>Windows key + R</kbd>（或者 `Start menu > Run...`）来定位文件夹。这会显示一个运行程序的对话框，然后你输入：

You can locate the preferences folder pressing the <kbd>Windows key + R</kbd>
key (or `Start menu > Run...` option). This will show the dialog to
%AppData%\Aseprite

并按下`Enter`键。

## macOS

你可以打开关注点搜索(<kbd>⌘Space</kbd>)，用<kbd>⌘V</kbd>粘贴下列文本`~/Library/Application Support/Aseprite`，再按<kbd>Enter</kbd>。

![Spotlight Search](preferences/spotlight.png)

## Linux

打开一个终端，粘贴下列命令并按<kbd>Enter</kbd>：

    xdg-open ~/.config/aseprite

## 特殊配置

从 Aseprite Aseprite v1.2.16.3 开始，为了测试，你可以用`ASEPRITE_USER_FOLDER`[环境变量](https://en.wikipedia.org/wiki/Environment_variable)重新配置偏好文件夹的位置指向其它文件夹。

---

**参见**

[偏好](preferences.md) | [重置偏好](reset-preferences.md)
