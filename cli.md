# Aseprite 命令行接口

你可以在命令行转换和导出精灵为其它格式（或者纹理 + JSON 数据）。参见[平台特定细节](#platform-specific-details)如何使用命令行。

- [选项](#options)
- [用例](#use-cases)
- [平台特定细节](#platform-specific-details)
- [自动处理](#automating-the-process)

![地图](//www.aseprite.org/assets/images/atlas.gif)

# 选项

<pre>
用法：
  aseprite.exe [OPTIONS] [FILES]...

选项：
      --<a href="#shell">shell</a>                  启动一个交互式控制台来执行脚本
  -b, --<a href="#batch">batch</a>                  不要启动 UI
  -p, --<a href="#preview">preview</a>                不要执行动作，只打印会发生的事
      --<a href="#save-as">save-as</a> &lt;filename&gt;     保存给定的精灵为其它格式
      --<a href="#palette">palette</a> &lt;filename&gt;     改变上一个给定精灵的调色板
      --<a href="#scale">scale</a> &lt;factor&gt;         调整所有之前打开的精灵的尺寸
      --<a href="#dithering-algorithm">dithering-algorithm</a> &lt;algorithm&gt;
                               --color-mode 使用的用于将 RGB 模式转换为索引模式的抖动算法
      --<a href="#dithering-matrix">dithering-matrix</a> &lt;matrix&gt;
                               有序抖动算法使用的矩阵
      --<a href="#color-mode">color-mode</a> &lt;mode&gt;      改变所有之前打开的精灵的颜色模式：
                                 rgb
                                 grayscale
                                 indexed
      --<a href="#data">data</a> &lt;filename.json&gt;   存储精灵表元数据的文件
      --<a href="#format">format</a> &lt;format&gt;        输出数据的文件格式（json-hash，json-array）
      --<a href="#sheet">sheet</a> &lt;filename.png&gt;   保存纹理的图片文件
      --<a href="#sheet-type">sheet-type</a>             创建精灵表的算法：
                                 horizontal
                                 vertical
                                 rows
                                 columns
                                 packed
      --<a href="#sheet-width">sheet-width</a> &lt;pixels&gt;   精灵表宽度
      --<a href="#sheet-height">sheet-height</a> &lt;pixels&gt;  精灵表高度
      --<a href="#sheet-columns">sheet-columns</a> &lt;columns&gt;
      --<a href="#sheet-rows">sheet-rows</a> &lt;rows&gt;
      --<a href="#sheet-pack">sheet-pack</a>             使用打包算法以避免纹理的空间浪费
      --<a href="#split-layers">split-layers</a>           导入下一个给定精灵的每个图层为表中的独立的图片
      --<a href="#split-tags">split-tags</a>             保存每个标签为独立的文件
      --<a href="#split-slices">split-slices</a>           保存每个切片为独立的文件
      --<a href="#layer">layer</a> &lt;name&gt; 或
      --<a href="#layer">import-layer</a> &lt;name&gt;    在表中包含给定的图层
      --<a href="#all-layers">all-layers</a>             使所有图层可见。默认情况下隐藏图层会被忽略
      --<a href="#ignore-layer">ignore-layer</a> &lt;name&gt;    在表中排除给定图层或保存为操作
      --<a href="#tag">tag</a> &lt;name&gt;
      --<a href="#tag">frame-tag</a> &lt;name&gt;       在表中包含被标记的帧
      --<a href="#frame-range">frame-range</a> from,to    只导出在[from,to]范围内的帧
      --<a href="#ignore-empty">ignore-empty</a>           不导出空帧或赛璐珞
      --<a href="#merge-duplicates">merge-duplicates</a>       合并精灵表中的重复帧
      --<a href="#border-padding">border-padding</a> &lt;value&gt; 在纹理边界添加边距
      --<a href="#shape-padding">shape-padding</a> &lt;value&gt;  在帧之间添加边距
      --<a href="#inner-padding">inner-padding</a> &lt;value&gt;  在每个帧内添加边距
      --<a href="#trim">trim</a>                   对于 --save-as 剪裁整个精灵，对于 --sheet，剪裁独立帧
      --<a href="#trim-sprite">trim-sprite</a>            剪裁整个精灵 (对于 --save-as 和 --sheet)
      --<a href="#extrude">extrude</a>                挤压所有图像重复边界为 1 像素
      --<a href="#crop">crop</a> x,y,width,height  修剪所有图像到指定的矩形
      --<a href="#slice">slice</a> &lt;name&gt;           修剪精灵到指定的切片区域
      --<a href="#filename-format">filename-format</a> &lt;fmt&gt;  生成文件名的特殊格式
      --<a href="#tagname-format">tagname-format</a> &lt;fmt&gt;   生成 JSON 数据标签名的特殊格式
      --<a href="#script">script</a> &lt;filename&gt;      执行指定的脚本
      --<a href="#script-param">script-param</a> name=value
                               CLI 执行脚本的才输，其中包含 app.params
      --<a href="#list-layers">list-layers</a>            列出给定精灵的图层或 JSON 数据包含的图层
      --<a href="#list-tags">list-tags</a>              列出给定精灵的标签或 JSON 数据包含的帧标签
      --<a href="#list-slices">list-slices</a>            列出给定精灵的切片或 JSON 数据包含的切片
      --<a href="#oneframe">oneframe</a>               加载第一帧
  -v, --<a href="#verbose">verbose</a>                解释当前正在执行的
      --<a href="#debug">debug</a>                  详细信息模式并复制日志到桌面
  -?, --<a href="#help">help</a>                   展示帮助并退出
      --<a href="#version">version</a>                输出版本并退出
</pre>

## --shell

[REPL 模式](https://en.wikipedia.org/wiki/Read%E2%80%93eval%E2%80%93print_loop)运行 Aseprite。在这个模式中，你可以写 Javascript 代码。未来版本，将会更新一个[特定 API](https://github.com/aseprite/api-draft)。

## --batch

运行 Aseprite 但只运行命令行选项，然后结束。如果你想从一个脚本运行 Aseprite 来进行自动的精灵表生成、图像转换等时非常有用。示例：

    aseprite --batch

或者你可以使用缩略形式：

    aseprite -b

## --preview

在**v1.2-beta2**中，只显示成果（不修改磁盘中的文件）。

    aseprite --preview ...

## --save-as

使用给定的文件名保存最新被打开的文档，相当于在界面中使用`File > Save As`。示例：

    aseprite -b sprite.ase --save-as frame001.png

这会生成`frame001.png`、`frame002.png`等`sprite.ase`的帧图像。

在**v1.2-beta1**中，你可以直接指定[--filename-format](#filename-format)参数到文件名中。示例：

    aseprite -b sprite.ase --save-as layer-{layer}-frame-{frame01}.png

这就像分别使用[--split-layers](#split-layers)和[--filename-format](#filename-format)

## --palette

在**v1.2-beta2**中，更改命令中给出的最后一个精灵的调色板。它可以用来用不同的掉色版来保存一个精灵：

    aseprite -b ryu-template.png --palette pal1.png --save-as ryu1.png --palette pal2.png --save-as ryu2.png

在**v1.1**这个参数用于改变默认的程序调色板，但现在可以使用*[Save as Default Palette](default-palette.md)*菜单选项。

## --scale

    aseprite ... --scale FACTOR

根据给定的`FACTOR`重新设定在命令行中`--scale`选项前的所有图片的尺寸。示例：

    aseprite -b original.png --scale 2 --save-as image-x2.png

## --dithering-algorithm

    aseprite -b sprite.ase --dithering-algorithm ALGORITHM

抖动算法被用在[--color-mode indexed](#color-mode)命令中，以转换图像从 RGB 模式为索引模式。

- `--dithering-algorithm none`
- `--dithering-algorithm ordered`
- `--dithering-algorithm old`

## --dithering-matrix

    aseprite -b sprite.ase --dithering-matrix MATRIX

抖动矩阵被用在[--dithering-algorithm](#dithering-algorithm)和[--color-mode indexed](#color-mode)命令中，以转换图像从 RGB 模式为索引模式。`MATRIX`可以是：

- `--dithering-matrix bayer8x8`
- `--dithering-matrix bayer4x4`
- `--dithering-matrix bayer2x2`
- 或者已安装插件提供的其它抖动矩阵的标识符（`id`）。

这些默认的抖动矩阵（比如`bayer8x8`）包含在[bayer-matrices](https://github.com/aseprite/aseprite/tree/master/data/extensions/bayer-matrices) Aseprite 插件中，编号则在[packages.json](https://github.com/aseprite/aseprite/blob/master/data/extensions/bayer-matrices/package.json#L10)文件中。

## --color-mode

    aseprite -b sprite.ase --color-mode MODE

改变所有之前打开的精灵的颜色模式为给定的`MODE`。这个`MODE`可以是：

- `--color-mode rgb`
- `--color-mode grayscale`
- `--color-mode indexed`

记得[--dithering-algorithm](#dithering-algorithm)和[--dithering-matrix](#dithering-matrix)会影响 RGB → Indexed 转换。

示例：

```
aseprite -b idx-sprite.ase --color-mode rgb --save-as rgb-output.png
aseprite -b rgb-sprite.ase --dithering-algorithm ordered --dithering-matrix bayer8x8 --color-mode indexed --save-as idx-output.png
```

## --data

    aseprite.exe ... --sheet file.png --data file.json

保存导出精灵表的信息为 JSON 格式。

参见 [--sheet](#sheet) 选项，可以改变精灵表图片的保存位置。

## --format

更改用于剔除[--data](#data)选项指定的精灵表数据的格式。可用的格式有：

- `--format json-hash`（默认格式）（[example](https://gist.github.com/dacap/db18e5747a4b6e208d3c)）
- `--format json-array`（[example](https://gist.github.com/dacap/a32adb9248320326733a)）

## --sheet

    aseprite ... --sheet SPRITESHEET.png

到处所有命令行中在`--sheet`选项之前指定的图片到`SPRITESHEET.png`图像（文件会被覆盖）。

参见[--data](#data)选项，改变精灵表 JSON 数据的目标位置。

## --sheet-width

指定[--sheet](#sheet)指向的精灵表的宽度（像素）。

## --sheet-height

指定[--sheet](#sheet)指向的精灵表的高度（像素）。

## --sheet-type

[--sheet](#sheet)使用的精灵表类型：

- `horizontal`
- `vertical`
- `rows`
- `columns`
- `packed` (和[--sheet-pack](#sheet-pack)相同)

## --sheet-pack

使用一个特殊的打包算法来避免精灵表的存储空间浪费。

## --split-layers

分割命令行中声明的**下一个文档**的可见图层，这样你就可以保存每个图层到一个独立的图像/条目。它影响[--sheet](#sheet)和[--save-as](#save-as)选项。

**警告**: The `--split-layers`选项必须在你的精灵**之前**。

示例:

      aseprite.exe -b --split-layers with-layers.ase --save-as output1.png

记得`--split-layers`必须在`with-layers.ase`之前。在这个示例中，如果`with-layers.ase`有 3 帧，和`Background`与`Layer 1`图层，接下来的命令会生成个文件（每个帧/图层一个文件）：

      output (Background) 1.png
      output (Background) 2.png
      output (Background) 3.png
      output (Layer 1) 1.png
      output (Layer 1) 2.png
      output (Layer 1) 3.png

从**v1.2-beta1**开始，如果你在[--save-as](#save-as)的文件名中指定`{layer}`，`--split-layers`就是隐式使用的。比如：

    aseprite.exe -b with-layers.ase --save-as output-{layer}-{frame}.png

想要保存隐藏的图层，你可以把这个选项和[--all-layers](#all-layers)合并：

    aseprite.exe -b --all-layers with-layers.ase --save-as output-{layer}-{frame}.png

## --split-tags

从**v1.2-beta8**开始，分割下一个文档的标签到不同的文件中。它影响[--save-as](#save-as)选项。如同：

    aseprite.exe -b animations.ase --save-as animations-{tag}.gif

## --split-slices

从**v1.2-beta8**开始，分割下一个文档的切片到不同的文件中。它影响[--save-as](#save-as)选项。如同：

    aseprite.exe -b sheet.ase --save-as part-{slice}.png

## --layer

选择并仅导出一个图层（隐藏所有其它图层）。它影响[--sheet](#sheet)和[--save-as](#save-as)选项。

    aseprite.exe -b --layer "Body Layer" with-layers.ase --save-as body-layer.gif

保存一个仅包含`Body Layer`图层的动画到`body-layer.gif`文件中。

在**v1.2-beta2**，你可以指定多个图层和/或组：

    aseprite.exe -b --layer "head/hat" --layer "body/gloves" player.ase --save-as clothes.gif

保存一个劲包含`hat`图层（`head`组的一个子元素）和`gloves`图层（`body`组的一个子元素）的动画到`clothes.gif`文件中。

## --all-layers

    aseprite -b ... --all-layers ...

在[--save-as](#save-as)/[--sheet](#sheet)操作中包含/显示所有图层。如果你的精灵中包含隐藏的图层但是你想导出他们，你可以使用这个选项。

示例：

    aseprite -b --all-layers player.aseprite --save-as player-{layer}-{frame}.png

## --ignore-layer

    aseprite -b ... --ignore-layer LAYERNAME ...

在[--save-as](#save-as)/[--sheet](#sheet)操作中，在最后的结果/渲染中隐藏一个特定的图层。

你必须在打开`.aseprite`文件前指明这个参数。

示例：

    aseprite -b --ignore-layer "Guides Layer" player.aseprite --save-as player.gif

## --tag

导出帧到给定的标签中。在**v1.1**中，它对[--sheet](#sheet)起效，从**v1.2-beta1**开始，它对[--save-as](#save-as)起效。

示例：

    aseprite -b --tag "Run Cycle" several-animations.ase --save-as run-cycle.gif

## --frame-range

导出在给定`[from, to]`范围内的帧。

## --ignore-empty

忽略空帧/图层。它影响[--sheet](#sheet)选项。

在**v1.2.10-beta3**中，它也影响[--save-as](#save-as)。

## --border-padding

    aseprite ... --border-padding N ...

给整个 N 像素的表引入一个边框。它只影响[--sheet](#sheet)选项。

![Border Padding](cli/border-padding.png)

## --shape-padding

    aseprite ... --shape-padding N ...

在每个 N 像素的帧之前引入一个空格。它只影响[--sheet](#sheet)选项。

![Shape Padding](cli/shape-padding.png)

## --inner-padding

    aseprite ... --inner-padding N ...

在每个 N 像素的帧之前引入一个边框。它只影响[--sheet](#sheet)选项。

![Inner Padding](cli/inner-padding.png)

## --trim

在保存精灵/图层/赛璐珞之前去除它们的边框（相当于每个将要被导出的图像执行*Edit > Trim*）。它影响[--sheet](#sheet)和[--save-as](#save-as)选项。

## --crop

    aseprite ... --crop X,Y,WIDTH,HEIGHT

导出精灵/图层/赛璐珞中指定矩形的部分。它影响[--sheet](#sheet)和[--save-as](#save-as)选项。

## --extrude

从**v1.2-beta21**开始，[--sheet](#sheet)将要导出的图像/精灵边缘复制一个像素。

## --slice

从**v1.2-beta8**开始

    aseprite ... --slice SLICE

仅导出指定剪裁区域。它影响[--save-as](#save-as)选项。

## --filename-format

    aseprite --filename-format FORMAT

这个选项指定一个特殊的字符串，用来设定[--sheet](#sheet)生成的精灵表或[--save-as](#save-as)生成的文件的名称格式。

`FORMAT`字符串可以包含一些特殊值：

- `{fullname}`：原精灵全名（路径 + 文件名 + 扩展名）。
- `{path}`：文件名的路径。 比如，如果精灵文件名是`C:\game-assets\file.ase`，将会得到`C:\game-assets`。
- `{name}`：文件名的名称（包含扩展名）比如，如果精灵文件名是`C:\game-assets\file.ase`，将会得到`file.ase`。
- `{title}`：文件名中不包含扩展名的名称。比如，如果精灵文件名是`C:\game-assets\file.ase`，将会得到`file`。
- `{extension}`：文件名的扩展名。比如，如果精灵文件名是`C:\game-assets\file.ase`，将会得到`ase`。
- `{layer}`：当前图层名。
- `{tag}`：当前标签名。
- `{innertag}`：最小/内部当前标签名。
- `{outertag}`：最大/外部当前标签名。
- `{frame}`：当前帧（从`0`开始 ）。你可以用`{frame1}`从 1 开始，或者其它形式，比如`{frame000}`或`{frame001}`等等。
- `{tagframe}`：当前标签的当前帧。`0`表示当前标签的第一帧，以此类比。和`{frame}`一样，它接受像`{tagframe000}`的变量。
- `{duration}`：当前帧的时长。

比如，如果`animation-with-layers.ase`包含 3 帧和 2 个图层（命名为`Face`和`Background`）：

    aseprite -b animation-with-layers.ase --filename-format '{path}/{title}-{layer}-{frame}.{extension}' --save-as output.png

会生成这样的文件：

    output-Face-0.png
    output-Face-1.png
    output-Face-2.png
    output-Background-0.png
    output-Background-1.png
    output-Background-2.png

在**v1.2-beta1**，你可以用同一个[--save-as](#save-as)参数指定文件名格式。

## --script

    aseprite -script filename.lua

在命令行中执行指定的脚本。

## --script-param

这是一个添加元素到[`app.params`](https://github.com/aseprite/api/blob/master/api/app.md#appparams)表格的方法：

    aseprite -b -script-param key1=value1 -script test.lua

然后`test.lua`

```lua
if app.params["key1"] == "value1" then
  ...
end
```

## --list-layers

    aseprite --list-layers file.ase

打印出给定文件中从底到顶的图层列表。比如：

![Layers](cli/list-layers.png)

    C:\....> aseprite -b --list-layers file.ase
    Background
    Layer 1
    Layer 2

当和[--data](#data)一起被使用是，图层会在 JSON 输出的`meta`属性中获得。比如：

    { "frames": [
      ...
     ],
     "meta": {
      ...,
      "layers": [
       { "name": "Background" },
       { "name": "Layer 1" },
       { "name": "Layer 2" }
      ]
     }
    }

## --list-tags

    aseprite --list-tags file.ase

打印出给定文件中从第一到最后的标签列表。比如：

![Tags](cli/list-tags.png)

    C:\....> aseprite -b --list-tags file.ase
    Walk
    Run

当和[--data](#data)一起被使用是，标签会在 JSON 输出的`meta`属性中获得。比如：

    { "frames": [
      ...
     ],
     "meta": {
      ...,
      "frameTags": [
       { "name": "Walk", "from": 0, "to": 3 },
       { "name": "Run", "from": 4, "to": 6 }
      ]
     }
    }

## --list-slices

从**v1.2-beta8**开始：

    aseprite --list-slices file.ase

打印给定文件的且切片列表。

当和[--data](#data)一起被使用是，切片会在 JSON 输出的`meta`属性中获得。比如：

    { "frames": [
      ...
     ],
     "meta": {
      ...,
      "slices": [
        { "name": "cursor",
          "color": "#0000ffff",
          "keys": [{ "frame": 0,
                     "bounds": {"x": 80, "y": 0, "w": 16, "h": 16 },
                     "center": {"x": 2, "y": 2, "w": 12, "h": 12 },
                     "pivot": {"x": 8, "y": 8 } }] },
        ...
      ]
     }
    }

## --oneframe

    aseprite -b --oneframe frame1.png --save-as frame1.pcx
    aseprite -b --oneframe walk-animation.aseprite --save-as walk-thumbnail.png

在**v1.2-beta4**中，只加载动画的第一帧。只加载动画序列（比如只加载`frame1.png`，即使`frame2.png`、`frame3.png`等存在）的第一帧或只加载整个动画的第一帧（对创建动画的缩略图）很有用。

## --debug

如果你在命令行中使用`--debug`参数执行 Aseprite，一个特别的`Aseprite-v1.1-dev-DebugOutput.txt`的文件会被创建在桌面上，包含可能出现的问题的信息（比如可以用来知道当程序没有正确启动时发生了什么）。

在 Steam 中，你可以[从 Aseprite 属性](http://imgur.com/txXcgzO)添加这个`--debug`选项。

## --verbose

    aseprite --verbose

这会在`aseprite.log`文件中记录更多的信息

- Windows：`aseprite.log`位于`%AppData%\Aseprite\aseprite.log`。
- macOS 和 Linux：`aseprite.log`位于`~/.config/aseprite/aseprite.log`。

## --help

    aseprite --help

在控制台中显示命令行可用选项。

## --version

    aseprite --version

显示 Aseprite 版本。

# 用例

## 转换 Aseprite 文件为 PNG、GIF 等等

    aseprite.exe -b image.ase --save-as image.png
    aseprite.exe -b animation.ase --save-as animation.gif

## 转换一个动画为一组 PNG 文件序列（frame1.png、frame2.png 等等）

    aseprite.exe -b animation.ase --save-as frame1.png

## 重新设定一个精灵的尺寸

    aseprite.exe -b original.ase --scale 2 --save-as output-x2.png
    aseprite.exe -b original.ase --scale 4 --save-as output-x4.png
    aseprite.exe -b original.ase --scale 6 --save-as output-x6.png
    aseprite.exe -b original.ase --scale 8 --save-as output-x8.png

## 导出一个图层到 PNG/GIF 文件

    aseprite.exe -b --layer "Layer 1" animation.ase --save-as output-Layer-1.gif

## 导出所有图层到不同的 PNG/GIF 文件

如果`animation.ase`包含 3 帧和图层`Background`和`Layer 1`，接下来的命令会生成 6 个文件（每帧/图层一个文件）：

    aseprite.exe -b --split-layers animation.ase --save-as output1.png

生成的文件是：

    output (Background) 1.png
    output (Background) 2.png
    output (Background) 3.png
    output (Layer 1) 1.png
    output (Layer 1) 2.png
    output (Layer 1) 3.png

在**v1.2-beta1**中，你可以隐式指定[--split-layers](#split-layers)和[--filename-format](#filename-format)，像这样：

    aseprite.exe -b animation.ase --save-as output-{layer}.png

## 导出一个动画到精灵表

    aseprite.exe -b animation.ase --sheet sheet.png --data sheet.json

## 导出每个图层为一个不同的动画到同一个精灵表

    aseprite.exe -b --split-layers animation-with-layers.ase --sheet sheet.png --data sheet.json

## 从一个精灵导出一个特定的图层

    aseprite.exe -b --layer=Background sprite.ase --sheet sheet.png --data sheet.json

## 从几个精灵创建一个纹理地图

    aseprite.exe -b *.ase --sheet-pack --sheet atlas-bestfit.png --data atlas-bestfit.json
    aseprite.exe -b *.ase --sheet-pack --sheet-width=1024 --sheet-height=1024 --sheet atlas-1024x1024.png --data atlas-1024x1024.json

# 平台特定细节

在 Windows 中，如果你安装了程序，它应该位于`Program Files`文件夹中，尝试这个命令：

    "C:\Program Files (x86)\Aseprite\Aseprite.exe" --help

或者

    "C:\Program Files\Aseprite\Aseprite.exe" --help

在 macOS 中，如果你安装了程序到`/Applications`，尝试下列的命令：

    /Applications/Aseprite.app/Contents/MacOS/aseprite --help

# 自动化过程

## 如果 Aseprite 被直接安装

你可以在资源文件夹（即你的`.ase`文件所在的位置）创建一个`convert.bat`文本文件，包含下列内容：

    @set ASEPRITE="C:\Program Files\Aseprite\aseprite.exe"
    %ASEPRITE% -b animation.ase --scale 2 --save-as animation-x2.gif
    %ASEPRITE% -b animation.ase --scale 4 --save-as animation-x4.gif

每一次你修改`animation.ase`的原始动画，双击`.bat`文件你会从新内容自动生成一个`animation-x2.gif`和一个`animation-x4.gif`文件。

对于 Mac 用户，你可以创建`convert.sh`：

    ASEPRITE="/Applications/Aseprite.app/Contents/MacOS/aseprite"
    $ASEPRITE -b animation.ase --scale 2 --save-as animation-x2.gif
    $ASEPRITE -b animation.ase --scale 4 --save-as animation-x4.gif

## 在 Steam 场景中

Aseprite 二进制文件被安装到下列目录：

- Mac `~/Library/Application Support/Steam/steamapps/common/Aseprite/Aseprite.app/Contents/MacOS/aseprite`
- Windows `C:\Program Files (x86)\Steam\steamapps\common\Aseprite\Aseprite.exe`
- Ubuntu `~/.steam/debian-installation/steamapps/common/Aseprite/aseprite`
