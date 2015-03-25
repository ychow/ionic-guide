## Ionic-JavaScript API

> Ionic 除了提供 CSS 框架，还提供了一个 JavaScrpt UI 库。许多组件都是需要通过javascript来产生比较炫的效果。ionic和Cocoa Touch 这个框架有点类似，都是采用了MVC的设计模式。下面就是关于ionic的中文javascript API介绍。



### $ionicActionSheet

> Action Sheet 通过网上弹出的框，来让用户选择选项。非常危险的选项会以高亮的红色来让人第一时间识别。你可以通过点击取消按钮或者点击空白的地方来让它消失。

**HTML**:
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

        <ion-pane>
            <ion-content >
                <h2 ng-click="show()">Action Sheet</h2>
            </ion-content>
        </ion-pane>
    </body>
</html>

```

**JavaScript**:

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

.controller( 'actionsheetCtl',['$scope','$ionicActionSheet','$timeout' ,function($scope,$ionicActionSheet,$timeout){
    $scope.show = function() {

        var hideSheet = $ionicActionSheet.show({
            buttons: [
              { text: '<b>Share</b> This' },
              { text: 'Move' }
            ],
            destructiveText: 'Delete',
            titleText: 'Modify your album',
            cancelText: 'Cancel',
            cancel: function() {
                 // add cancel code..
               },
            buttonClicked: function(index) {
              return true;
            }
        });

        $timeout(function() {
            hideSheet();
        }, 2000);

    };  
}])

```

![action-sheet](http://7vijqz.com1.z0.glb.clouddn.com/action-sheet.gif.gif)




### $ionicBackdrop

> 在UI上显示或隐藏背景层，在弹出框、加载框、其他弹出层中使用。许多UI界面需要背景层，在一个DOM页面只需要一个背景层就够了。在组件中可以使用$ionicBackdrop.retain()来显示背景层，使用$ionicBackdrop.release()隐藏背景层。每次调用retain后，背景会一直显示，直到调用release消除背景层。


**HTML**:

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

        <ion-pane>
            <ion-content >
                <h2 ng-click="action()">$ionicBackdrop</h2>
            </ion-content>
        </ion-pane>
    </body>
</html>

```

**JavaScript**:

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

.controller( 'actionsheetCtl',['$scope','$timeout' ,'$ionicBackdrop',function($scope,$timeout,$ionicBackdrop){

    $scope.action = function() {
       $ionicBackdrop.retain();
       $timeout(function() {    //默认让它1秒后消失
         $ionicBackdrop.release();
       }, 1000);
    }; 
}])

```

![ionic-backdrop](http://7vijqz.com1.z0.glb.clouddn.com/backdrop.gif)




### ion-refresher 

> 这个是类似于下拉刷新的效果。

**HTML**:

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

        <ion-pane>
            <ion-content >
                <ion-refresher pulling-text="下拉刷新" on-refresh="doRefresh()"></ion-refresher>
                <ion-list>
                    <ion-item ng-repeat="item in items" ng-bind="item.name"></ion-item>
                </ion-list>
            </ion-content>
        </ion-pane>
    </body>
</html>

```

**JavaScript**:

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

.controller( 'actionsheetCtl',['$scope','$timeout' ,'$http',function($scope,$timeout,$http){

    $scope.items=[
        {
            "name":"HTML5"
        },
        {
            "name":"JavaScript"
        },
        {
            "name":"Css3"
        }
    ];

    $scope.doRefresh = function() {
        $http.get('js/item.json')
            .success(function(newItems) {
                $scope.items = newItems;
            })
            .finally(function() {
                $scope.$broadcast('scroll.refreshComplete');
            });
    };
}])

```

**Json**:

```javascript
[
	{
		"name":"Ychow"
	},
	{
		"name":"Xiao"
	}
]
```

![ion-refresher](http://7vijqz.com1.z0.glb.clouddn.com/ion-fresher.gif)




### ion-checkbox


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

    $scope.devList = [
        { text: "HTML5", checked: true },
        { text: "CSS3", checked: false },
        { text: "JavaScript", checked: false }
      ];

      $scope.pushNotificationChange = function() {
        console.log('Push Notification Change', $scope.pushNotification.checked);
      };
      
      $scope.pushNotification = { checked: true };
      $scope.emailNotification = 'Subscribed';
      
}])

