## BEM

#### 快速开始

+ 介绍

  BEM (Block 块, Element 元素, Modifier 修饰符)是一种基于组件的网络开发方法。这个理论的背后是拆分用户的接口从而变成独立的快(Block). 这使得接口发展变得更加简单和快速即便是在复杂的UI下，并且这也允许重复使用已存在的代码免于复制粘贴。

  

+ 内容

  1.block 块 

  2.element 元素

  3.should i create a block or an element? 我应该创建一个块 还是 一个元素？

  4.modifier 修饰符

  5.mix 混合

  6.file structure 文件结构

  

+ Block 块

  一个具有功能性&独立的页面组件是可以被重复使用的。在HTML里，block是被带有class属性所代表的。

  + 特性：

    1. block的名字以目的性进行描述（这是什么？ 是菜单还是按钮）， 而不是以他的状态（他看起来是怎么样的？ 红还是大）

       举个例子：

       ```js
       <!--正确. `错误 error`是有意义的-->
       <div class="error"><div>
         
       <!--错误. `红色文本 red-text`描述了外观-->
       <div class="red-text"><div>
         
       ```

       

       2.块不应影响其环境，意味着不应设置块的外部几何形状（边距）或位置

       3.不应该使用css标记或ID选择器

       *这保证了在重用块或者从一个地方转移到另一个地方的独立性*

​             使用快的准则：

​                      1.嵌套

​                      	 1-1：block 可以相互浅嵌套

​                           1-2：可以有多个层级

​                      举个例子

```javascript
<!--header 块-->
<header class="header">
   <!--logo 块-->
   <div class="logo"></div>
   <search-form 块>
   <form class="search-form"></form>
</header>
```

​    





+ Element 元素

  块的复合部分不能分离的使用。

  - 特性

    1.元素的名字以目的性进行描述（这是什么？ 是一个项，文字等等）并不是它的状态（它看起来如何？ 红，大，等等）

    2.元素的完整名字应该是 块名字__元素名 （block-name____element-name）中间`__` 是两个下划线

    ```javascript
    <!--`search-from`块-->
    <form class="search-form">
      <!--`input` 元素在 `search-from`块中-->
      <input class="search-form__input">
      </input>
      <!--`button` 元素在 `search-from`块中-->
      <button class="search-from__button">search</button>
    </form>
    ```

    

  - 准则
    1. 嵌套
    2. membership？
    3. 可选性

  

  - 嵌套

    元素可以任意嵌套

    嵌套可以有多个层级

    一个元素总是在一个块当中，并非在另一个元素之中， 这就意味着不能这样命名（block __ elem1__elem2 这样是错的）

    举个🌰

    ```js
    <!--正确 整个结构的完整名字遵循以下的规则 `block-name__element-name`-->
    <form class="search-form">
      <div class="search-form__content">
        <input class="search-form__input"></input>
        <button class="search-form__button">search</button>
      </div>	
    </form>
    
    <!--错误-->
    <form class="search-form">
      <div class="search-form__content">
        <input class="search-form__content__input"></input>
        <button class="search-form__content__button">search</button>
      </div>	
    </form>    
    ```

    一个block可以被元素如此嵌套

    举个🌰

    ```javascript
    <div class="block">
      <div class="block__elem1">
        <div class="block__elem2">
          <div class="block__elem3">
          </div>
        </div>
      </div>
    </div>
    ```

    然鹅，在bem的方法论中，块的结构总是被表示成一组元素显示

    再举个🌰

    ```
    .blcok {}
    .block__elem1 {}
    .block__elem2 {}
    .block__elem3 {}
    ```

  



+ membership

  元素始终是块的一部分，并且不应与块分开使用。

  🌰

  ```javascript
  <!--正确 元素在block里-->
  <form class="search-form">
    <input class="search-form__input"></input>
    <button class="search-form__button">
  </form>
  
  <!--错误 元素不在block里-->
  <form class="search-form">
  </form>
  <!-- `input` element in the `search-form` block -->
  <input class="search-form__input">
  <!-- `button` element in the `search-form` block-->
  <button class="search-form__button">Search</button>
  ```

  

+ optionality 可选择性

  元素可以存在在block中，当然也可以没有。

  🌰

  ```javascript
  <!-- `search-form` block -->
  <div class="search-form">
      <!-- `input` block -->
      <input class="input">
  
      <!-- `button` block -->
      <button class="button">Search</button>
  </div>
  ```

  



+ 我要创建一个块还是一个元素咧？？？

  + 创建block

    + 如果一段代码可以重用，并且不依赖于正在实现的其他页面组件，那就创建block。

  + 创建元素

    + 如果一段代码不可以重用，并且不依赖于正在实现的其他页面组件，那就创建block。

    + 有一个例外，为了简化开发，必须将元素分成较小的部分（子元素）

      

+ 修饰符
  + .....