## Ionic Css 组件

#### Cards

> card是一种内容整洁并且涵盖丰富的表现形式，在应用中使用的越来越多。card默认样式带有box-shadow，由于性能的原因，和他类似的元素像list list-inset 并没有shadow。如果你有很多的card，每个card都有很多子元素，建议使用inset list。下面是一个简单的带有footer和header的card。

```javascript
<div class="card">
  <div class="item item-divider">
    I'm a Header in a Card!
  </div>
  <div class="item item-text-wrap">
    This is a basic Card with some text.
  </div>
  <div class="item item-divider">
    I'm a Footer in a Card!
  </div>
</div>
```

![card](http://7vijqz.com1.z0.glb.clouddn.com/card.png)



> 使用**list-card** 样式来创建一个列表卡片。


```javascript
<div class="list card">

  <a href="#" class="item item-icon-left">
    <i class="icon ion-home"></i>
    Enter home address
  </a>

  <a href="#" class="item item-icon-left">
    <i class="icon ion-ios7-telephone"></i>
    Enter phone number
  </a>

  <a href="#" class="item item-icon-left">
    <i class="icon ion-wifi"></i>
    Enter wireless password
  </a>

  <a href="#" class="item item-icon-left">
    <i class="icon ion-card"></i>
    Enter card information
  </a>

</div>
```


![list-card](http://7vijqz.com1.z0.glb.clouddn.com/list-card.png)



> 虽然在卡片里面包含图片显得非常大，但是 Ionic 中图片可以很好的和列表以及其他的元素相结合。

```javascript
<div class="list card">

  <div class="item item-avatar">
    <img src="avatar.jpg">
    <h2>Pretty Hate Machine</h2>
    <p>Nine Inch Nails</p>
  </div>

  <div class="item item-image">
    <img src="cover.jpg">
  </div>

  <a class="item item-icon-left assertive" href="#">
    <i class="icon ion-music-note"></i>
    Start listening
  </a>

</div>
```

![card-image](http://7vijqz.com1.z0.glb.clouddn.com/card-img.png)



> 这里有一个 card 的综合案例。


```javascript
<div class="list card">

  <div class="item item-avatar">
    <img src="mcfly.jpg">
    <h2>Marty McFly</h2>
    <p>November 05, 1955</p>
  </div>

  <div class="item item-body">
    <img class="full-image" src="delorean.jpg">
    <p>
      This is a "Facebook" styled Card. The header is created from a Thumbnail List item,
      the content is from a card-body consisting of an image and paragraph text. The footer
      consists of tabs, icons aligned left, within the card-footer.
    </p>
    <p>
      <a href="#" class="subdued">1 Like</a>
      <a href="#" class="subdued">5 Comments</a>
    </p>
  </div>

  <div class="item tabs tabs-secondary tabs-icon-left">
    <a class="tab-item" href="#">
      <i class="icon ion-thumbsup"></i>
      Like
    </a>
    <a class="tab-item" href="#">
      <i class="icon ion-chatbox"></i>
      Comment
    </a>
    <a class="tab-item" href="#">
      <i class="icon ion-share"></i>
      Share
    </a>
  </div>

</div>
```


![card](http://7vijqz.com1.z0.glb.clouddn.com/cards.png)



#### 表单和输入框


##### 输入框属性：placeholder

```javascript
<div class="list">
  <label class="item item-input">
    <input type="text" placeholder="First Name">
  </label>
  <label class="item item-input">
    <input type="text" placeholder="Last Name">
  </label>
  <label class="item item-input">
    <textarea placeholder="Comments"></textarea>
  </label>
</div>
```

![input-placeholder](http://7vijqz.com1.z0.glb.clouddn.com/input-placeholder.png)



##### 带有标签的输入框

```javascript
<div class="list">
  <label class="item item-input">
    <span class="input-label">Username</span>
    <input type="text">
  </label>
  <label class="item item-input">
    <span class="input-label">Password</span>
    <input type="password">
  </label>
</div>
```

![inputinline](http://7vijqz.com1.z0.glb.clouddn.com/inline-label.png)



##### 堆栈式的表单

```javascript
<div class="list">
  <label class="item item-input item-stacked-label">
    <span class="input-label">First Name</span>
    <input type="text" placeholder="John">
  </label>
  <label class="item item-input item-stacked-label">
    <span class="input-label">Last Name</span>
    <input type="text" placeholder="Suhr">
  </label>
  <label class="item item-input item-stacked-label">
    <span class="input-label">Email</span>
    <input type="text" placeholder="john@suhr.com">
  </label>
</div>
```

![stacked-labels](http://7vijqz.com1.z0.glb.clouddn.com/stack-label.png)


##### 动态显示标签的堆栈式表单

> 动态顾名思义就是有一个动画的效果，个人感觉动画蛮流畅的，而且比较新颖！

```javascript
<div class="list">
  <label class="item item-input item-floating-label">
    <span class="input-label">First Name</span>
    <input type="text" placeholder="First Name">
  </label>
  <label class="item item-input item-floating-label">
    <span class="input-label">Last Name</span>
    <input type="text" placeholder="Last Name">
  </label>
  <label class="item item-input item-floating-label">
    <span class="input-label">Email</span>
    <input type="text" placeholder="Email">
  </label>
</div>
```

![floating-labels](http://7vijqz.com1.z0.glb.clouddn.com/float-label.png)



##### 带padding的 inset form

```javascript
<div class="list list-inset">
  <label class="item item-input">
    <input type="text" placeholder="First Name">
  </label>
  <label class="item item-input">
    <input type="text" placeholder="Last Name">
  </label>
</div>
```

![inset-form](http://7vijqz.com1.z0.glb.clouddn.com/inset-form.png)


##### 内嵌 input 

> 使用 item-input-inset 样式可以内嵌一个按钮

```javascript
<div class="list">

  <div class="item item-input-inset">
    <label class="item-input-wrapper">
      <input type="text" placeholder="Email">
    </label>
    <button class="button button-small">
      Submit
    </button>
  </div>

</div>
```

![inset-input](http://7vijqz.com1.z0.glb.clouddn.com/inset-input.png)


##### 带有标签的input

> 如果想在 input 里面增加一个 icon ，可以添加 item-input 样式。

```javascript
<div class="list list-inset">
  <label class="item item-input">
    <i class="icon ion-search placeholder-icon"></i>
    <input type="text" placeholder="Search">
  </label>
</div>
```

![icon-input](http://7vijqz.com1.z0.glb.clouddn.com/icon-input.png)



##### 顶部输入框

> 还可以在带有 bar-header 样式的元素里面添加输入框。

```javascript
<div class="bar bar-header item-input-inset">
  <label class="item-input-wrapper">
    <i class="icon ion-ios7-search placeholder-icon"></i>
    <input type="search" placeholder="Search">
  </label>
  <button class="button button-clear">
    Cancel
  </button>
</div>
```

![header-input](http://7vijqz.com1.z0.glb.clouddn.com/header-input.png)




#### Toggle

> toggle是一种比较容易操作的多选框，类似于checkbox。这里是用label标签包裹toggle组件，为了是更容易操作。

```javascript
<ul class="list">

  <li class="item item-toggle">
     HTML5
     <label class="toggle toggle-assertive">
       <input type="checkbox">
       <div class="track">
         <div class="handle"></div>
       </div>
     </label>
  </li>

  ...

</ul>
```

![toggle](http://7vijqz.com1.z0.glb.clouddn.com/toggle.png)
