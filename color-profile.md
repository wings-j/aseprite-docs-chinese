# 颜色配置文件

我们在屏幕中看到的一个像素是一个有 3 个特定 RGB 值的小矩形，每个值可以被认为是从 0.0 到 1.0 的数字（或是从 0 到 255 的整数）。它表示一个三维控件中的一个位置，每个值表示一个轴（红、绿、蓝）的一个位置。

![RGB Cube](color-profile/rgb-cube.png)

但是一个三维空间中的一个位置代表什么意思呢？我们知道*RGB=(0,0,0)*代表黑色，*RGB=(255,0,0)*代表红色，*RGB=(255,255,255)*代表白色，等等。但是[白色](https://en.wikipedia.org/wiki/White_point)究竟是什么？当你的显示器在被校准并且制造商说*“好吧，这就是白色”*的时候用的是什么环境光？

每一台需要处理颜色的设备（显示器、打印机、照相机、扫描仪，等等）必须被校准以转换环境光为图片中的一些特定 RGB 值，反之亦然，从空间中的 RGB 值转换为[光波](https://en.wikipedia.org/wiki/Light)。

颜色配置文件指明这些 RGB 值处于的[色彩控件](https://en.wikipedia.org/wiki/Color_space)，什么是红，什么是蓝，什么是绿，什么是白。它被用于将一个设备（比如你创建图像的显示器）和其它设备（比如用户用于看你的图片的显示器）的 RGB 值相匹配。

网络图片通常使用[sRGB 色彩控件](https://en.wikipedia.org/wiki/SRGB)，但[PNG 文件](https://en.wikipedia.org/wiki/Portable_Network_Graphics)和[JPEG 文件](https://en.wikipedia.org/wiki/JPEG)可以内嵌一个特定的[ICC 颜色配置文件](https://en.wikipedia.org/wiki/ICC_profile)与它的[RGB 色域](https://en.wikipedia.org/wiki/Gamut)和[伽马校正](https://en.wikipedia.org/wiki/Gamma_correction)。从 Aseprite v1.2.10-beta2 开始，你也可以[保存颜色配置文件到`.aseprite`文件中](https://github.com/aseprite/aseprite/blob/master/docs/ase-file-specs.md#color-profile-chunk-0x2007)。

你可以在[精灵属性](sprite-properties.md)中指定或改变当前精灵的颜色配置文件。并且你可以在*Edit > Preferences > Color*配置 Aseprite 如何管理颜色配置文件：

![Color Management Preferences](color-profile/color-management-preferences.png)

---

**参见**

[颜色](color.md) | [精灵属性](sprite-properties.md)
