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

 * button的默认情况是按照 display: inline-block 来显示，宽度是随其内部文字长度增长的。

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


* 如果想让button占满父元素宽度，需要加上 button-block 样式

```javascript
<button class="button button-block button-positive">
  Block Button
</button>
```
![button-block](http://7vijqz.com1.z0.glb.clouddn.com/button-block.png)

* 如果是想让 button 100%撑满整个屏幕宽度，并且去掉任何边框以及圆角，当然了父元素也必须没有任何 padding

```javascript
<button class="button button-full button-positive">
  Full Width Block Button
</button>
```
![button-full](http://7vijqz.com1.z0.glb.clouddn.com/button-full.png)
