# Wintab

Wintab（`WinTab32.dll`）是 Wacom 创造的老 API，它用来在数位板设备和 Windows 程序间通信。在 Windows 8 之前，这曾经是从 Wacom 和其它品牌数位板获取压力信息的事实标准。从 Windows 8 开始，微软引入了新的官方 API，指针 API/Windows 墨水。

自从**Aseprite v1.2.34**（和**v1.3-beta12**）开始，因为我们已经收到了很多有关有问题的第三方`WinTab32.dll`的报告，所以我们已经切换到默认使用 Windows 指针 API。（Wintab 选项在[数位板选项](tablet.md)中仍然可用）

在 Aseprite 之前的版本中，我们尝试在初始化时就加载 Wintab 库，但是这可能会引起程序随机崩溃。有时重新安装驱动程序、重启 Windows、从[数位板选项](tablet.md)启用指针 API、或者在*Edit > Preferences > Tablet*（(旧版本中*Edit > Preferences > Experimental*)）直接禁用 Wintab 可以解决问题。

![Don't load the WinTab driver](wintab/disable-wintab.png)

## Aseprite 无法启动

如果你甚至无法启动程序，你可以携带`-disable-wintab`参数（从 Aseprite v1.2 后可用）执行 Aseprite：
"C:\Program Files\Aseprite\Aseprite.exe" -disable-wintab
这位禁止加载`WinTab32.dll`文件。你的数位板可能不能正确工作，但至少 Aseprite 可以用你的鼠标/轨迹板执行（或者你可以尝试[Windows 指针 API](tablet.md)）。

## Steam

在 Steam 你可以在 Aseprite 启动选项中添加`-disable-wintab`选项：

1. 在 Steam 库中的 Aseprite 右键点击并代开它的“属性”：

   ![Open Aseprite Properties](steam/steam-1-open-properties.png)

2. 点击“设置启动选项”按钮：

   ![Open launch options](steam/steam-2-launch-options.png)

3. 添加`-disable-wintab`选项并点击“OK”：

   ![Add disable wintab option](steam/steam-3-disable-wintab.png)

---

**参见**

[数位板](tablet.md) | [故障排除](troubleshooting.md)
