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

  定义块或者元素的外观。

  + 特性

    修饰符的名字描述了他的外观（什么尺寸 or 什么主题等等等等 size_s or theme_islands ）,它的状态（与其他的是怎么的不一样咧？disabled, fouces 等等等等）它的行为（他是咋样的行为 or它是怎么应对用户的行为的， 比如 directions_left-top）

    修饰符的名字应该与块和元素的名字以 _ 区别开来

  + 修饰符的类型

    + 布尔类型

      使用的时候，修饰符存在或者不存在是很重要的，并且它的值是无相关的。 比如说， disabled。如果布尔修饰符存在的话，那么它的值是true。

      它的结构

      block-name _ modifier-name

      Block-name __ element-name _ modifier-name

      ```javascript
      <!-- The `search-form` block has the `focused` Boolean modifier -->
      <form class="search-form search-form_focused">
          <input class="search-form__input">
      
          <!-- The `button` element has the `disabled` Boolean modifier -->
          <button class="search-form__button search-form__button_disabled">Search</button>
      </form>
      ```

      

    + Key-value

      当修饰符的值很重要的时候使用它。 举例，一个菜单的主题是islands： menu_theme_islands

      它的结构

      Block-name_modifier-name_modifier-value

      Block-name__element-name_modifier-name_modifier-value

      🌰

      ```javascript
      <!-- The `search-form` block has the `theme` modifier with the value `islands` -->
      <form class="search-form search-form_theme_islands">
          <input class="search-form__input">
      
          <!-- The `button` element has the `size` modifier with the value `m` -->
          <button class="search-form__button search-form__button_size_m">Search</button>
      </form>
      
      <!-- You can't use two identical modifiers with different values simultaneously -->
      <form class="search-form
                   search-form_theme_islands
                   search-form_theme_lite">
      
          <input class="search-form__input">
      
          <button class="search-form__button
                         search-form__button_size_s
                         search-form__button_size_m">
              Search
          </button>
      </form>
      ```

      

  + 修饰符的使用准则

    修饰符不能被单独使用

    从bem的角度来说，一个修饰符不能与已修改的块or元素单独使用。修饰符是更改外观的，行为或者状态并不是来替换的作用的。

    🌰 

    p.s.在我看来，这个search-form一点要优于search-form__theme-islands存在，一个看成爹爹

    一个看成儿子

    ```js
    <!--
        Correct. The `search-form` block has the `theme` modifier with
        the value `islands`
    -->
    <form class="search-form search-form_theme_islands">
        <input class="search-form__input">
    
        <button class="search-form__button">Search</button>
    </form>
    
    <!-- Incorrect. The modified class `search-form` is missing -->
    <form class="search-form_theme_islands">
        <input class="search-form__input">
    
        <button class="search-form__button">Search</button>
    </form>
    ```

+ Mix 混合

  在单个DOM节点上使用不同的BEM实体的技巧

  mixes 允许让你：

  整合多个实体的行为和样式，无需重复代码。

  基于现有组件创建语义上新的UI组件。

  ```js
  <!-- `header` block -->
  <div class="header">
      <!--
          The `search-form` block is mixed with the `search-form` element
          from the `header` block
      -->
      <div class="search-form header__search-form"></div>
  </div>
  
  ```

  在这个🌰中，我们把search-form这个块 & header__search-form 的样式和行为整合到一起去了，

  这个方法允许让我们设置外部的形状和位置在 header__search-form中，而search-form它自己本身保持通用型。结论就是，我们可以用这个block在任何场景下，因为他木有特定的任何填充。这就是为什么我们可以将其称为独立。

+ file structure 文件结构

  bem 方法中采用的组件方法也适用于文件结构中的项目。 块，元素和修饰符的实现分为独立的技术文件，这意味着我们可以单独连接它们。

  + 特性

    + 一个块对应一个目录

    + 块和目录有一样的名字。🌰，header块应该在header/目录下，menu块应该在menu/目录下

    + 块的实现拆分为独立的文件。 例如header.css和header.js

    + 块目录是其元素和修饰符的子目录的根目录。

    + 元素目录的名称以双下划线（__）开头。 例如，标题/ __ logo /和菜单/ __ item /。

    + 修饰符目录的名称以单个下划线（_）开头。 例如，header / _fixed /和menu / _theme_islands /。

    + 元素和修饰符的实现分为单独的文件。 例如，header__input.js和header_theme_islands.css。

      ```
      search-form/                           # Directory of the search-form
      
          __input/                           # Subdirectory of the search-form__input
              search-form__input.css         # CSS implementation of the
                                             # search-form__input element
              search-form__input.js          # JavaScript implementation of the
                                             # search-form__input element
      
          __button/                          # Subdirectory of the search-form__button
                                             # element
              search-form__button.css
              search-form__button.js
      
          _theme/                            # Subdirectory of the search-form_theme
                                             # modifier
              search-form_theme_islands.css  # CSS implementation of the search-form block
                                             # that has the theme modifier with the value
                                             # islands
              search-form_theme_lite.css     # CSS implementation of the search-form block
                                             # that has the theme modifier with the value
                                             # lite
      
          search-form.css                    # CSS implementation of the search-form block
          search-form.js                     # JavaScript implementation of the
                                             # search-form block
      ```

      

    这个文件结构让代码重用变得更加简单。

  ......

