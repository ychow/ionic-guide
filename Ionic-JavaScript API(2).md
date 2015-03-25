## Ionic-JavaScript API


### ion-header-bar

> 这个是固定在屏幕顶部的一个头部标题栏。如果给它加上'bar-subheader' 这个样式，它就是subheader 了。(如果忘记 subheader 是什么了，可以看看之前的CSS API的介绍)。


**HTML:**

```javascript
<!DOCTYPE html>
<html>
  <head>
    <meta charset="utf-8">
    <meta name="viewport" content="initial-scale=1, maximum-scale=1, user-scalable=no, width=device-width">
    <title></title>

    <link href="lib/ionic/css/ionic.css" rel="stylesheet">
    <link href="css/style.css" rel="stylesheet">

    <script src="lib/ionic/js/ionic.bundle.js"></script>

    <script src="js/app.js"></script>
  </head>
    <body ng-app="starter" ng-controller="actionsheetCtl" >
        <ion-header-bar align-title="left" class="bar-positive" no-tap-scroll=true>
          <div class="buttons">
            <button class="button" ng-click="doSomething()">Left Button</button>
          </div>
          <h1 class="title">Title!</h1>
          <div class="buttons">
            <button class="button">Right Button</button>
          </div>
        </ion-header-bar>
        <ion-content>
            <div style="height:2000px">test</div>
        </ion-content>
    </body>
</html>

```

> ion-header-bar 它有两个API。

1. align-title
> 这个是对齐 title 的。如果没有设置，它将会按照手机的默认排版(Ios的默认是居中，Android默认是居左)。它的值可以是 'left','center','right'。

2. no-tap-scroll
> 这个是设置 header-bar 是否跟随着内容的滚动而滚动，就是是否固定在顶部。它的值是布尔值（true/false）。




### ion-footer-bar

> 知道了 ion-header-bar ，理解ion-footer-bar就轻松多啦！只是 ion-footer-bar 是在屏幕的底部。

> 和 ion-header-bar 不同的是，ion-footer-bar 只有 align-title 这个 API。