```

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
              <h1 class="title">Checkboxes</h1>
            </ion-header-bar>
                     
            <ion-content>
              
              <div class="list">
                
                <ion-checkbox ng-repeat="item in devList"
                              ng-model="item.checked" 
                              ng-checked="item.checked">
                  {{ item.text }}
                </ion-checkbox>
                
                <div class="item">
                  <pre ng-bind="devList | json"></pre> 
                </div>
                
                <div class="item item-divider"> 
                  Notifications
                </div>
                
                <ion-checkbox ng-model="pushNotification.checked"
                              ng-change="pushNotificationChange()">
                  Push Notifications
                </ion-checkbox>
                
                <div class="item">
                  <pre ng-bind="pushNotification | json"></pre> 
                </div>
                
                <ion-checkbox ng-model="emailNotification"
                              ng-true-value="'Subscribed'"
                              ng-false-value="'Unubscribed'">
                  Newsletter
                </ion-checkbox>
                <div class="item">
                  <pre ng-bind="emailNotification | json"></pre> 
                </div>
                
              </div>
              
            </ion-content>
            
    </body>
</html>

```


### ion-radio

> Ionic 的 ion-radio 指令只有样式上和普通的有所区别。


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
            <h1 class="title">Radio Buttons</h1>
          </ion-header-bar>
                   
          <ion-content>
            
            <div class="list">
              
              <div class="item item-divider"> 
                Clientside, Selected Value: {{ data.clientSide }}
              </div>
              
              <ion-radio ng-repeat="item in clientSideList"
                         ng-value="item.value"
                         ng-model="data.clientSide">
                {{ item.text }}
              </ion-radio>
              
              <div class="item item-divider">
                Serverside, Selected Value: {{ data.serverSide }}
              </div>
              
              <ion-radio ng-repeat="item in serverSideList"
                         ng-value="item.value"
                         ng-model="data.serverSide"
                         ng-change="serverSideChange(item)"
                         name="server-side">
                {{ item.text }}
              </ion-radio>
              
            </div>
            
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

    $scope.clientSideList = [
        { text: "Backbone", value: "bb" },
        { text: "Angular", value: "ng" },
        { text: "Ember", value: "em" },
        { text: "Knockout", value: "ko" }
      ];

      $scope.serverSideList = [
        { text: "Go", value: "go" },
        { text: "Python", value: "py" },
        { text: "Ruby", value: "rb" },
        { text: "Java", value: "jv" }
      ];
      
      $scope.data = {
        clientSide: 'ng'
      };
      
      $scope.serverSideChange = function(item) {
        console.log("Selected Serverside, text:", item.text, "value:", item.value);
      };
      
}])

```



### ion-toggle

> Ionic 的 toggle 和 Ios 系统下的非常像，都是 switch 的动画。


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
              <h1 class="title">Toggles</h1>
            </ion-header-bar>
                     
            <ion-content>
              
              <div class="list">
                
                <div class="item item-divider"> 
                  Settings
                </div>
                
                <ion-toggle ng-repeat="item in settingsList"
                            ng-model="item.checked" 
                            ng-checked="item.checked">
                  {{ item.text }}
                </ion-toggle>
                
                <div class="item">
                  <pre ng-bind="settingsList | json"></pre> 
                </div>
                
                <div class="item item-divider"> 
                  Notifications
                </div>
                
                <ion-toggle ng-model="pushNotification.checked"
                            ng-change="pushNotificationChange()">
                  Push Notifications
                </ion-toggle>
                
                <div class="item">
                  <pre ng-bind="pushNotification | json"></pre> 
                </div>
                
                <ion-toggle toggle-class="toggle-assertive"
                            ng-model="emailNotification"
                            ng-true-value="Subscribed"
                            ng-false-value="Unubscribed">
                  Newsletter
                </ion-toggle>
                
                <div class="item">
                  <pre ng-bind="emailNotification | json"></pre> 
                </div>
                
              </div>
              
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

    $scope.settingsList = [
        { text: "Wireless", checked: true },
        { text: "GPS", checked: false },
        { text: "Bluetooth", checked: false }
      ];

      $scope.pushNotificationChange = function() {
        console.log('Push Notification Change', $scope.pushNotification.checked);
      };
      
      $scope.pushNotification = { checked: true };
      $scope.emailNotification = 'Subscribed';
      
}])

```



