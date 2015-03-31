## Ionic-JavaScript API


### ion-tabs

> ion-tabs 是有一组页面选项卡组成的选项卡栏。可以通过点击选项来切换页面。对于 IOS，它会出现在屏幕的底部，Android会出现在屏幕的顶部(导航栏下面)。

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
    <body ng-app="starter" >
        <ion-nav-bar class="bar-positive">
              <ion-nav-back-button>
              </ion-nav-back-button>
            </ion-nav-bar>
                     
            <ion-nav-view></ion-nav-view>


            <script id="templates/tabs.html" type="text/ng-template">
              <ion-tabs class="tabs-icon-top tabs-positive">

                <ion-tab title="Home" icon="ion-home" href="#/tab/home">
                  <ion-nav-view name="home-tab"></ion-nav-view>
                </ion-tab>

                <ion-tab title="About" icon="ion-ios-information" href="#/tab/about">
                  <ion-nav-view name="about-tab"></ion-nav-view>
                </ion-tab>

                <ion-tab title="Contact" icon="ion-ios-world" ui-sref="tabs.contact">
                  <ion-nav-view name="contact-tab"></ion-nav-view>
                </ion-tab>

              </ion-tabs>
            </script>

            <script id="templates/home.html" type="text/ng-template">
              <ion-view view-title="Home">
                <ion-content class="padding">
                  <p>
                    <a class="button icon icon-right ion-chevron-right" href="#/tab/facts">Scientific Facts</a>
                  </p>
                </ion-content>
              </ion-view>
            </script>

            <script id="templates/facts.html" type="text/ng-template">
              <ion-view view-title="Facts">
                <ion-content class="padding">
                  <p>Banging your head against a wall uses 150 calories an hour.</p>
                  <p>Dogs have four toes on their hind feet, and five on their front feet.</p>
                  <p>The ant can lift 50 times its own weight, can pull 30 times its own weight and always falls over on its right side when intoxicated.</p>
                  <p>A cockroach will live nine days without it's head, before it starves to death.</p>
                  <p>Polar bears are left handed.</p>
                  <p>
                    <a class="button icon ion-home" href="#/tab/home"> Home</a>
                    <a class="button icon icon-right ion-chevron-right" href="#/tab/facts2">More Facts</a>
                  </p>
                </ion-content>
              </ion-view>
            </script>

            <script id="templates/facts2.html" type="text/ng-template">
              <ion-view view-title="Also Factual">
                <ion-content class="padding">
                  <p>111,111,111 x 111,111,111 = 12,345,678,987,654,321</p>
                  <p>1 in every 4 Americans has appeared on T.V.</p>
                  <p>11% of the world is left-handed.</p>
                  <p>1 in 8 Americans has worked at a McDonalds restaurant.</p>
                  <p>$283,200 is the absolute highest amount of money you can win on Jeopardy.</p>
                  <p>101 Dalmatians, Peter Pan, Lady and the Tramp, and Mulan are the only Disney cartoons where both parents are present and don't die throughout the movie.</p>
                  <p>
                    <a class="button icon ion-home" href="#/tab/home"> Home</a>
                    <a class="button icon ion-chevron-left" href="#/tab/facts"> Scientific Facts</a>
                  </p>
                </ion-content>
              </ion-view>
            </script>

            <script id="templates/about.html" type="text/ng-template">
              <ion-view view-title="About">
                <ion-content class="padding">
                  <h3>Create hybrid mobile apps with the web technologies you love.</h3>
                  <p>Free and open source, Ionic offers a library of mobile-optimized HTML, CSS and JS components for building highly interactive apps.</p>
                  <p>Built with Sass and optimized for AngularJS.</p>
                  <p>
                    <a class="button icon icon-right ion-chevron-right" href="#/tab/navstack">Tabs Nav Stack</a>
                  </p>
                </ion-content>
              </ion-view>
            </script>

            <script id="templates/nav-stack.html" type="text/ng-template">
              <ion-view view-title="Tab Nav Stack">
                <ion-content class="padding">
                  <p><img src="http://ionicframework.com/img/diagrams/tabs-nav-stack.png" style="width:100%"></p>
                </ion-content>
              </ion-view>
            </script>

            <script id="templates/contact.html" type="text/ng-template">
              <ion-view title="Contact">
                <ion-content>
                  <div class="list">
                    <div class="item">
                      @IonicFramework
                    </div>
                    <div class="item">
                      @DriftyTeam
                    </div>
                  </div>
                </ion-content>
              </ion-view>
            </script> 
    </body>
