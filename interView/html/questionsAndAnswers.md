# HTML  问题答案

> 下面所有的代码都是个人作答，可能存在理解错误或者答案错误的地方，欢迎大家在[项目下方](https://github.com/springHyc/InterviewLibrary)或者[项目的 issues](https://github.com/springHyc/InterviewLibrary/issues)中留言指正。

## 1. 下面代码中，在浏览器上显示为什么会有空格？

```html
<div>
  <span>1</span>
  <span>2</span>
  <span>3</span>
</div>
```

显示结果：`1 2 3`，为什么会有空格 ?

* 原因：

  > 行内元素之间产生的间距，是由于换行符、tab( 制表符 )、空格等字符引起，而字符的大小是定义字体大小来控制。（不论空格、换行符、tab 有几个，都显示一个空格）

  三个`span`标签之间都有换行符，而 “ 行内元素之间的空格相当于块级元素的回车换行
  ” 所以会在输出时，显示空格。

* 解决办法

  1.  可以使用浮动来去除空格。

  > 不可否认，使用浮动技术是比较好的办法，实际工作中我们使用浮动也是比较多，但是也并不是每处地方都要使用浮动，而且使用浮动后还需要清除浮动的操作。

  ```html
    <div>
      <span>1</span>
      <span>2</span>
      <span>3</span>
    </div>

    <style>
      span {
        float: left;
    }
  </style>
  ```

  2.  由于 “ 行内元素之间产生的间距，是由于换行符、tab( 制表符 )、空格等字符引起，而<u>字符的大小是定义字体大小来控制</u>。” 所以我们可以控制父级元素的字符大小来去除空格。

```html
    <div>
      <span>1</span>
      <span>2</span>
      <span>3</span>
  </div>

  <style>
    div{
      font-size: 0; /* 所有浏览器 */
      *word-spacing:-1px;/* 使用word-spacing 修复 IE6、7 中始终存在的 1px 空隙，减少单词间的空白（即字间隔） */
    }
    span {
      font-size: 16;
      letter-spacing: normal;/* 设置字母、字间距为0 */
      word-spacing: normal; /* 设置单词、字段间距为0 */
    }
</style>
```

经过测试后，可发现设置 font-size:0 并不能使得换行符、tab( 制表符 )、空格等在所有浏览器中产生的额外间距消失：IE6 、 7 浏览器始终存在的 1px 空隙。

针对 IE6、7 浏览器，使用 word-spacing 修复 IE6、7 中始终存在的 1px 空隙，减少 单词间的空白（即字间隔 `*word-spacing:-1px;`

* 相关：

> 行内元素的高度由其内容撑开，**不可显示的设置其高度**，这就是为什么我们一次次的在 span 上设置 height 属性不好使的原因。

## 2. HTML 语义化是什么？

## 3. 为什么要进行 HTML 的语义化？

## 4. 写 HTML 代码时应注意什么？

* 尽可能少的使用无语义的标签。例如`div`,`span`
* 在语义不明显时，既可以使用`div`又可以使用`P`的时候，尽量使用`P`，因为`P`在默认情况下有上下间距，对兼容特殊终端有利
* 不要使用纯样式标签，例如：`b,font,u`, 该用 CSS 设置
* 需要强调的文本，可以包含在 strong 或 em 标签中（浏览器预设样式，能用 CSS 指定就不用它们）， strong 默认样式是加粗（不要用 b）， em 是斜体（不用 i）
* 使用表格时，标题要用 caption，表头用 thead，主体部分用 tbody 包围，尾部用
  tfoot 包围。表头和一般单元格要区分开，表头用 th，单元格用 td
* 表单域要用 fieldset 标签包起来，并用 legend 标签说明表单的用途
* 每个 input 标签对应的说明文本都需要使用 label 标签，并且通过为 input 设置 id
  属性，在 lable 标签中设置 for=someld 来让说明文本和相对应的 input 关联起来

> 备注 :
> [HTML5 语义元素](https://www.w3cschool.cn/html5/html5-semantic-elements.html)

## 5. 块级元素有哪些？

* div
* p
* H1
* H2
* H3
* H4
* H5
* H6
* form
* ul

## 6. 行内元素有哪些？

* span
* a
* b
* br
* i
* input

## 7. 行内块级元素有哪些？

* img
* input
* button
* texterea
* label

## 8. 行内元素和块级元素的具体区别是什么？行内元素的 padding 和 margin 可以设置吗？

行内元素:

* 和相邻的内联元素在同一行；
* width\height\padding-bottom\padding-bottom 和 margin-top\margin-bottom 都不可改变（也就是 padding 和 margin 的 left 和 right 是可以改变的）
* 宽度只与内容有关；
* 行内元素只能容纳文本或其他行内元素。

块级元素

* 总是在新的一行上开始，占据一整行，而且后面的元素也会另起一行显示；
* width\height\padding\margin 都可控制；
* 宽度始终与浏览器宽度一致，与内容无关；
* 它可以容纳内联元素和其他块元素。

### 块级元素的特性

* 总是在新行上开始，占据一整行，而且其后的元素也会另起一行显示
* 宽度 (width)、高度 (height)、内边距 (padding) 和外边距 (margin) 都可控制
* 宽带始终是与浏览器宽度一样，与内容无关
* 它可以容纳内联元素和其他块元素

### 行内元素的特性

* 和相邻的内联元素在同一行
* 宽度 (width)、高度 (height)、内边距的 top/bottom(padding-top/padding-bottom)
  和外边距的 top/bottom(margin-top/margin-bottom) 都不可改变（也就是 padding 和
  margin 的 left 和 right 是可以设置的），就是里面文字或图片的大小
* 宽度只与内容有关
* 行内元素只能容纳文本或者其他行内元素

## 9. 那么问题来了，浏览器还有默认的天生 inline-block 元素（拥有内在尺寸，可设置高宽，但不会自动换行），有哪些？( 行内块级元素 )

* `<input>`
* `<img>`
* `<button>`
* `<texterea>`
* `<label>`

## 10 每个 HTML 文件里开头都有个很重要的东西，`DOCTYPE`，这是做什么的？

`<DOCTYPE>`声明位于文档中最前面的位置，处于`<html>`标签之前。他是标准通用标记语言的文档类型声明，有助于在浏览器中正确的显示网页。此标签可以告知浏览器文档使用哪种类型的 HTML 或 XHTML 规范。

**重点就是，告诉浏览器按照何种规范来解析页面。**

## 11. get 和 post 的区别？

> 要本质的东西，不要说 API 使用上的区别

GET 和 POST 本质上就是 TCP 链接，并无差别。但是由于 HTTP 的规定和浏览器/服务器的限制，导致他们在应用过程中体现出一些不同。 GET 和 POST 还有一个重大区别，简单的说：GET 产生一个 TCP 数据包；POST 产生两个 TCP 数据包。对于 GET 方式的请求，浏览器会把 http header 和 data 一并发送出去，服务器响应 200（返回数据）； 而对于 POST，浏览器先发送 header，服务器响应 100 continue，浏览器再发送 data，服务器响应 200 ok（返回数据）。 但是，比如你想在 GET 请求里带 body，一样可以发送 Expect: 100-continue 并等待 100 continue，这是符合标准的。

作者：杨光链接：https://www.zhihu.com/question/28586791/answer/145424285
来源：知乎著作权归作者所有。商业转载请联系作者获得授权，非商业转载请注明出处。

从前端的常规使用来说，由于服务器和浏览器的限制，出现了一些不同之处：

* GET 在浏览器回退时是无害的，而 POST 会再次提交请求。
* GET 产生的 URL 地址可以被书签收藏，而 POST 不可
* GET 请求会被浏览器主动 cache，而 POST 不会，除非手动设置。
* GET 请求只能进行 url 编码，而 POST 支持多种编码方式。
* GET 请求参数会被完整保留在浏览器历史记录里，而 POST 中的参数不会被保留。
* GET 请求在 URL 中传送的参数是有长度限制的(大多数浏览器限制在 2K，大多数服务器在 64K 左右)，而 POST 么有。
* 对参数的数据类型，GET 只接受 ASCII 字符，而 POST 没有限制。
* GET 比 POST 更不安全，因为参数直接暴露在 URL 上，所以不能用来传递敏感信息。
* GET 参数通过 URL 传递，POST 放在 Request body 中。

> [这个解释很棒](https://mp.weixin.qq.com/s?__biz=MzI3NzIzMzg3Mw==&mid=100000054&idx=1&sn=71f6c214f3833d9ca20b9f7dcd9d33e4#rd)
