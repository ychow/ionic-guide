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




### ion-list 

> 在许多移动应用里面，列表是运用得最广的。ionList 和 ionItem 这两个指令还支持多种多样的交互模式，比如移除其中的某一项，拖动重新排序，滑动编辑等等。


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
        <ion-header-bar class="bar-positive">
              <div class="buttons">
                <button class="button button-icon icon ion-ios-minus-outline"
                  ng-click="data.showDelete = !data.showDelete; data.showReorder = false"></button>
              </div>
              <h1 class="title">Ionic Delete/Option Buttons</h1>
              <div class="buttons">
                <button class="button" ng-click="data.showDelete = false; data.showReorder = !data.showReorder">
                    Reorder
                </button>
              </div>
            </ion-header-bar>

            <ion-content>

              
              <ion-list show-delete="data.showDelete" show-reorder="data.showReorder">

                <ion-item ng-repeat="item in items" 
                          item="item"
                          href="#/item/{{item.id}}" class="item-remove-animate">
                  Item {{ item.id }}
                  <ion-delete-button class="ion-minus-circled" 
                                     ng-click="onItemDelete(item)">
                  </ion-delete-button>
                  <ion-option-button class="button-assertive"
                                     ng-click="edit(item)">
                    Edit
                  </ion-option-button>
                  <ion-option-button class="button-calm"
                                     ng-click="share(item)">
                    Share
                  </ion-option-button>
                  <ion-reorder-button class="ion-navicon" on-reorder="moveItem(item, $fromIndex, $toIndex)"></ion-reorder-button>
                </ion-item>

              </ion-list>

            </ion-content>
              
    </body>
</html>

```


**JavaScript:**

```javascript

angular.module('starter', ['ionic'])

.run(function($ionicPlatform) {
  $ionicPlatform.ready(function() {
    // Hide the accessory bar by default (remove this to show the accessory bar above the keyboard
    // for form inputs)
    if(window.cordova && window.cordova.plugins.Keyboard) {
      cordova.plugins.Keyboard.hideKeyboardAccessoryBar(true);
    }
    if(window.StatusBar) {
      StatusBar.styleDefault();
    }
  });
})

.controller( 'actionsheetCtl',['$scope',function($scope){

    $scope.data = {
        showDelete: false
      };
      
      $scope.edit = function(item) {
        alert('Edit Item: ' + item.id);
      };
      $scope.share = function(item) {
        alert('Share Item: ' + item.id);
      };
      
      $scope.moveItem = function(item, fromIndex, toIndex) {
        $scope.items.splice(fromIndex, 1);
        $scope.items.splice(toIndex, 0, item);
      };
      
      $scope.onItemDelete = function(item) {
        $scope.items.splice($scope.items.indexOf(item), 1);
      };
      
      $scope.items = [
        { id: 0 },
        { id: 1 },
        { id: 2 },
        { id: 3 },
        { id: 4 },
        { id: 5 },
        { id: 6 },
        { id: 7 },
        { id: 8 },
        { id: 9 },
        { id: 10 },
        { id: 11 },
        { id: 12 },
        { id: 13 },
        { id: 14 },
        { id: 15 },
        { id: 16 },
        { id: 17 },
        { id: 18 },
        { id: 19 },
        { id: 20 },
        { id: 21 },
        { id: 22 },
        { id: 23 },
        { id: 24 },
        { id: 25 },
        { id: 26 },
        { id: 27 },
        { id: 28 },
        { id: 29 },
        { id: 30 },
        { id: 31 },
        { id: 32 },
        { id: 33 },
        { id: 34 },
        { id: 35 },
        { id: 36 },
        { id: 37 },
        { id: 38 },
        { id: 39 },
        { id: 40 },
        { id: 41 },
        { id: 42 },
        { id: 43 },
        { id: 44 },
        { id: 45 },
        { id: 46 },
        { id: 47 },
        { id: 48 },
        { id: 49 },
        { id: 50 }
      ];
}])

```

