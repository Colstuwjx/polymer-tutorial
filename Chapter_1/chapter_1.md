### 第一章 Hello, Polymer
#### 1.1 万物皆元素

[Polymer](https://www.polymer-project.org/)，英文直译为"聚合物"，是Google在2013年的Google I/O大会上发布的一款面向未来的Web Component Library。它主张以开发可重用、高度抽象的[Web组件](https://en.wikipedia.org/wiki/Web_Components)的方式来构建Web应用。

Web组件实际上是W3C定义的一个未来标准，目前还处于草案阶段，但各大浏览器已经开始支持。它给了前端开发者扩展浏览器标签的能力，可以自由的定制组件，更好的进行模块化开发，彻底解放了前端开发者的生产力。关于Web组件这块，有兴趣的朋友还可以转到以下链接来了解更多的细节：https://css-tricks.com/modular-future-web-components/

时下许多的现代Web框架，如AngularJS，采用的是融合双向数据绑定 + 依赖注入的前端MVC模式来构建用户界面，ReactJS更是实现了一套自己的所谓的VirtualDOM，与这些框架不同的是，Polymer将视角放在了最本源的[DOM](https://en.wikipedia.org/wiki/Document_Object_Model)上，它认为: `DOM is the Framework`，并且通过提供polyfill类库（现已更名为`webcomponents.js`）来支持面向未来的[Web组件标准](http://webcomponents.org/)，使得Web开发者们可以基于此实现一套全新的前端开发模式。

在Polymer的世界里，`everything is an element.`
在这里面，Polymer扮演的角色正是一个library，它为开发者们带来了以下几个激动人心的特性（而这些统统都是着眼于DOM本身）：

* HTML imports：在其他HTML document中引入和重用HTML document的方法；
* Custom Element：让开发者可以自定义和重用DOM Element；
* Shadow DOM：在DOM中提供的封装，最主要的特性在于CSS样式的隔离；
* HTML Templates：类似AngularJS的template模式，实现数据的双向绑定.

关于上述这些特性，将会在后面章节里详细介绍。现在，你只需要记住一点，在Polymer的世界里，任何事物均可以抽象成`Element`，需要开发SPA应用? 没问题，使用[carbon-route](https://elements.polymer-project.org/elements/carbon-route)好了! 需要调用Ajax和后台交互? 没问题，使用[iron-ajax](https://elements.polymer-project.org/elements/iron-ajax)吧！一切的一切，都被抽象成了`Element`，而你需要做的，只是类似于乐高积木那样，构建所需的"积木块"，并把它们组合起来！

#### 1.2 应用场景

Polymer的定位是WebComponent和Custom Element之间的library，那么它适用于哪些应用场景呢？众所周知，构建一个app所需考虑的有以下几点：

* 布局（包括响应式）；
* UI样式；
* 性能；
* 业务逻辑的实现方式以及可维护性（包括分工、Module\Component管理、AMD\COMMON.js按需加载等）；

很显然，如果你的应用无法很好的切分成多块层层堆叠的"积木"的话，仅仅选用Polymer（之所以这样说，是因为在可以预见的未来，Polymer也许可以和其他主流框架做集成）也许不是一个好主意。因此，它更适用于相对松散的分工模式。

关于Polymer，如今业界已经有不少的成功产品案例，Polymer官方也维护了一个对应的列表:
https://github.com/Polymer/polymer/wiki/Who's-using-Polymer%3F ，当然，国内也已经有像[Fireball](https://www.youtube.com/watch?v=8U9Ojc8Babc)这样的基于Polymer实现的优秀产品，读者朋友不妨去体验一下实际的效果。
