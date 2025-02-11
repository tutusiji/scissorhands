## 灵活的图片拼接合并工具——剪刀手

### 技术栈：vue3 + typescript

### 设计思路：
1. 图片上传：上传一张或者多张图片。
2. 图片拼接：使用Canvas API来加载、拼接图片，等图片加载完成之后，沿y轴等比例的拼接绘制到canvas上面，canvas宽度固定，并且canvas的画布要根据最终拼接的图片长度来拓展。
3. 画线并拖动：在Canvas上画一条线并使其可沿y轴拖动，图片上传拼接完成之后，在canvas上绘制一条线条，该线条宽度等于canvas宽度，高度为2px，可以沿着y轴拖动，x轴固定。
4. 切割Canvas图像：根据线条的位置将Canvas切割成上下两部分，当拖动完线条之后，记录下y轴的位置，点击一个按钮，将canvas图像按照线条最终的位置切割成上下两块图像元素，还是在canvas中显示，之后线条不可再拖动。
5. 图像拖动：使切割后的图像沿y轴可拖动，且有界限控制。切割为上下两块之后，上下两块是可以且只能沿着y轴拖动的，选中任意一块进行上下拖动图像时，如果是向着线条的方向拖动则会隐藏掉越过线条的部分图像，反向拖动时再显示出来，但是反向拖动的最大边界就是该图像和线条初始时的位置。
6. 合成最终图像：提供一个按钮来合成并保存最终图像，点击一个合成按钮，保存最后拖动的图片，其中要去掉线条，线条不显示在图像上。
7. 自适应Canvas宽度：根据设备宽度设置Canvas宽度。