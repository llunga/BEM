### 关键观念 Key concepts 

+ block
+ element
+ modifier
+ BEM entity
+ mix
+ BEM tree
+ Block implementation （block的实现）
+ block implementation technology （block的实现技巧）
+ block redefinition （block的重定义）
+ redefinition level （重定义的级别）

##### 块

一个有逻辑性且具有功能性的独立页面组件等价于web组件里的组件。块封装了行为（JavaScript），模块，

样式，和其他的实现技巧。block的独立能够让其复用，以及促进项目开发。

###### 块 的特性

嵌套结构

+ block可以被嵌套多次

  🌰 一个head 块 可以由商标，搜索，授权三大块构成。

  ![截屏2020-08-30 上午11.01.16](/Users/llunga/Library/Application Support/typora-user-images/截屏2020-08-30 上午11.01.16.png)

+ 任意位置

  块可以在页面上移动，也可以在页面或项目之间移动。 将块实现为独立实体可以更改其在页面上的位置，并确保其正常运行和外观。

  因此，商标和授权表单可以互换，而无需修改块的CSS或JavaScript代码。

+ 重复使用

  一个接口可以包含同一块的多个实例。

  ![截屏2020-08-30 上午11.04.37](/Users/llunga/Library/Application Support/typora-user-images/截屏2020-08-30 上午11.04.37.png)

  ###### element

  element是block的组成部分，不能被用在外部。

  🌰 menu item 不能用在menu block的外面

  ![截屏2020-08-30 上午11.05.56](/Users/llunga/Library/Application Support/typora-user-images/截屏2020-08-30 上午11.05.56.png)

###### 修饰符 

BEM实例定义了块或元素的外观和行为。

使用修饰符是可选择的

修饰符可以看成是HTML的属性，一样的block看起来不一样是因为用了不一样的修饰符。

###### BEM 实例

块 block，元素 element，修饰符 modifier 都可以看成是 BEM的实例

值得注意的是，这个概念既可以用来指代单个BEM实体，又可以用作块，元素和修饰符的通用术语。

###### 混合

单个DOM节点上的不同BEM实体的实例

+ mix 允许我们
  + 结合多个BEM实例的行为和样式，同时避免代码重复。
  + 在现有BEM实体的基础上创建语义上新的接口组件。

###### BEM 树

用块，元素和修饰符表示的网页结构。 它是DOM树的抽象，描述了BEM实体的名称，它们的状态，顺序，嵌套和辅助数据。

在真实存在的项目里，一个BEM tree可以以任何支持树结构的格式表示。



🌰

```js
<header class="header">
    <img class="logo">
    <form class="search-form">
        <input class="input">
        <button class="button"></button>
    </form>
    <ul class="lang-switcher">
        <li class="lang-switcher__item">
            <a class="lang-switcher__link" href="url">en</a>
        </li>
        <li class="lang-switcher__item">
            <a class="lang-switcher__link" href="url">ru</a>
        </li>
    </ul>
</header>
```

与之对应的tree看起来是这样的：

```
header
    logo
    search-form
        input
        button
    lang-switcher
        lang-switcher__item
            lang-switcher__link
        lang-switcher__item
            lang-switcher__link
```

###### 块的实现 

bem实例可以由下面一组不同技巧实现

+ 行为
+ 外观
+ 测试
+ 模块
+ 文档
+ 依赖描述
+ 附加数据（比如 图片）

###### 实现的技巧

block可以被一个or多个技巧实现

🌰

行为 —— JavaScript，Coffeescript

外观 —— css , stylus, sass

模块 —— BEMHTML, BH, Pug, Handlebars, XSL

文档 —— Markdown, Wiki, XML.

###### 块的重定义

通过在不同级别向块添加新功能来修改块实现。

###### 重定义的级别

p.s.直接看图吧....

![截屏2020-08-30 上午11.22.07](/Users/llunga/Library/Application Support/typora-user-images/截屏2020-08-30 上午11.22.07.png)