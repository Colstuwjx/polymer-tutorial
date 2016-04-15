#### 1.1 万物皆元素

Polymer，英文直译为"聚合物"，是Google在2013年的Google I/O大会上发布的一款面向未来的Web Component Library。它主张以开发可重用、高度抽象的[Web组件](https://en.wikipedia.org/wiki/Web_Components)的方式来构建Web应用。

Web组件实际上是W3C定义的一个未来标准，目前还处于草案阶段，但各大浏览器已经开始支持。它给了前端开发者扩展浏览器标签的能力，可以自由的定制组件，更好的进行模块化开发，彻底解放了前端开发者的生产力。关于Web组件这块，有兴趣的朋友还可以转到以下链接来了解更多的细节：https://css-tricks.com/modular-future-web-components/

时下许多的现代Web框架，如Angularjs，采用的是融合双向数据绑定 + 依赖注入的前端MVC模式来构建用户界面，ReactJS更是实现了一套自己的所谓的VirtualDOM，与这些框架不同的是，Polymer将视角放在了最本源的[DOM](https://en.wikipedia.org/wiki/Document_Object_Model)上，它认为: `DOM is the Framework`，并且通过提供polyfill类库（现已更名为`webcomponents.js`）来支持面向未来的[Web组件标准](http://webcomponents.org/)，使得Web开发者们可以基于此实现一套全新的前端开发模式。

在Polymer的世界里，`everything is an element.`
在这里面，Polymer扮演的角色正是一个library，它为开发者们带来了以下几个激动人心的特性（而这些统统都是着眼于DOM本身）：

* HTML imports：在其他HTML document中引入和重用HTML document的方法；
* Custom Element：让开发者可以自定义和重用DOM Element；
* Shadow DOM：在DOM中提供的封装，最主要的特性在于CSS样式的隔离；
* HTML Templates：类似Angularjs的template模式，实现数据的双向绑定.

关于上述这些特性，将会在后面章节里详细介绍。现在，你只需要记住一点，在Polymer的世界里，任何事物均可以抽象成`Element`，需要开发SPA应用? 没问题，使用[路由Element](https://elements.polymer-project.org/elements/carbon-route)好了! 需要调用Ajax和后台交互? 没问题，使用[Iron-ajax](https://elements.polymer-project.org/elements/iron-ajax)吧！一切的一切，都被抽象成了`Element`，而你需要做的，只是类似于乐高积木那样，构建所需的"积木块"，并把它们组合起来！
