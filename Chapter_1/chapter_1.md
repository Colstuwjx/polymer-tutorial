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
https://github.com/Polymer/polymer/wiki/Who's-using-Polymer%3F ，当然，国内也已经有像[Fireball](https://www.youtube.com/watch?v=8U9Ojc8Babc)这样的基于Polymer实现的优秀产品，它的源码已经开源到[Github](https://github.com/cocos-creator/deprecated-editor-ui)，读者朋友不妨去体验一下实际的效果。

#### 1.3 Polymer Starter Kit

Polymer官方在[Polymer 1.0](https://developers.googleblog.com/2015/05/polymer-10-released.html)发布时还配套提供了一款入门工具[Polymer Starter Kit](https://developers.google.com/web/tools/polymer-starter-kit/?hl=en)。这款工具非常贴心地为用户打包了所有最新的elements(包括非常炫酷的[service worker](https://github.com/PolymerElements/platinum-sw)等)，并且提供了完整的route方案（目前是使用[Page.js](https://github.com/visionmedia/page.js)，以后可能会有所变动）、端对端的工具链以及推荐的应用代码结构等等。

对于Polymer starter kit，目前也有两种安装方式，第一种自然是传统的下载zip方式：
```
# 可能墙，mac下面可以尝试一下proxychains配合ss来下载
wget -O <your_app_dir_&_detail_zip_name> https://github.com/PolymerElements/polymer-starter-kit/releases/download/v1.3.0/polymer-starter-kit-light-1.3.0.zip

# unzip to app dir
unzip <zip_name>
```
当然，用户也可以第二种更加优雅的方式，使用[Yoeman](http://yeoman.io/)（更详细的polymer yo scaffold请参见这个[Github 链接](https://github.com/yeoman/generator-polymer)的介绍）来完成下载和安装：
```
# 如果你还未安装yo的话，可以通过如下命令先行安装这款工具
npm install -g yo

# install the generator
npm install -g generator-polymer

# yo the polymer scaffold
cd <your_app_dir>
yo polymer

# then follow its steps..
```

完成下载后可以通过以下命令来实际在本地（笔者在mac Yosemite下测试ok）运行该款工具（当然，实在不能下载的话，笔者这边也提供一个下载好的zip，放到了[Github 这里](https://github.com/Colstuwjx/polymer-tutorial/blob/master/Chapter_1/code/polymer-starter-kit-light-1.3.0.zip)）：
```
# 使用yo构建方式的话，可以使用gulp来serve，这样的好处是代码的更改可以立即生效，端口5000
gulp serve

# 或者使用python SimpleHTTPServer module
python -m SimpleHTTPServer 5000
```
在Chrome浏览器上输入`127.0.0.1:5000`后看到的即Polymer starter kit的UI，的确它非常简单，也正因为如此，这个工具的完整代码能够给初学者很好的引导作用，而且也如页面中显示的内容那样，Polymer starter kit为用户提供了非常完整的生产环境标准的应用示例。关于Polymer starter kit，后面章节还将详细介绍，并且一些Polymer的特性和代码demo也将基于此工具实现，在此之前，强烈建议读者朋友先行部署安装对应环境。

备注：关于初学者工具，其实在Polymer 0.5版本时代还有一个很优秀的产品[Polymer designer](https://polymer-designer.appspot.com/)，这其实可以给前端开发者们以“UI工程师借此实现原型 => 前端工程师实际实现业务逻辑”这样的创新工作流，可惜，Polymer 1.0（更准确来说是v0.8+）开始，Custom Element的定义格式完全变样（这一点也非常值得吐槽...），并且创建了[Elements Catalog](https://elements.polymer-project.org/)，因此，Polymer designer tool还[未能加入对新版本的支持](https://github.com/Polymer/designer#status)，官方repo上也有对应[issue](https://github.com/Polymer/designer/issues/153)，期待这款工具的更新。

#### 1.4 关于兼容性

Polymer支持的是面向未来的Web Components，眼下主流的浏览器对于Polymer的支持仍不尽人意（即使有webcomponents.js，依旧会有很多不兼容的地方存在），关于兼容性支持，用户可以转到这个[官方链接](https://www.polymer-project.org/1.0/resources/compatibility.html)来了解详情。

在一段时间内，Polymer在兼容性方面的问题可能很难根除，这主要是Web Component标准仍未正式确立，另外，各大浏览器对Web Component技术的支持也相当暧昧不清。然而，这并非Polymer本身的问题。Polymer面向的是未来，借用知乎网友的一句话，“最好的办法就是'活在当下面向未来'。”

至此，本章便告一段落，相信通过这一章，读者朋友应该对“Polymer是什么”，“有什么主打特性”有一定的了解。下一章，我们将借助Polymer starter kit，介绍如何开发`Custom Element`。
