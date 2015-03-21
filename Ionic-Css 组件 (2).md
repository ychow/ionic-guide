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

