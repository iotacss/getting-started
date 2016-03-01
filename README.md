# Getting Started with iotaCSS #

This is a detailed documentation with everything you need to know about iotaCSS and how to get started with it.


## What is iotaCSS ##

iotaCSS is a smart and minimalistic CSS Framework built for scale. It's SASS based and follows the BEM Methodology.


## Understanding iotaCSS ##

iotaCSS is a set of standalone modules and each one of them has it's own dependencies. Each module can be used as a unit or it can be used together with other modules in order to build more complex features. iotaCSS modules are separated into different categories, which help developers understand what each category is meant for and how it has to be threated by the developer. The main categories are:


### Settings ###

Setting files contain options that are shared by more than one modules. Options that are connected to one and only module are a part of the module it self.

### Tools ###

Tools are a set of general sass mixins and functions used by iotaCSS modules.


### Base ###

Base are modules related to the basic styles of an application, like Typography, Reset and styling of global elements. **This part is still under development.**


### Objects ###

Objects are elements that provide structure to your content, like Grid or Media Object. They do not contain any cosmetic CSS and they should never directly overitten. By default, an object is prefixed with "o-".


### Components ###

Components are UI elements. They contain cosmetic CSS and they can be directly overriten to fit your UI Kit style. iotaCSS provides a set of minimalistic components, having the only needed styling, all controlled by options, to achieve zero unnecessary CSS property override. By default, a component is prefixed with "c-".


### Utilities ###

Utilities are helper classes. They are usually one line of code, like .u-text-right or .u-float-right. iotaCSS provide all the utilities you will ever need. BY default, a utility is prefixed with "u-".


Now you understand the architecture behind iotaCSS, let's get started.


## Learn iotaCSS By Example


### Building Tabs

Assuming we need several inline tabs which they take over the 100% of their containers

We will need the modules:

* [Settings.Default](https://github.com/iotacss/settings.default)
* [Objects.List](https://github.com/iotacss/objects.grid)

```
npm install --save iotacss-list
```

*The reason I didn't install also the Settings.Default is because it's a dependency of Objects.List. All modules have their own dependencies installed with them. Please make sure you read their dependencies, so, you know what you have to import in your sass file. Import order of modules follow the order of the categories as mentioned above.*

Back to our example now. Our sass file will look like this:

```sass
$iota-list--span: true;  // Enable span list in order to have inline elements that take the 100% of their container

@import "node_modules/iotacss-default/settings.default";
@import "node_modules/iotacss-list/objects.list";

.c-tab-nav {}

  .c-tab-nav__list {}
  
    .c-tab-nav__item {}
```

Our HTML will look like:

```html
<nav class="c-tab-nav">
  <ul class="c-tab-nav__list  o-list  o-list--span">
    <li class="c-tab-nav__item  o-list__item">
      <a href="#">Tab 1</a>
    </li>
    <li class="c-tab-nav__item  o-list__item">
      <a href="#">Tab 2</a>
    </li>
    <li class="c-tab-nav__item  o-list__item">
      <a href="#">Tab 3</a>
    </li>
  </ul>
</nav>
```


### Building Comments List

We will need the modules:

* [Settings.Default](https://github.com/iotacss/settings.default)
* [Tools.Mixin](https://github.com/iotacss/objects.grid)
* [Objects.Media](https://github.com/iotacss/objects.grid)

```
npm install --save iotacss-media
```

Our sass will look like:

```sass
@import "node_modules/iotacss-default/settings.default";
@import "node_modules/iotacss-mixin/tools.mixin";
@import "node_modules/iotacss-list/objects.list";

.c-comments {}

  .c-comments__list {}
  
  .c-comment__form {}

  
.c-comment {}

  .c-comment__image {}
  
    .c-comment__avatar {}
    
  .c-comment__body {}
```

Our HTML will look like:

```html
<div class="c-comments">

  <div class="c-comments__list">
  
    <div class="c-comment  o-media">
      <div class="c-comment__image  o-media__image">
        <img src="..." class="c-comment__avatar" />
      </div>
      <div class="c-comment__body  o-media__body">
        <p>Hey! I am a comment</p>
      </div>
    </div>
    
    <div class="c-comment  o-media">
      <div class="c-comment__image  o-media__image">
        <img src="..." class="c-comment__avatar" />
      </div>
      <div class="c-comment__body  o-media__body">
        <p>Hey! I am a comment</p>
      </div>
    </div>
    
  </div>
  
  <form class="c-comment__form">
    
  </form>
  
</div>
```


### Building a Responsive Grid

Assuming we will need a 2, 3 and 4 column responsive grid. We will need the modules:

* [Settings.Default](https://github.com/iotacss/settings.default)
* [Settings.Column](https://github.com/iotacss/settings.column)
* [Settings.Breakpoint](https://github.com/iotacss/settings.breakpoint)
* [Objects.Grid](https://github.com/iotacss/objects.grid)
* [Utilities.Size](https://github.com/iotacss/utilities.size)

```
npm install --save iotacss-column iotacss-breakpoint iotacss-grid iotacss-size
```

Our sass file will look like this:

```sass
$iota-column-sizes: 2, 3, 4;  // That will create 2, 3 and 4 sizes
$iota-size--res: true;  // That will enable responsive size utilities based on our Breakpoint Settings


@import "node_modules/iotacss-default/settings.default";  // Required dependency of iotaCSS
@import "node_modules/iotacss-column/settings.column";
@import "node_modules/iotacss-breakpoint/settings.breakpoint";

@import "node_modules/iotacss-grid/objects.grid";
@import "node_modules/iotacss-size/utilities.size";
```

Our HTML will look like

```html
<div class="o-grid">
  <div class="o-grid__col  u-1/2  u-1/3@sm  u-1/4@md">
    A half column at mobile, one third in tablets and one forth in desktops
  </div>
  <div class="o-grid__col  u-1/2  u-1/3@sm  u-1/4@md">
    A half column at mobile, one third in tablets and one forth in desktops
  </div>
  <div class="o-grid__col  u-1/2  u-1/3@sm  u-1/4@md">
    A half column at mobile, one third in tablets and one forth in desktops
  </div>
  <div class="o-grid__col  u-1/2  u-1/3@sm  u-1/4@md">
    A half column at mobile, one third in tablets and one forth in desktops
  </div>
</div>
```


## License

iotaCSS is released under the MIT License.
