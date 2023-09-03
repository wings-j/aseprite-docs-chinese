# 新帧

你可以这样添加新帧：

- _Frame > New Frame_（<kbd>Alt+N</kbd>）在下一个位置创建当前帧的副本.
- _Frame > New Empty Frame_（<kbd>Alt+B</kbd>）：创建一个新的空帧（[透明图层](layers.md#transparent-layers)创建一个空赛璐珞，[背景图层](layers.md#background-layer)使用激活背景色填充）。
- _Frame > Duplicated Cels_（<kbd>Alt+D</kbd>）：复制当前赛璐珞，或者创建当前时间线选区，到下一个位置/帧。
- _Frame > Duplicated Linked Cels_（<kbd>Alt+Shift+D</kbd> or <kbd>Alt+M</kbd>）：创建链接到当前赛璐珞（或者当前时间线选择去）到下一个位置/帧。

状态栏的小`+`符号可以用来添加新帧（如同按下<kbd>Alt+N</kbd>）。

![New Frame Button](new-frame/new-frame-button.png)

## 新帧

使用*View > New Frame*（<kbd>Alt+N</kbd>）创建一个当前帧的副本。对于[连续图层](continuous-layers.md)，赛璐珞会被[链接](linked-cels.md)。

## 新空帧

当用<kbd>Alt+B</kbd>添加新帧时，所有[透明图层](layers.md#transparent-layers)都不会包含赛璐珞，[背景图层](layers.md#background-layer)会被用[背景色](color-bar.md#background-color)清除。

当你[移动](move-cels.md)或者[复制赛璐珞](copy-cels.md)到动画末尾的时候，会创建空帧。
