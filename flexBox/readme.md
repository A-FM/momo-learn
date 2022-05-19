[TOC]
# 弹性盒子

标签（空格分隔）： CSS

---


**Flex Box:** 用于适配不同屏幕大小，以确保在不同设备上仍然有预期内美观、大方的布局。

## 基本概念

采用Flex布局的元素，称为Flex容器，简称”容器”。它的所有子元素自动成为容器成员，称为Flex项目，简称”项目”。
![此处输入图片的描述][1]
其中需要注意`main axis`、`cross axis`、`main start`、`main end`、`cross start`、`cross end`的这些概念。


### 弹性盒子

**弹性盒子：**主要包括**弹性容器**和**弹性子元素组成**。
**使用方法：**通过设置`display`属性的值为`flex`或`inline-flex`将其定义为弹性容器。
**注意事项：**弹性容器外以及弹性子元素内是正常渲染的。弹性盒子只定义了弹性子元素如何在弹性容器内布局。常见的浏览器内核有Trident、 Gecko、 Webkit、 Presto、 Blink五种，在`Webkit`浏览器中我们需要加上-webkit前缀。
```CSS
.box{
  display: -webkit-flex; /* Safari */
  display: flex;
}
```
[以此处为例][2]`flex-item`就是`flex-container`的子元素，其中的排列默认为从左到右。我们可以通过指定`flex-direction`的[方法][3]将其改变位置

##容器的属性

### flex-direction

其主要决定主轴（`main axis`）的方向，其默认值为`row`。
![此处输入图片的描述][4]
可选值为：
1. `row`：主轴为水平方向，`main start`在左端。
2. `row-reverse`:主轴为水平方向，`main start`在右端。
3. `column`：主轴为垂直方向、起点在上沿。
4. `column-reverse`：主轴为垂直方向、起点在下沿。

### flex-wrap

默认情况下所有的`item`都排列在`main axis`上，当一条轴线排不下的时候，该如何换行？


可选项为：
1. `nowrap`：不换行其效果如下
![](https://github.com/A-FM/momo-learn/blob/master/flexBox/img/img.png)
![](https://github.com/A-FM/momo-learn/blob/master/flexBox/img/img_3.png)
2. `wrap`：换行且第一行在上方。
![](https://github.com/A-FM/momo-learn/blob/master/flexBox/img/img_1.png)
![](https://github.com/A-FM/momo-learn/blob/master/flexBox/img/img_4.png)
3. `wrap-reverse`：换行，第一行在下方。
![](https://github.com/A-FM/momo-learn/blob/master/flexBox/img/img_2.png)
![](https://github.com/A-FM/momo-learn/blob/master/flexBox/img/img_5.png)

### flex-flow

`flex-flow`属性是`flex-direction`和`flex-wrap`的简写，默认值为`row nowarp`.
```css
.box {
  flex-flow: <flex-direction> <flex-wrap>;
}
```

### justify-content
其定义了项目在主轴上的对齐方式。
```css
.box {
    justify-content: flex-start | flex-end | center | space-between | space-around;
}
```
具体效果如下：
**flex-start**
![](https://github.com/A-FM/momo-learn/blob/master/flexBox/img/img_6.png)

### align-items

其定义项目在交叉轴上如何对齐。

```css
.box {
  align-items: flex-start | flex-end | center | baseline | stretch;
}
```
其属性可选有：
1. `flex-start`：`cross start`对齐

![](https://github.com/A-FM/momo-learn/blob/master/flexBox/img/img_7.png)
2. `flex-end`:`cross end`对齐

![](https://github.com/A-FM/momo-learn/blob/master/flexBox/img/img_8.png)
3. `center`:`cross axis`中点对齐

![](https://github.com/A-FM/momo-learn/blob/master/flexBox/img/img_9.png)
4. `baseline`:项目的第一行文字基线对齐

![](https://github.com/A-FM/momo-learn/blob/master/flexBox/img/img_10.png)
5. `stretch默认值`:如果项目没有设置高度或者为`auto`，将占满整个容器的高度。

![](https://github.com/A-FM/momo-learn/blob/master/flexBox/img/img_11.png)

### align-content

`align-content`:定义了多跟轴线的对齐方式，其基本上和`justify-content`不过本属性是横轴的，`justify-content`是纵轴的。
![](https://github.com/A-FM/momo-learn/blob/master/flexBox/img/img_12.png)

## 项目的属性

### order属性

`order`属性定义项目的排列顺序。数值越小，排列越靠前。
```css
.item {
  order: <integer>;
}
```
![](https://github.com/A-FM/momo-learn/blob/master/flexBox/img/img_13.png)

### flex-grow

```css
.item {
  flex-grow: <number>; /* default 0 */
}
```
![](https://github.com/A-FM/momo-learn/blob/master/flexBox/img/img_14.png)
其默认值为0，即即使container有剩余空间，也不放大。
如果所有项目的`flex-group`都为1，则它们均分剩余空间。
![](https://github.com/A-FM/momo-learn/blob/master/flexBox/img/img_15.png)
![](https://github.com/A-FM/momo-learn/blob/master/flexBox/img/img_16.png)

### flex-shrink
其定义了项目的缩小比例，默认为1，如果空间不足则将该项目缩小。
```css
.item {
  flex-shrink: <number>; /* default 1 */
}
```
如果所有项目的flex-shrink属性都为1，当空间不足时，都将等比例缩小。如果一个项目的flex-shrink属性为0，其他项目都为1，则空间不足时，前者不缩小。
![](https://github.com/A-FM/momo-learn/blob/master/flexBox/img\17.png)














[1]: https://www.runoob.com/wp-content/uploads/2015/07/3791e575c48b3698be6a94ae1dbff79d.png
[2]: https://www.runoob.com/try/try.php?filename=trycss3_flexbox_flexline
[3]: https://www.runoob.com/try/try.php?filename=trycss3_flexbox_direction_row-reverse
[4]: https://www.runoob.com/wp-content/uploads/2015/07/903d5b7df55779c03f2687a7d4d6bcea.png