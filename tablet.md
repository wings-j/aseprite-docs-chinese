# 数位板

## Windows

从 Windows 8 开始，微软引入了一个供数位板和 Windows 程序使用的的新 API：指针 API。从 Aseprite v1.2.19.1 开始，你能将 API 配置成你偏好的样子：

![Tablet section](tablet/tablet.png)

- _Windows 8/10 指针 API_：对于大多数现代设备，选项应该是足够的，你可以试试你的数位板是怎样和这个 API 一起工作的（应该会比 Wintab 更好）。
- _[Wintab](wintab.md)_：在老系统（Windows Vista/7）和其它设备上支持压力敏感度时这个选项很有用。
- _Wintab（直接数据包处理）_：这个选项在一些设备上可能无法很好地工作，但在其它设备上可以很好的避免丢包和获得顺滑的笔触。

点击*OK*/*Apply*按钮可以立即改变数位板设置，不需要重启程序。

## Linux/X11

在 X11 上，看起来数位板/笔时依靠设备名称/品牌被识别的，而不是设备功能。

有一些预定义的笔 ID，但不一定够（如同[#3176](https://github.com/aseprite/aseprite/issues/3176)的说明）。

如果 Aseprite 没有识别你的笔压力，从**Aseprite v1.2.35**开始，你可以试试这些措施：

1. 关闭 Aseprite。
2. 在终端/控制台运行`xinput --list`。
3. 检查输出，看你的笔可能和什么设备有关。（[输出示例](https://github.com/aseprite/aseprite/issues/3176#issuecomment-1111799083)）
4. 打开[偏好文件夹](preferences-folder.md)中的`aseprite.ini`文件。
5. 搜索`[general]`节，添加你的笔的名称到`x11_stylus_id`选项（名称必须出现在`xinput --list`输出的第一列）：

```
[general]
x11_stylus_id = Your Stylus Name
```

6. 保存文件并启动 Aseprite

如果这个方法对你的情况无效，请通过在[#3176](https://github.com/aseprite/aseprite/issues/3176)添加一个评论来通知我们，并指明你的设备名称。

---

**参见**

[Wintab](wintab.md) | [故障排除](troubleshooting.md)
