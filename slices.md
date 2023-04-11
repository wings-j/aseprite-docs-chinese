# 切片

通过切片工具![Slice tool icon](tools/slice-tool.png)（<kbd>Shift+C</kbd>），你可以指示精灵区域并赋予一个名称或标签，提供一些用户自定义的信息。这里有一些[9 宫格](https://en.wikipedia.org/wiki/9-slice_scaling)的相关信息。

通过这个工具你可以：

1. 按下鼠标、拖动鼠标、放开鼠标，然后创建一个标记矩形的新切片。
2. 如果标记的矩形接触现有切片，那些切片会被选中。
3. 你可以拖放一组选中的切片来把它们移动到其它地方。或者你可以重新调整从角落或边缘拖过来的切片的大小。
4. 通过按下删除键或*Edit > Delete*菜单选项，你可以删除选中的切片。
5. 双击一个切片，你会看到[切片属性](#slice-properties)对话框。

## 切片属性

如果你双击一个切片，你会看到它的属性：

![切片属性对话框](slices/properties.png)

在这里你可以指定：

1. 画布中切片的边界。
2. 九宫格属性，指定一个内部的矩形，进而将边界划分为子切片。
3. 切片内精灵的中心或基础锚点位置。

## 导出切片

你可以使用[--split-slice 选项](cli.md/#split-slices)导出切片会不同的精灵。

你也可以使用[--data 选项](cli.md/#data)或*File > Export Sprite Sheet*菜单并勾选 JSON 输出，来导出切片信息到一个精灵表 JSON。这里有个导出数据的示例：

```json
{
  "meta": {
    "slices": [{ "name": "Button-patch", "color": "#0000ffff", "keys": [{ "frame": 0, "bounds": { "x": 118, "y": 118, "w": 20, "h": 21 }, "center": { "x": 5, "y": 5, "w": 10, "h": 9 } }] }]
  }
}
```

---

**参见**

[绘图](drawing.md)
