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


