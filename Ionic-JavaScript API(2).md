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



### ion-delete-button 

> 可以删除 ion-item 。

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
        <ion-list show-delete="shouldShowDelete">
          <ion-item>
            <ion-delete-button class="ion-minus-circled"></ion-delete-button>
            Hello, list item!
          </ion-item>
        </ion-list>
        <ion-toggle ng-model="shouldShowDelete">
          Show Delete?
        </ion-toggle>
              
    </body>
</html>

```

![ion-delete](http://7vijqz.com1.z0.glb.clouddn.com/ion-delete.gif)



### collection-repeat

> 如果列表项目有非常多，你可以使用 collection-repeat ，它的性能比 ng-repeat 好。


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
            <h1 class="title">1000 Items</h1>
          </ion-header-bar>
          <ion-content>
            <ion-list>
              <ion-item collection-repeat="item in main.items">
                {{item}}
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

    $scope.items = [];
      for (var i = 0; i < 1000; i++){
        $scope.items.push(i);
      }
}])

```


![collection-repeat](http://7vijqz.com1.z0.glb.clouddn.com/collection-repeat.png)



### $ionicLoading

> 这个是 Ionic 默认的一个加载交互效果。里面的内容也是可以在 template 里面修改。


**HTML:**

···javascript
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
          <ion-content>
            <h2 ng-click="show()">ionicLoading</h2>
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

.controller( 'actionsheetCtl',['$scope','$ionicLoading','$timeout',function($scope,$ionicLoading,$timeout){

    $scope.show = function() {
        $ionicLoading.show({
          template: 'Loading...'
        });
      };

    $timeout(function(){
       $ionicLoading.hide();
    },2000)
      
}])

```


![ionicLoading](http://7vijqz.com1.z0.glb.clouddn.com/ionicLoading.gif)


### $ionicModal

> 它是一个可以遮住用户主界面的内容框。

> 你可以在你的 index 文件 或者是 其他文件内嵌入一下代码(里面的代码都可以根据你自己的业务场景相应的改变)：

```javascript
<script id="my-modal.html" type="text/ng-template">
  <ion-modal-view>
    <ion-header-bar>
      <h1 class="title">My Modal title</h1>
    </ion-header-bar>
    <ion-content>
      Hello!
    </ion-content>
  </ion-modal-view>
</script>
```

> 然后你就可以在你的 Controller 里面的注入 $ionicModal 。然后调用你刚刚写入的模板，进行初始化操作。就像下面的代码：

```javascript
angular.module('testApp', ['ionic'])
.controller('MyController', function($scope, $ionicModal) {
  $ionicModal.fromTemplateUrl('my-modal.html', {
    scope: $scope,
    animation: 'slide-in-up'
  }).then(function(modal) {
    $scope.modal = modal;
  });
  $scope.openModal = function() {
    $scope.modal.show();
  };
  $scope.closeModal = function() {
    $scope.modal.hide();
  };
  //Cleanup the modal when we're done with it!
  $scope.$on('$destroy', function() {
    $scope.modal.remove();
  });
  // Execute action on hide modal
  $scope.$on('modal.hidden', function() {
    // Execute action
  });
  // Execute action on remove modal
  $scope.$on('modal.removed', function() {
    // Execute action
  });
});
```

### $ionicPopover

> ionicPopover 是一个可以浮在app内容上的一个视图框。它经常被用来聚集或是展现一些信息给用户。

> 你可以在 index的文件或是其他文件里写入你想展现的模板。

```javascript
<script id="my-popover.html" type="text/ng-template">
          <ion-popover-view>
            <ion-header-bar>
              <h1 class="title">My Popover Title</h1>
            </ion-header-bar>
            <ion-content>
              Hello!
            </ion-content>
          </ion-popover-view>
        </script>  
```

> 然后在相应的Controller里面注入$ionicPopover，以及初始化。

```javascript
.controller( 'actionsheetCtl',['$scope','$ionicPopover','$timeout',function($scope,$ionicPopover,$timeout){

    $scope.popover = $ionicPopover.fromTemplateUrl('my-popover.html', {
      scope: $scope
    });

    // .fromTemplateUrl() method
    $ionicPopover.fromTemplateUrl('my-popover.html', {
      scope: $scope
    }).then(function(popover) {
      $scope.popover = popover;
    });


    $scope.openPopover = function($event) {
      $scope.popover.show($event);
    };
    $scope.closePopover = function() {
      $scope.popover.hide();
    };
    //Cleanup the popover when we're done with it!
    $scope.$on('$destroy', function() {
      $scope.popover.remove();
    });
    // Execute action on hide popover
    $scope.$on('popover.hidden', function() {
      // Execute action
    });
    // Execute action on remove popover
    $scope.$on('popover.removed', function() {
      // Execute action
    });
      
}])

```

> 然后你就可以在页面上调用相应的方法，来触发它。

```javascript
 <p>
  <button ng-click="openPopover($event)">Open Popover</button>
</p>
```

![$ionicPopover](http://7vijqz.com1.z0.glb.clouddn.com/ionicPopover.gif)



### $ionicPopup

> $ionicPopup 提供了3个方法：alert(), prompt(),以及 confirm() 。用法也非常简单！

**HTML:**

```javascript
 <button class="button button-dark" ng-click="showPopup()">
      show
    </button>
    <button class="button button-primary" ng-click="showConfirm()">
      Confirm
    </button>
    <button class="button button-positive" ng-click="showAlert()">
      Alert
    </button>
    
    <script id="popup-template.html" type="text/ng-template">
      <input ng-model="data.wifi" type="text" placeholder="Password">
    </script>
```

**JavaScript:**

```javascript
.controller('PopupCtrl',function($scope, $ionicPopup, $timeout) {

 // Triggered on a button click, or some other target
 $scope.showPopup = function() {
   $scope.data = {}

   // An elaborate, custom popup
   var myPopup = $ionicPopup.show({
     template: '<input type="password" ng-model="data.wifi">',
     title: 'Enter Wi-Fi Password',
     subTitle: 'Please use normal things',
     scope: $scope,
     buttons: [
       { text: 'Cancel' },
       {
         text: '<b>Save</b>',
         type: 'button-positive',
         onTap: function(e) {
           if (!$scope.data.wifi) {
             //don't allow the user to close unless he enters wifi password
             e.preventDefault();
           } else {
             return $scope.data.wifi;
           }
         }
       },
     ]
   });
   myPopup.then(function(res) {
     console.log('Tapped!', res);
   });
   $timeout(function() {
      myPopup.close(); //close the popup after 3 seconds for some reason
   }, 3000);
  };
   // A confirm dialog
   $scope.showConfirm = function() {
     var confirmPopup = $ionicPopup.confirm({
       title: 'Consume Ice Cream',
       template: 'Are you sure you want to eat this ice cream?'
     });
     confirmPopup.then(function(res) {
       if(res) {
         console.log('You are sure');
       } else {
         console.log('You are not sure');
       }
     });
   };

   // An alert dialog
   $scope.showAlert = function() {
     var alertPopup = $ionicPopup.alert({
       title: 'Don\'t eat that!',
       template: 'It might taste good'
     });
     alertPopup.then(function(res) {
       console.log('Thank you for not eating my delicious ice cream cone');
     });
   };
});
```

![ionicPopup](http://7vijqz.com1.z0.glb.clouddn.com/popup.gif)


