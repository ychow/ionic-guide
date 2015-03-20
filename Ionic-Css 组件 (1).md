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

> button的默认情况是按照 display: inline-block 来显示，宽度是随其内部文字长度增长的。

![button](http://7vijqz.com1.z0.glb.clouddn.com/button.png)

