# coding-specification (代码规范)

> 黄金定律：永远遵循一套编码规范，不管多少人共同参与一个项目，一定要确保每一行代码都像同一个人编写的


**说明：**

- 本规范参照了
  - [`Google HTML/CSS Style Guide`](https://google.github.io/styleguide/htmlcssguide.html)
  - [`Google JavaScript Style Guide`](https://google.github.io/styleguide/jsguide.html)
  - [`Code Guide`](http://alloyteam.github.io/CodeGuide/)

## 基础规范

### `项目文件夹` & `html, css, js 文件`命名规范

- 必须全部小写，并且可以包含下划线（`_`）或短划线（`-`），但不包含其他标点符号。具体使用哪个依照项目约定
- 有复数结构时，要采用复数命名法 例：`scripts, styles, images`

### 编码

- 使用`UTF-8`（无BOM）
- 在HTML模板和文档中指定编码 `<meta charset="utf-8">`。不要指定样式表的编码，因为它们都采用UTF-8

### 缩进

- 一次缩进2个空格(可以调整编辑器格式)

```html
.example {
  color: blue;
}

<ul>
  <li>Fantastic
  <li>Great
</ul>
```

- 嵌套结构也使用两个空格以保持结构统一

### 大小写

- 只用小写字母
- 所有代码必须为小写：这适用于
- `HTML` 的
  - `元素名称(element names)`
  - `属性(attributes)`
  - `属性值(attribute values)`（除非 `text/CDATA`）
- `CSS` 的
  - `选择器(selectors)`
  - `属性(properties)`
  - `属性值(property values)`（字符串除外）

```html
<!-- 不推荐 -->
<A HREF="/">Home</A>

color: #E5E5E5;
```

```html
<!-- 推荐 -->
<img src="google.png" alt="Google">

color: #e5e5e5;
```

### 空格

以下几种情况不需要空格：

- 属性名后不需要空格
  - `color : #333;` 不推荐
  - `color: #333;` 推荐
- 多个规则的分隔符','前
- 属性值中的'`,`'后
  - `background-color: rgba(0,0,0,.5);` 不推荐
  - `background-color: rgba(0, 0, 0, .5);` 推荐
- `!important` '`!`'后
  - `color :red! important;` 不推荐
  - `color: red !important;` 推荐
- 属性值中'`(`'后和'`)`'前
  - `background-color: rgba( 0, 0, 0, .5 );` 不推荐
  - `background-color: rgba(0, 0, 0, .5);` 推荐
- 行末不要有多余的空格

以下几种情况需要空格：

- 属性值前
  - `color:#333;` 不推荐
  - `color: #333;` 推荐
- 选择器'>', '+', '~'前后
  - `.element>.dialog` 不推荐
  - `.element > .dialog` 推荐
- '`{`'前
  - `.element{}` 不推荐
  - `.element {}` 推荐
- `!important` '`!`'前 (非必要情况下不推荐使用 `!important`)
  - `color: red ! important;` 不推荐
  - `color: red !important;` 推荐

### 注释

- 注释'`/*`'后和'`*/`'前要空一个空格
- `//` 后要空一个空格
- 使用注释时尽量把要解释的内容解释清楚
- 使用注释来解释代码：
  - 它包含了什么
  - 它的用途是什么
  - 为什么使用或优先使用相应的解决方案？

### 待做任务(`TODO`)

- 用`TODO` 来突出显示待办事项，而非其他格式
- 用`TODO: 需要做的事` 在冒号后添加需要做的事
- 用 `TODO(姓名): 需要做的事` 在括号中指定某人需要做什么事

```html
{# TODO(john.doe): revisit centering #}
<center>Test</center>

<!-- TODO: remove optional tags -->
<ul>
  <li>Apples</li>
  <li>Oranges</li>
</ul>
```

### Protocol(协议)

- 尽可能使用 `HTTPS` 协议嵌入资源

```html
<!-- 推荐：省略协议，以备以后协议调整 -->
<script src="//ajax.googleapis.com/ajax/libs/jquery/3.1.0/jquery.min.js"></script>

<!-- 不推荐：使用HTTP协议 -->
<script src="http://ajax.googleapis.com/ajax/libs/jquery/3.1.0/jquery.min.js"></script>
```

```less
/* 推荐：省略协议 */
@import '//fonts.googleapis.com/css?family=Open+Sans';

/* 不推荐：使用HTTP协议 */
@import 'http://fonts.googleapis.com/css?family=Open+Sans';
```

---

## `HTML` 样式规则

### 文件类型(Document Type)

- 使用 `HTML5`
- 对于所有HTML文档，`HTML5`（HTML语法）是首选：`<!DOCTYPE html>`

### 语言属性

- 根据HTML5规范：
  - 强烈建议为html根元素指定lang属性，从而为文档设置正确的语言。这将有助于语言合成工具确定其应该采用的发音，有助于翻译工具去顶其翻译时应遵守的规则等。
- `<html lang="en-us">`
- 这里可以查看[语言表](https://www.sitepoint.com/iso-2-letter-language-codes/)

### 不要关闭`单标签`元素

- 即写 `<br>`，而不是 `<br />`
- 写 `<img src="logo.png" alt="logo">`，而不是`<img src="logo.png" alt="logo" />`

### IE兼容模式

- IE支持通过特定的`<meta>`标签来确定绘制当前页面所应采用的IE版本。除非有强烈的特殊需求，否则最好是设置为`edge mode`从而通知IE采用其所支持的最新模式
- `<meta http-equiv="X-UA-Compatible" content="IE=Edge">`
- 这里可以查看关于标签设置的[更多信息](https://stackoverflow.com/questions/6771258/what-does-meta-http-equiv-x-ua-compatible-content-ie-edge-do)

### 引入CSS和JavaScript文件

- 根据HTML5规范，在引入CSS和JavaScript文件时一般不需要指定`type`属性，因为`text/css`和`text/javascript`分别是它们的默认值
- `<link rel="stylesheet" href="xxx.css">`
- `<script src="xxx.js"></script>`

### 属性顺序

- HTML属性应当按照以下给出的顺序一次书写，确保易读性
- `class`
- `id，name`
- `data-*`
- `scr，for，type，href，value`
- `title，alt`
- `role，aria-*`
- class用于标识高度可复用组件，应该排在首位，id用于标识具体组件，应当谨慎使用

```htmlbars
<a class="..." id="..." data-toggle="modal" href="#">
  Example link
</a>

<input class="form-control" type="text">

<img src="..." alt="...">
```

### 布尔（boolean）型属性

- 布尔型属性可以在声明时不赋值，XHTML规范要求为其赋值，但是HTML5不需要
  - HTML5中：*元素的布尔属性如果有值，就是true，如果没有值，就是false*
- 如果一定要为其赋值的话，参考WhatWG规范
  - *如果属性存在其值必须是空字符串或者[...]属性的规范名称，并且不要在首尾添加空白符*
- **简单来说就是不用赋值**

```html
<input type="text" disabled>

<input type="checkbox" value="1" checked>

<select>
  <option value="1" selected>1</option>
</select>
```

### 语义化标签

- 根据标签作用合理使用标签
- 根据其目的使用HTML对于可访问性，重用性和代码效率的原因很重要

```html
<!-- 不推荐 -->
<div onclick="goToRecommendations();">All recommendations</div>
```

```html
<!-- 推荐 -->
<a href="recommendations/">All recommendations</a>
```

### 为多媒体提供替代内容 alt

- 对于多媒体，如 `images`，`videos`，`动画对象(animated objects)` 通过 `canvas`，确保提供替代访问。对于 `images`，意味着使用有意义的替代文本（alt）以及视频和音频转录本和标题（如果可用）
- 提供替代内容对于可访问性的原因很重要：如果没有 `alt` 盲人用户就不会知道有没有图像，而其他用户可能无法理解视频或音频内容

```html
<!-- 不推荐不带 alt -->
<img src="spreadsheet.png">
```

```html
<!-- 推荐 -->
<img src="spreadsheet.png" alt="Spreadsheet screenshot.">
```

### 严格保持结构规整

- 严格保持结构（`HTML`），样式（`CSS`）和行为（`script`）分开，并尽量保持三者之间的交互作用最小
- 此外，通过尽可能少地从文档和模板链接样式表和脚本，尽可能减少接触面积

```html
<!-- 不推荐 -->
<!DOCTYPE html>
<title>HTML sucks</title>
<link rel="stylesheet" href="base.css" media="screen">
<link rel="stylesheet" href="grid.css" media="screen">
<link rel="stylesheet" href="print.css" media="print">
<h1 style="font-size: 1em;">HTML sucks</h1>
<p>I’ve read about this on a few sites but now I’m sure:
  <u>HTML is stupid!!1</u>
<center>I can’t believe there’s no way to control the styling of
  my website without doing everything all over again!</center>
```

```html
<!-- 推荐 -->
<!DOCTYPE html>
<title>My first CSS-only redesign</title>
<link rel="stylesheet" href="default.css">
<h1>My first CSS-only redesign</h1>
<p>I’ve read about this on a few sites but today I’m actually
  doing it: separating concerns and avoiding anything in the HTML of
  my website that is presentational.
<p>It’s awesome!
```

### 实体引用

- 不需要使用实体引用，例如 `&mdash;`，`&rdquo;`或者 `&#x263a;` 假设文件和编辑器以及团队之间使用相同的编码（UTF-8）
- 唯一的例外适用于HTML中具有特殊含义的字符（如 `<` 和 `&`）以及控件或“不可见”字符（如不间断空格 `&nbsp;`）

```html
<!-- Not recommended -->
The currency symbol for the Euro is &ldquo;&eur;&rdquo;.
```

```html
<!-- Recommended -->
The currency symbol for the Euro is “€”.
```

### 省略可选标签（可选）

- **【虽然可以省略，但为了结构清晰、层次明了，项目中不要这样】**
- 为了文件大小优化和可扫描性目的，考虑省略可选标签。在HTML5规范 定义标签可以被遗漏了什么
- （这种方法可能需要将宽限期作为更宽泛的指导方针来制定，因为它与Web开发人员通常所教的内容有很大不同。出于一致性和简单性的原因，最好省略所有可选标记，而不仅仅是选择）

```html
<!-- 不推荐 -->
<!DOCTYPE html>
<html>
  <head>
    <title>Spending money, spending bytes</title>
  </head>
  <body>
    <p>Sic.</p>
  </body>
</html>
```

```html
<!-- 推荐 -->
<!DOCTYPE html>
<title>Saving money, saving bytes</title>
<p>Qed.
```

### 属性换行

- 尽量不要把所有的属性都写到一行
- 换行时，保持缩进

```html
<md-progress-circular md-mode="indeterminate" class="md-accent"
    ng-show="ctrl.loading" md-diameter="35">
</md-progress-circular>

<md-progress-circular
    md-mode="indeterminate"
    class="md-accent"
    ng-show="ctrl.loading"
    md-diameter="35">
</md-progress-circular>

<md-progress-circular md-mode="indeterminate"
                      class="md-accent"
                      ng-show="ctrl.loading"
                      md-diameter="35">
</md-progress-circular>
```

### 属性值引号

- 引用属性值时，请使用**`双引号`**

```html
<!-- 不推荐 -->
<a class='maia-button maia-button-secondary'>Sign in</a>
```

```html
<!-- 推荐 -->
<a class="maia-button maia-button-secondary">Sign in</a>
```

---

## CSS 样式规则

### 基本规范

- 为选择器分组时，将单独的选择器放在一行
- 为了易读性，在每个声明块的左边花括号前添加一个空格
- 声明快的右括号应当单独成一行
- 每条声明语句的`:`后应该插入一个空格
- 为了获取更准确的错误报告，每条声明都应该独占一行
- 所有声明语句都应该以分号结尾。最后一条声明语句后面的分号是可选的，但是不要省略
- 对于以逗号分隔的属性值，每个逗号后面都应该插入一个空格（例如：`box-shadow: 0 1px 3px #333, 0 1px 3px #333;`）
- 不要在`rgb()、rgba()、hsl()、rect()`值的内部的逗号后面插入空格，这样有利益多个属性值中区分多个颜色值
- 为选择器的属性添加双引号（例如：`input[type="text"]`）
- 避免为0值制定的单位（例如：用`margin: 0;`替代`margin: 0px;`）

```css
/* Bad CSS */
.selector, .selector-secondary, .selector[type=text] {
  padding:15px;
  margin:0px 0px 15px;
  background-color:rgba(0, 0, 0, 0.5);
  box-shadow:0px 1px 2px #CCC,inset 0 1px 0 #FFFFFF
}

/* Good CSS */
.selector,
.selector-secondary,
.selector[type="text"] {
  padding: 15px;
  margin-bottom: 15px;
  background-color: rgba(0,0,0,.5);
  box-shadow: 0 1px 2px #ccc, inset 0 1px 0 #fff;
}
```

### `ID` 和 `CLASS` 命名

- 使用有意义的或通用的ID和类名称
- 在表述明确的情况下，尽可能的使用短的 `ID` 和 `CLASS`命名

```css
/* 不推荐：无意义 */
#yee-1901 {}

/* 不推荐: presentational */
.button-green {}
.clear {}

/* 不建议 */
#navigation {}
.atr {}
```

```css
/* 推荐：特定 */
#gallery {}
#login {}
.video {}

/* 推荐：通用 */
.aux {}
.alt {}

/* 推荐：精炼 */
#nav {}
.author {}
```

### 声明顺序

- 应该把相关的属性声明归为一组，并按照下面的顺序排列
  - `Positioning`
  - `Box model`
  - `Typographic`
  - `Visual`
- 由于定位（positioning）可以从正常的文档流中移除元素，并能覆盖盒模型（box model）的样式，因此排在首位。盒模型排在第二位，因为它决定了组建的尺寸和位置
- 其他属性只是影响组件内部或者不影响前两组属性，因此排在后面
- 这里有完整的属性[排序规则](http://twitter.github.io/recess/)

```css
.declaration-order {
  /* Positioning */
  position: absolute;
  top: 0;
  right: 0;
  bottom: 0;
  left: 0;
  z-index: 100;

  /* Box-model */
  display: block;
  float: right;
  width: 100px;
  height: 100px;

  /* Typography */
  font: normal 13px "Helvetica Neue", sans-serif;
  line-height: 1.5;
  color: #333;
  text-align: center;

  /* Visual */
  background-color: #f5f5f5;
  border: 1px solid #e5e5e5;
  border-radius: 3px;

  /* Misc */
  opacity: 1;
}
```

### 类型选择器

- 避免使用类型选择器来限定ID和类名。
- 除非必要（例如使用助手类），否则不要将元素名称与ID或类结合使用
- 出于[性能原因](http://www.stevesouders.com/blog/2009/06/18/simplifying-css-selectors/)，避免不必要的祖先选择器是有用的

```css
/* 不建议 */
ul#example {}
div.error {}
```

```css
/* 建议 */
#example {}
.error {}
```

### 属性值 `0` 后的单位

- 除非需要，否则不要在值为 `0` 之后使用单位

```css
flex: 0px; /* 这个基于弹性的组件需要一个单位. */
flex: 1 1 0px; /* 没有单位不含糊，但在IE11中需要. */
margin: 0;
padding: 0;
```

### 忽略值为小数时首位的 `0`

- 属性值在 `1 到 -1` 之间时，表现为小数位（`0.1、0.5、-0.1、-0.5`），应该省略小数点前的 `0`

```css
font-size: .8em;
```

### 尽可能使用`3个字符的小写十六进制符号`

```css
/* 不建议 */
color: #eebbcc;
color: #EEBBCC;
```

```css
/* 推荐的 */
color: #ebc;
```

### 使用带有特定前缀的前缀选择器

- 在大型项目中以及嵌入到其他项目或外部站点中的代码使用ID和类名称的前缀（作为命名空间）使用简短的唯一标识符，后面跟一个破折号
- 使用命名空间有助于防止命名冲突，并且可以使维护更加轻松，例如在搜索和替换操作中

```css
.adw-help {} /* AdWords */
#maia-note {} /* Maia */
```

### `ID` 和 `CLASS` 名称分隔符

- 用连字符(`-`)分隔 `ID` 和 `CLASS` 
- 为了提高理解度和可扫描性，除了连字符之外，不要将连接词中的单词和缩写连接到任何字符

```css
/* 不推荐: 没有把 “demo” 和 “image” 分开写 */
.demoimage {}

/* 不推荐：使用下划线代替连字符 */
.error_status {}
```

```css
/* 推荐 */
#video-id {}
.ads-sample {}
```

### `CSS Hacks`

- Avoid user agent detection as well as CSS “hacks”—try a different approach first.
- It’s tempting to address styling differences over user agent detection or special CSS filters, workarounds, and hacks. Both approaches should be considered last resort in order to achieve and maintain an efficient and manageable code base. Put another way, giving detection and hacks a free pass will hurt projects in the long run as projects tend to take the way of least resistance. That is, allowing and making it easy to use detection and hacks means using detection and hacks more frequently—and more frequently is too frequently

### 内容缩进

- 缩进所有块内容，即规则内的规则以及声明，以反映层次结构并提高理解力

```less
@media screen, projection {

  html {
    background: #fff;
    color: #444;
  }

}
```

### 声明后使用分号结尾

- 出于一致性和可扩展性的原因，用分号结束每个声明

```css
/* 不建议 */
.test {
  display: block;
  height: 100px
}
```

```css
/* 推荐 */
.test {
  display: block;
  height: 100px;
}
```

### 属性名称的冒号后面使用空格

- 出于一致性原因，始终在属性和值之间使用单个空格（但属性和冒号之间没有空格）

```css
/* 不建议 */
h3 {
  font-weight:bold;
}
```

```css
/* 建议 */
h3 {
  font-weight: bold;
}
```

### 属性声明

- 在最后一个选择器和声明块之间使用空格
- 始终在最后一个选择器和开始大括号之间使用一个空格来开始声明块
- 左大括号应该与给定规则中的最后一个选择符位于同一行

```css
/* 不推荐：缺少空间 */
#video{
  margin-top: 1em;
}

/* Not recommended: unnecessary line break */
#video
{
  margin-top: 1em;
}
```

```css
/* 推荐 */
#video {
  margin-top: 1em;
}
```

- 用新行分隔选择器和声明
- 始终为每个选择器和声明开始一个新行

```css
/* 不建议 */
a:focus, a:active {
  position: relative; top: 1px;
}
```

```css
/* 推荐 */
h1,
h2,
h3 {
  font-weight: normal;
  line-height: 1.2;
}
```

- 用新行分开声明
- 始终在规则之间放置一个空白行

```css
html {
  background: #fff;
}

body {
  margin: auto;
  width: 50%;
}
```

### 属性值引号

- 对属性选择器和属性值使用单引号（`''`）而不是双引号（`""`）
- 不要在URI值（`url()`）中使用引号

```css
/* 不建议 */
@import url("https://www.google.com/css/maia.css");

html {
  font-family: "open sans", arial, sans-serif;
}
```

```css
/* 推荐 */
@import url(https://www.google.com/css/maia.css);

html {
  font-family: 'open sans', arial, sans-serif;
}
```

### 注释分块

- 用评注释把每个块分开，方便区分不同块

```css
/* Header */

#adw-header {}

/* Footer */

#adw-footer {}

/* Gallery */

.adw-gallery {}
```

### Less和Sass中的嵌套

- 避免不必要的嵌套。只有在必须将样式限制在父元素内，并且存在多个需要嵌套的元素时才使用嵌套
- [查看更多信息](http://markdotto.com/2015/07/20/css-nesting/)

```less
// Without nesting
.table > thead > tr > th { … }
.table > thead > tr > td { … }

// With nesting
.table > thead > tr {
  > th { … }
  > td { … }
}
```

### Less和Sass中的操作符

- 为了提高易读性，在圆括号中的数学表达式的数值、变量和操作符之间均添加一个空格

```less
// Bad example
.element {
  margin: 10px 0 @variable*2 10px;
}

// Good example
.element {
  margin: 10px 0 (@variable * 2) 10px;
}
```

### 编辑器配置

- 将你的编辑器按照下面的配置进行设置，以免常见的代码不一致和差异
  - 用两个空格代替tab
  - 保存文件时，删除尾部的空白符
  - 设置文件编码为UTF-8
  - 在文件结尾添加一个空白行

### CSS 的 BEM 命名方式(可选，依据项目约定而定)

- `B.E.M`
  - `B` Block 独立的模块
    - 所有东西都划分为一个独立的模块,一个header是block,header里嵌套的搜索框是block,甚至一个icon一个logo也是block
    - block可以相互嵌套
  - `E` Element 元素
    - 模块的所有下层平级元素
    - 一个Block下的所有Element无论相互层级如何,都要摊开扁平的属于Block所以 BEM 
    - 最多只有 `B+E+M` 三级,不可能出现 B+E+E+..+E+M 超长class名,也要求E不能同名
  - `M` Modifier 状态
    - 之前我们经常写的 `.current .active` 等表达状态

## `javascript`