### On-hold (长按)

> 长按的时间是500毫秒。

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
        <button on-hold="onHold()" class="button">长按我！</button>
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

    $scope.onHold=function(){
        alert('on-hold')
    }
    
      
}])

```


### On-tap(手点击)

> 这个是手势轻击事件，如果长按时间超过250毫秒，那就不是轻击了。

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
        <button on-tap="onTap()" class="button">轻击我</button>
    </body>
</html>

```

**JavaScript：**

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

    $scope.onTap=function(){
        alert('on-tap')
    }
    
      
}])

```



### on-double-tap (手双击屏幕事件)


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
        <button on-double-tap="onDoubleTap()" class="button">双击</button>
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

    $scope.onDoubleTap=function(){
        alert("你触发了双击事件")
    }
    
      
}])

```


### on-touch

> 这个和 on-tap 还是有区别的，这个是立即执行，而且是用户点击立马执行。不用等待 touchend/mouseup 。

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
        <button on-touch="onTouch()" class="button">on-touch</button>
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

    $scope.onTouch=function(){
        alert("你触发了on-touch")
    }
    
      
}])

```



### on-release 

> 当用户结束触摸事件时触发。


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
        <button on-release="onRelease()" class="button">onRelease</button>
    </body>
</html>

```


**JavaScript**

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

    $scope.onRelease=function(){
        alert("你触发了onRelease")
    }
    
      
}])

```


### on-drag

> 这个有点类似于PC端的拖拽。当你一直点击某个物体，并且手开始移动，都会触发 on-drag。


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
        <button on-drag="onDrag()" class="button">onDrag</button>
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

    $scope.onDrag=function(){
        console.log("onDrag")
    }
    
      
}])

```


### on-drag-up
### on-drag-right
### on-drag-down
### on-drag-left

> 这几个都和 on-drag 类似，只是根据手势移动的方向不同而触发各自的事件。你还可以在各自的方法里，添加当前手所点击的横纵坐标，来让方块和你的手势动起来！


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
        <button on-drag-up="onDragUp()" class="button">onDragUp</button>
        <button on-drag-down="onDragDown()" class="button">onDragDown</button>
        <button on-drag-right="onDragRight()" class="button">onDragRight</button>
        <button on-drag-left="onDragLeft()" class="button">onDragLeft</button>
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

    $scope.onDragUp=function(){
        console.log("onDragUp")
    }

    $scope.onDragDown=function(){
        console.log("onDragDown")
    }

    $scope.onDragRight=function(){
        console.log("onDragRight")
    }
    
    $scope.onDragLeft=function(){
        console.log("onDragLeft")
    }
      
}])

```



### on-swipe
### on-swipe-up
### on-swipe-down
### on-swipe-left
### on-swipe-right

> on-swipe 是指手指滑动效果，可以是任何方向上的。而且也和 on-drag 类似，都有四个方向上单独的事件。


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
        <button on-swipe="onSwipe()" class="button">onSwipe</button>
        <button on-swipe-up="onSwipeUp()" class="button">onSwipeUp</button>
        <button onSwipeDown="onSwipeDown()" class="button">onSwipeDown</button>
        <button onSwipeUp="onSwipeRight()" class="button">onSwipeRight</button>
        <button onSwipeUp="onSwipeLeft()" class="button">onSwipeLeft</button>
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

    $scope.onSwipe=function(){
        console.log("onSwipe")
    }

    $scope.onSwipeUp=function(){
        console.log("onSwipeUp")
    }

    $scope.onSwipeDown=function(){
        console.log("onSwipeDown")
    }

    $scope.onSwipeLeft=function(){
        console.log("onSwipeLeft")
    }

    $scope.onSwipeRight=function(){
        console.log("onSwipeRight")
    }
      
}])

```
