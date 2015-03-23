## Ionic Css 组件

#### 栈栏

> Ionic 的栈栏和其他大部分框架有所不同，它采用了  Flexible box 。而且在移动端，基本上的手机都支持。row 样式指定行，col 样式指定列。


##### 平均分的 grid

> 在带有 row 的样式的元素里如果包含了 col 的样式，就会默认平均分成几块。

```javascript
<div class="row">
  <div class="col">.col</div>
  <div class="col">.col</div>
  <div class="col">.col</div>
  <div class="col">.col</div>
  <div class="col">.col</div>
</div>
```

![grid](http://7vijqz.com1.z0.glb.clouddn.com/grid.png)


##### 指定列宽

```javascript
<div class="row">
  <div class="col col-50">.col.col-50</div>
  <div class="col">.col</div>
  <div class="col">.col</div>
</div>

<div class="row">
  <div class="col col-75">.col.col-75</div>
  <div class="col">.col</div>
</div>

<div class="row">
  <div class="col">.col</div>
  <div class="col col-75">.col.col-75</div>
</div>

<div class="row">
  <div class="col">.col</div>
  <div class="col">.col</div>
</div>
```

![explicit](http://7vijqz.com1.z0.glb.clouddn.com/explicit-column.png)


> 下面列出了指定列宽的一些百分比的样式名

```javascript
.col-10	    10%
.col-20	    20%
.col-25	    25%
.col-33	    33.3333%
.col-50	    50%
.col-67	    66.6666%
.col-75	    75%
.col-80	    80%
.col-90	    90%
```



##### 有偏移量的grid

```javascript
<div class="row">
  <div class="col col-33 col-offset-33">.col</div>
  <div class="col">.col</div>
</div>

<div class="row">
  <div class="col col-33">.col</div>
  <div class="col col-33 col-offset-33">.col</div>
</div>

<div class="row">
  <div class="col col-33 col-offset-67">.col</div>
</div>
```

![offset-column](http://7vijqz.com1.z0.glb.clouddn.com/offset-column.png)


> 下面是一些百分比的偏移量样式名

```javascript
.col-offset-10	10%
.col-offset-20	20%
.col-offset-25	25%
.col-offset-33	33.3333%
.col-offset-50	50%
.col-offset-67	66.6666%
.col-offset-75	75%
.col-offset-80	80%
.col-offset-90	90%
```


##### 纵向对其的 grid

```javascript
<div class="row">
  <div class="col">.col</div>
  <div class="col">.col</div>
  <div class="col">.col</div>
  <div class="col">1<br>2<br>3<br>4</div>
</div>

<div class="row">
  <div class="col col-top">.col</div>
  <div class="col col-center">.col</div>
  <div class="col col-bottom">.col</div>
  <div class="col">1<br>2<br>3<br>4</div>
</div>

<div class="row row-top">
  <div class="col">.col</div>
  <div class="col">.col</div>
  <div class="col">.col</div>
  <div class="col">1<br>2<br>3<br>4</div>
</div>

<div class="row row-center">
  <div class="col">.col</div>
  <div class="col">.col</div>
  <div class="col">.col</div>
  <div class="col">1<br>2<br>3<br>4</div>
</div>

<div class="row row-bottom">
  <div class="col">.col</div>
  <div class="col">.col</div>
  <div class="col">.col</div>
  <div class="col">1<br>2<br>3<br>4</div>
</div>
```

![vertically-column](http://7vijqz.com1.z0.glb.clouddn.com/vertically-column.png)



##### 响应式 grid

```javascript
<div class="row responsive-sm">
  <div class="col">.col</div>
  <div class="col">.col</div>
  <div class="col">.col</div>
  <div class="col">.col</div>
</div>
```

![responsive-grid](http://7vijqz.com1.z0.glb.clouddn.com/responsive-grid.png)



#### 颜色

> Ionic 提供了很多颜色的配置，当然你可以根据自己的需要自定义颜色。

![color](http://7vijqz.com1.z0.glb.clouddn.com/color.png)


#### 图标

> Ionic 也默认提供了许多的图标，大概有500多个。用法也非常的简单：

```javascript
<i class="icon ion-star"></i>
```

> 要查找到全部的 Ionic 的图标，可以去 [ionicons](http://ionicons.com/) 查看。