</html>
```

**JavaScript:**

```javascript

angular.module('starter', ['ionic'])

.config(function($stateProvider, $urlRouterProvider) {

  $stateProvider
    .state('tabs', {
      url: "/tab",
      abstract: true,
      templateUrl: "templates/tabs.html"
    })
    .state('tabs.home', {
      url: "/home",
      views: {
        'home-tab': {
          templateUrl: "templates/home.html",
          controller: 'HomeTabCtrl'
        }
      }
    })
    .state('tabs.facts', {
      url: "/facts",
      views: {
        'home-tab': {
          templateUrl: "templates/facts.html"
        }
      }
    })
    .state('tabs.facts2', {
      url: "/facts2",
      views: {
        'home-tab': {
          templateUrl: "templates/facts2.html"
        }
      }
    })
    .state('tabs.about', {
      url: "/about",
      views: {
        'about-tab': {
          templateUrl: "templates/about.html"
        }
      }
    })
    .state('tabs.navstack', {
      url: "/navstack",
      views: {
        'about-tab': {
          templateUrl: "templates/nav-stack.html"
        }
      }
    })
    .state('tabs.contact', {
      url: "/contact",
      views: {
        'contact-tab': {
          templateUrl: "templates/contact.html"
        }
      }
    });


   $urlRouterProvider.otherwise("/tab/home");

})

.controller('HomeTabCtrl', function($scope) {
  console.log('HomeTabCtrl');
});
```


### ion-spinner

> ionSpinner 提供了许多种旋转加载的动画图标。当你的界面加载时，你就可以呈现给用户相应的加载图标。该图标采用的是SVG。用法也非常简单。

```javascript
<ion-spinner icon="spiral"></ion-spinner>    //默认用法
```

> 下面是 Ionic 提供的一些，前面是它们各自的命名，你只需要在icon 里面写上各自的命名，就Ok啦。

![spinner](http://7vijqz.com1.z0.glb.clouddn.com/spinner.png)


> 像大部分其他的Ionic组件一样，Spinner也可以使用Ionic的标准颜色命名规则，就像下面这样：

```javascript
<ion-spinner class="spinner-energized"></ion-spinner>
```

![spiiner](http://7vijqz.com1.z0.glb.clouddn.com/spiner.gif)



### ion-slide-box

>它是一个多页面的容器，你可以滑动或者拖拽来切换他们。我们也可以用它来做一个幻灯片(我在公司的项目里面就是用它来改的幻灯片)！最简单的用法如下：

**HTML:**
```javascript
<ion-slide-box on-slide-changed="slideHasChanged($index)">
  <ion-slide>
    <div class="box blue"><h1>BLUE</h1></div>
  </ion-slide>
  <ion-slide>
    <div class="box yellow"><h1>YELLOW</h1></div>
  </ion-slide>
  <ion-slide>
    <div class="box pink"><h1>PINK</h1></div>
  </ion-slide>
</ion-slide-box>
```

![ion-slide-box](http://ionicframework.com.s3.amazonaws.com/docs/controllers/slideBox.gif)


### ion-side-menus 

**HTML:**

```javascript
<ion-side-menus>
  <!-- Center content -->
  <ion-side-menu-content ng-controller="ContentController">
  </ion-side-menu-content>

  <!-- Left menu -->
  <ion-side-menu side="left">
  </ion-side-menu>

  <!-- Right menu -->
  <ion-side-menu side="right">
  </ion-side-menu>
</ion-side-menus>
```

**Javascript:**

```javascript
function ContentController($scope, $ionicSideMenuDelegate) {
  $scope.toggleLeft = function() {
    $ionicSideMenuDelegate.toggleLeft();
  };
}
```

![ion-side-menus](http://ionicframework.com.s3.amazonaws.com/docs/controllers/sidemenu.gif)
