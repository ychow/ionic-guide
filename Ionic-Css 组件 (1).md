## Ionic Css 组件

#### Header

> Header是固定在屏幕顶部的组件,可以包如标题和左右的功能按钮。Ionic 默认提供了许多种颜色样式，你可以调用不同的样式名。当然也可以自定义一个。


```javascript
<div class="bar bar-header bar-calm">
  <h1 class="title">bar-calm</h1>
</div>
```

![header-calm](http://7vijqz.com1.z0.glb.clouddn.com/header.png)


#### Sub Header

> Sub Header同样是固定在顶部，只是是在Header的下面，就算没有写Header这个，Sub Header这个样式也会距离顶部有一个Header的距离。颜色样式同 Header 。

```javascript
<div class="bar bar-header bar-calm">
    <div class="h1 title">Header</div>
</div>
<div class="bar bar-subheader bar-dark">
    <div class="h2 title">Sub Header</div>
</div>
```

![sub-header](http://7vijqz.com1.z0.glb.clouddn.com/subheader.png)


#### Footer

> Footer 同上面的 Header，只是把样式名 bar-header 换做 bar-footer 。当然，footer 是在屏幕的最下方。

```javascript
<div class="bar bar-footer bar-calm">
  <button class="button button-clear">Left</button>
    <div class="title">Title</div>
  <button class="button button-clear">Right</button>
</div>
```

![Footer](http://7vijqz.com1.z0.glb.clouddn.com/footer.png)


#### Button

 1. button的默认情况是按照 display: inline-block 来显示，宽度是随其内部文字长度增长的。

```javascript
<button class="button">
  Default
</button>
<button class="button button-light">
  button-light
</button>
<button class="button button-stable">
  button-stable
</button>
<button class="button button-positive">
  button-positive
</button>
<button class="button button-calm">
  button-calm
</button>
<button class="button button-balanced">
  button-balanced
</button>
<button class="button button-energized">
  button-energized
</button>
<button class="button button-assertive">
  button-assertive
</button>
<button class="button button-royal">
  button-royal
</button>
<button class="button button-dark">
  button-dark
</button>
```

![button](http://7vijqz.com1.z0.glb.clouddn.com/button.png)


2. 如果想让button占满父元素宽度，需要加上 button-block 样式

```javascript
<button class="button button-block button-positive">
  Block Button
</button>
```
![button-block](http://7vijqz.com1.z0.glb.clouddn.com/button-block.png)


3. 如果是想让 button 100%撑满整个屏幕宽度，并且去掉任何边框以及圆角，当然了父元素也必须没有任何 padding

```javascript
<button class="button button-full button-positive">
  Full Width Block Button
</button>
```
![button-full](http://7vijqz.com1.z0.glb.clouddn.com/button-full.png)


4. ionic 默认也为 button 提供了不同的大小样式。button-large 和 button-small

```javascript
<button class="button button-small button-assertive">
  Small Button
</button>
<button class="button button-large button-positive">
  Large Button
</button>
```

![button-size](http://7vijqz.com1.z0.glb.clouddn.com/button-size.png)


5. 还有只显示框线的button-----button-outline

```javascript
<button class="button button-outline button-positive">
  Outlined Button
</button>
```

![button-outline](http://7vijqz.com1.z0.glb.clouddn.com/button-outline.png)


6. 不显示边框的 button 样式--- button-clear

```javascript
<button class="button button-clear button-positive">
  Clear Button
</button>
```

![button-clear](http://7vijqz.com1.z0.glb.clouddn.com/button-clear.png)


7. 带icon的button，可以控制icon的位置

```javascript
<button class="button">
  <i class="icon ion-loading-c"></i> Loading...
</button>

<button class="button icon-left ion-home">Home</button>

<button class="button icon-left ion-star button-positive">Favorites</button>

<a class="button icon-right ion-chevron-right button-calm">Learn More</a>

<a class="button icon-left ion-chevron-left button-clear button-dark">Back</a>

<button class="button icon ion-gear-a"></button>

<a class="button button-icon icon ion-settings"></a>

<a class="button button-outline icon-right ion-navicon button-balanced">Reorder</a>
```

![icon-button](http://7vijqz.com1.z0.glb.clouddn.com/icon-button.png)


8. 我们也可以在 Header 上面添加按钮，并且可以把按钮放在左右两边，常用于导航按钮。

```javascript
<div class="bar bar-header">
  <button class="button icon ion-navicon"></button>
  <h1 class="title">Header Buttons</h1>
  <button class="button">Edit</button>
</div>
```

![icon-nav](http://7vijqz.com1.z0.glb.clouddn.com/button-nav.png)



9. 一组 button

```javascript
<div class="button-bar bar-positive">
  <a class="button">First</a>
  <a class="button">Second</a>
  <a class="button">Third</a>
</div>
```

![buttons](http://7vijqz.com1.z0.glb.clouddn.com/buttons.png)



#### List


> 列表默认会为每一个 li 有一个 border-bottom 的样式。默认代码：

```javascript
<ul class="list">
    <li class="item">
      	list1
    </li>
    <li class="item">
      	list1
    </li>
    <li class="item">
      	list1
    </li>
    <li class="item">
      	 list1
    </li>
</ul>
```

![list](http://7vijqz.com1.z0.glb.clouddn.com/list.png)



##### List 分栏


> 为列表的任何一个子元素添加 item-divider 样式,就可以实现分栏的效果。

```javascript
<ul class="list">
 <li class="item item-divider">
    Title
  </li>
  <li class="item">
    list1
  </li>
  <li class="item item-divider">
    Title
  </li>
  <li class="item">
    list1
  </li>
</ul>
```


![list-divider](http://7vijqz.com1.z0.glb.clouddn.com/list-divider.png)


##### 列表图标

> 在list 中可以给每一个有 item 样式的添加 icons，并且可以通过添加**item-icon-left**排在左边，或者添加**item-icon-right** 排在右边。

```javascript
<div class="list">

  <a class="item item-icon-left" href="#">
    <i class="icon ion-email"></i>
    Check mail
  </a>

  <a class="item item-icon-left item-icon-right" href="#">
    <i class="icon ion-chatbubble-working"></i>
    Call Ma
    <i class="icon ion-ios7-telephone-outline"></i>
  </a>

  <a class="item item-icon-left" href="#">
    <i class="icon ion-mic-a"></i>
    Record album
    <span class="item-note">
      Grammy
    </span>
  </a>

  <a class="item item-icon-left" href="#">
    <i class="icon ion-person-stalker"></i>
    Friends
    <span class="badge badge-assertive">0</span>
  </a>

</div>
```

![list-icon](http://7vijqz.com1.z0.glb.clouddn.com/list-icon.png)


##### 列表按钮

> 可以通过添加**item-button-right** 或者 **item-button-left** 来让 item 里面的按钮排在左右

```javascript
<div class="list">
  <div class="item item-button-right">
    Call Ma
    <button class="button button-positive">
      <i class="icon ion-ios7-telephone"></i>
    </button>
  </div>
</div>
```

![list-button](http://7vijqz.com1.z0.glb.clouddn.com/list-button.png)


> 带有头像的 item 。可以添加 **item-avatar** 样式


```javascript
<div class="list">
    <a class="item item-avatar" href="#">
      <img src="venkman.jpg">
      <h2>Venkman</h2>
      <p>Back off, man. I'm a scientist.</p>
    </a>
</div>
```

![item-avatar](http://7vijqz.com1.z0.glb.clouddn.com/list-avatar.png)



> 带有缩略图的 item 。注意**item-thumbnail-left** 和 **item-thumbnail-right** 样式，可以指定缩略图不同的显示位置。

```javascript
<div class="list">
    <a class="item item-thumbnail-left" href="#">
      <img src="cover.jpg">
      <h2>Pretty Hate Machine</h2>
      <p>Nine Inch Nails</p>
    </a>
</div>
```


![item-thumbnail](http://7vijqz.com1.z0.glb.clouddn.com/list-thumbnail.png)


> 表格样式的list，这个主要是有了margin的样式，显示两边的框线。注意样式list list-inset。


```javascript
<div class="list list-inset">
    <div class="item">
      Raiders of the Lost Ark
    </div>
</div>
```


![list-inset](http://7vijqz.com1.z0.glb.clouddn.com/list-inset.png)






> Ionic CSS 组件(1) 完结    2015/3/22
