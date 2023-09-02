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

Exports the frames inside the given tag only. It works for
[--sheet](#sheet) on **v1.1**, and it works for [--save-as](#save-as) since
**v1.2-beta1**.

Example:

    aseprite -b --tag "Run Cycle" several-animations.ase --save-as run-cycle.gif

## --frame-range

Exports the frames inside the given `[from, to]` range only.

## --ignore-empty

Ignores empty frames/layers. It affects [--sheet](#sheet) option.

On **v1.2.10-beta3**: It affects [--save-as](#save-as) too.

## --border-padding

    aseprite ... --border-padding N ...

Includes a border for the whole sheet of N pixels. It affects [--sheet](#sheet) option only.

![Border Padding](cli/border-padding.png)

## --shape-padding

    aseprite ... --shape-padding N ...

Includes a separation between each frame of N pixels. It affects [--sheet](#sheet) option only.

![Shape Padding](cli/shape-padding.png)

## --inner-padding

    aseprite ... --inner-padding N ...

Includes a border to each frame of N pixels. It affects [--sheet](#sheet) option only.

![Inner Padding](cli/inner-padding.png)

## --trim

Removes borders from sprites/layers/cels before save
them. (I.e. executes the _Edit > Trim_ option for each image to be
exported.) It affects [--sheet](#sheet) and [--save-as](#save-as)
options.

## --crop

    aseprite ... --crop X,Y,WIDTH,HEIGHT

Exports only the specified rectangle from all sprites/layers/cels. It
affects [--sheet](#sheet) and [--save-as](#save-as) options.

## --extrude

Since **v1.2-beta21**: Extrudes all images/sprites that are going to
be exported with [--sheet](#sheet) duplicating all edges one pixel.

## --slice

Since **v1.2-beta8**:

    aseprite ... --slice SLICE

Exports only the area specified by the given slice. It affects
[--save-as](#save-as) option.

## --filename-format

    aseprite --filename-format FORMAT

This option specifies the special string used to format filenames
generated in sprite sheets on [--sheet](#sheet) or files generated on
[--save-as](#save-as).

The `FORMAT` string can contain some special values:

- `{fullname}`: Original sprite full filename (path + file + extension).
- `{path}`: Path of the filename. E.g. If the sprite filename is `C:\game-assets\file.ase` this will be `C:\game-assets`.
- `{name}`: Name (including extension) of the filename. E.g. If the sprite filename is `C:\game-assets\file.ase` this will be `file.ase`.
- `{title}`: Name without extension of the filename. E.g. If the sprite filename is `C:\game-assets\file.ase` this will be `file`.
- `{extension}`: Extension of the filename. E.g. If the sprite filename is `C:\game-assets\file.ase` this will be `ase`.
- `{layer}`: Current layer name.
- `{tag}`: Current tag name.
- `{innertag}`: Smallest/inner current tag name.
- `{outertag}`: Largest/outer current tag name.
- `{frame}`: Current frame (starting from `0`). You can use `{frame1}` to start from 1, or other formats like `{frame000}`, or `{frame001}`, etc.
- `{tagframe}`: The current frame in the current tag. It's `0` for the first frame of the tag, and so on. Same as `{frame}`, it accepts variants like `{tagframe000}`.
- `{duration}` The duration of the current frame.

For example, if `animation-with-layers.ase` contains three frames with two layers (named `Face` and `Background`):

    aseprite -b animation-with-layers.ase --filename-format '{path}/{title}-{layer}-{frame}.{extension}' --save-as output.png

Will generate files like:

    output-Face-0.png
    output-Face-1.png
    output-Face-2.png
    output-Background-0.png
    output-Background-1.png
    output-Background-2.png

On **v1.2-beta1**: You can specify the filename format in the same
[--save-as](#save-as) argument.

## --script

    aseprite -script filename.lua

Executes the given script from the command line.

## --script-param

This is a way to add elements to the [`app.params`](https://github.com/aseprite/api/blob/master/api/app.md#appparams) table:

    aseprite -b -script-param key1=value1 -script test.lua

And then `test.lua`

```lua
if app.params["key1"] == "value1" then
  ...
end
```

## --list-layers

    aseprite --list-layers file.ase

Prints the list of layers in the given file from bottom to top. E.g.

![Layers](cli/list-layers.png)

    C:\....> aseprite -b --list-layers file.ase
    Background
    Layer 1
    Layer 2

When used with [--data](#data), the layers will be available in the
JSON output in the `meta` attribute. E.g.

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

Prints the list of tags in the given file from the first one to the last one. E.g.

![Tags](cli/list-tags.png)

    C:\....> aseprite -b --list-tags file.ase
    Walk
    Run

When used with [--data](#data), the tags will be available in the JSON
output in the `meta` attribute. E.g.

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

Since **v1.2-beta8**:

    aseprite --list-slices file.ase

Prints the list of slices in the given file.

When used with [--data](#data), slices will be available in the JSON
output in the `meta` attribute. E.g.

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

On **v1.2-beta4**: Load just the first frame of the animation. It's
useful to load just one frame in a image sequence (e.g. loading just
`frame1.png` in case that `frame2.png`, `frame3.png`, etc. exist) or
to load just the first frame of a full animation (e.g. useful to
create a thumbnail of the animation).

## --debug

If you execute Aseprite with the `--debug` parameter in the command
line, a special `Aseprite-v1.1-dev-DebugOutput.txt` file will be
created in your desktop with possible useful information to know what
problem is going on (e.g. this is useful to know what is going on in
case that the program don't start correctly).

On Steam, you can add this `--debug` option [from the Aseprite
properties](http://imgur.com/txXcgzO).

## --verbose

    aseprite --verbose

It will log more information in the `aseprite.log` file:

- On Windows: `aseprite.log` is located in `%AppData%\Aseprite\aseprite.log`
- On macOS and Linux: `aseprite.log` is located in `~/.config/aseprite/aseprite.log`

## --help

    aseprite --help

Shows available command line options in the console output.

## --version

    aseprite --version

Shows Aseprite version.

# Use Cases

## Convert Aseprite files into PNG, GIF, etc.

    aseprite.exe -b image.ase --save-as image.png
    aseprite.exe -b animation.ase --save-as animation.gif

## Convert an animation to a sequence of PNG files (frame1.png, frame2.png, etc.)

    aseprite.exe -b animation.ase --save-as frame1.png

## Resize one sprite to several dimensions

    aseprite.exe -b original.ase --scale 2 --save-as output-x2.png
    aseprite.exe -b original.ase --scale 4 --save-as output-x4.png
    aseprite.exe -b original.ase --scale 6 --save-as output-x6.png
    aseprite.exe -b original.ase --scale 8 --save-as output-x8.png

## Export one layers to PNG/GIF files

    aseprite.exe -b --layer "Layer 1" animation.ase --save-as output-Layer-1.gif

## Export all layers into different PNG/GIF files

If `animation.ase` contains 3 frames and layers `Background` and `Layer 1`,
the following command will generate 6 files (one for each frame/layer):

    aseprite.exe -b --split-layers animation.ase --save-as output1.png

Generated files will be:

    output (Background) 1.png
    output (Background) 2.png
    output (Background) 3.png
    output (Layer 1) 1.png
    output (Layer 1) 2.png
    output (Layer 1) 3.png

On **v1.2-beta1**: You can specify [--split-layers](#split-layers) and
[--filename-format](#filename-format) implicity using something like:

    aseprite.exe -b animation.ase --save-as output-{layer}.png

## Export an animation to a sprite sheet

    aseprite.exe -b animation.ase --sheet sheet.png --data sheet.json

## Export each layer as a different animation in the same sprite sheet

    aseprite.exe -b --split-layers animation-with-layers.ase --sheet sheet.png --data sheet.json

## Export a specific layer from a sprite

    aseprite.exe -b --layer=Background sprite.ase --sheet sheet.png --data sheet.json

## Create a texture atlas from several sprites

    aseprite.exe -b *.ase --sheet-pack --sheet atlas-bestfit.png --data atlas-bestfit.json
    aseprite.exe -b *.ase --sheet-pack --sheet-width=1024 --sheet-height=1024 --sheet atlas-1024x1024.png --data atlas-1024x1024.json

# Platform-specific Details

On Windows, if you've installed the program it should be located
`Program Files` folder, try this command:

    "C:\Program Files (x86)\Aseprite\Aseprite.exe" --help

Or

    "C:\Program Files\Aseprite\Aseprite.exe" --help

On macOS, if you've installed the program in `/Applications`, try the following command:

    /Applications/Aseprite.app/Contents/MacOS/aseprite --help

# Automating the process

## If Aseprite was installed directly

You could create a `convert.bat` text file in your assets directory
(i.e. where your `.ase` files are located) with some lines like these:

    @set ASEPRITE="C:\Program Files\Aseprite\aseprite.exe"
    %ASEPRITE% -b animation.ase --scale 2 --save-as animation-x2.gif
    %ASEPRITE% -b animation.ase --scale 4 --save-as animation-x4.gif

So each time you modify the original animation in `animation.ase`,
double clicking the `.bat` file you could generate `animation-x2.gif` and
`animation-x4.gif` automatically from the new content.

For Mac users, you could create a `convert.sh`:

    ASEPRITE="/Applications/Aseprite.app/Contents/MacOS/aseprite"
    $ASEPRITE -b animation.ase --scale 2 --save-as animation-x2.gif
    $ASEPRITE -b animation.ase --scale 4 --save-as animation-x4.gif

## In the case of Steam

Aseprite binary is installed in the following directories.

- Mac `~/Library/Application Support/Steam/steamapps/common/Aseprite/Aseprite.app/Contents/MacOS/aseprite`
- Windows `C:\Program Files (x86)\Steam\steamapps\common\Aseprite\Aseprite.exe`
- Ubuntu `~/.steam/debian-installation/steamapps/common/Aseprite/aseprite`
