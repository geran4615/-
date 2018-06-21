
# 区块元素
## 段落
Markdown段落由一个或多个连续的文本行组成，前后要有一个以上的空行（空行的定义是显示上看起来像是空的。例如，若某一行只包含空格和制表符，则改行也会被视为空行）。

普通段落不该用空格或制表符来缩进。

换行方法：在插入处先按两个以上的空格，然后回车。

## 标题
Markdown支持两种标题的语法：类Setext和类Atx形式。
### 类Setext形式
采用底线的形式，利用=（最高阶标题）和-（第二阶标题）。任何数量的=和-都可以有效果。
### 类Atx形式
在行首插入1到6个#，对应标题1到6阶。为了美观，也可以在行尾加上#，行尾的#数量也不用和开头一样。（行首的#数量已经决定了标题的阶数）。

## 区块引用 Blockquotes
### 先断好行，然后在每行的最前面加上>，如：
>this is a blockquote with two paragraphs. Lorem ipsum dolor set amet,
>consecterruer adipiscing elit. 
>
>Donec sit amet nisl. Suspendiisse id sem consectetuer libero luctus adipiscing.
### 区块引用可以嵌套（例如，引用内的引用），只要根据层次加上不同数量的>：
>this is the first lefel of quoting.
>
>>this is nested blockquote.
>
>back to the first level.
### 引用的区块内也可以使用其他的Markdown语法，包括标题、列表、代码区块等：
>## 标题
>
>1.   第一行
>2.   第二行
>
>给出例子代码：
>
>return int;
## 列表
Markdown支持有序列表和无序列表：无序列表使用*或+或-作为列表标记。有序列表则使用数字接着一个英文句点。

+ 有序列表标记上使用的数字并不会影响输出的HTML结果；（如果懒得话，可以完全不在意数字的正确性）

+ 列表项目标记通常放在最左边，最多可以缩进3个空格，项目标记后面一定要接着至少一个空格或制表符；
+ 如果列表项目间用空行分开，在输出HTML时Markdown就会将项目内容用<p>标签括起来；
+ 列表项目可以包含多个段落，每个项目下的段落都必须缩进4个空格或是1个制表符；
+ 如果要在列表项目内放入引用，那>就需要缩进；如果要放代码区块的话，该区块就需要缩进两次，也就是8个空格或是两个制表符；
+ 列表项目很可能会不小心产生，换句话说，只要在行首出现“数字-句点-空白”，Markdown就认为这是列表。为了避免混淆，可以在句点前面加上反斜杠。

要让列表看起来更漂亮，可以把内容用固定的缩进整理好，这样会好看很多：
*   Lorem ipsum dolor  

    Aliquam hendrerit  

    viverra nec
*   Donec sit amet nisl.  

    Suspendisse id sem

如果懒，也可以：
*   Lorem ipsum dolor
Aliguanm hendrerit
*   Donec sit amet nisl.

## 代码区块
Markdown会用```<pre>```和```<code>```标签来把代码区包起来。建立代码区块很简单，只要简单缩进4个空格或是1个制表符就可以,代码区块会一直持续到没有缩进的那一行（或是文件结尾）。例如：

这是一个普通段落：

    这是一个代码区块
另：

Here is an example of AppleScript:

    tell application "foo"
        beep
    end tell
在代码区块里面，&、<和>会自动转成HTML实体，这样的方式方便我们使用Markdown插入范例用的 HTML原始码（只需要复制粘贴，在加上缩进就可以了，剩下的Markdown会自行处理，例如：
    <div class="footer">
      &copy:2004 Foo Corporation
    </div>

代码区块中，一般的Markdown语法不会被转换（如星号便只是星号），这意味着可以很容易地以Markdown语法撰写Markdown语法相关的文件。
## 分割线
可以在一行中用三个以上的星号、减号或底线来建立一个分割线，行内不能有其他东西，但允许在星号或减号中间加入空格。
# 区段元素
## 链接
Markdown支持两种形式的链接语法：行内式和参考式。但不管是哪一种，链接文字都是用[]来标记。
### 行内式链接
要建立一个行内式的链接，只要在方括号后面紧跟着圆括号并插入网址链接即可。如果还想加上链接的title文字，只要在网址后面用双引号把title文字包起来即可。例如：

This is [an example](http://example.com/ "Title") inline link.  
[This link](http://example.net/) has no title attribute.

如果要链接的资源与当前文档在同一主机下，可以使用相对路径：

See my [About](/about/) page for details.
### 参考式链接
参考式链接是在链接文字的括号后面再接上一个方括号，而在第二个方括号里面要填入用以辨识链接的标记。例如，

This is [an example][id] reference-style link.

接着，在文件的任意处把这个标记的链接内容定义出来，

[id]: http://example.com/ "Optional Title Here"

链接内容定义的形式为：
+ 方括号（可以选择性地在前面加上至多三个空格来缩进），里面输入链接标记
+ 接着一个冒号
+ 接着一个以上的空格或制表符
+ 接着链接的网址，可以用尖括号包起来
+ 选择性地接着title内容，可以用单引号、双引号或是括弧包着

可以把title属性放到下一行，也可以加一些缩进，若网址太长的话，这样比较好看。如，

[id]: http://example.com/longish/path/to/resource/here
      "optional Title Here"

网址定义只有在产生链接的时候才会用到，并不会直接出现在文件中。

链接标记（辨别）标签可以包含字母、数字、空白和标点符号，但不区分大小写。

#### 隐式链接标记
隐式链接标记功能让你可以省略指定链接标记，这种情况下，链接标记会视为等同于链接文字。使用隐式链接标记只要在链接文字后面加上一个空的方括号。如果想让“google”链接到google.com，可以简化为：

[Google][]

[Google]: http://google.com/

## 强调
Markdown使用星号（*）和底线（_）作为标记强调字词的符号,但要注意用什么符号开启标签，就要用相同的符号来结束标签。被\*或\_包围的字词会被转成用```<em>```标签包围，用两个\*或\_包起来的话，则会被转成```<strong>```。例如：

*single asterisks*

_single saterisks_

**double asterisks**

__double asterisks__

un*frigging*believable

如果\*和\-两边都有空白的话，则只会被当成普通的符号。如，

un * frigging * believable

如果要在文字前后直接插入普通的星号或底线，可以用反斜线。

## 代码
如果要标记一小段行内代码，可以用反引号把它包起来，例如：

Use the `printf()` function

如果要在代码区段中插入反引号，可以用多个反引号来开启和结束代码区段：

``There is a literal backtick（`） here.``

## 图片
Markdown使用一种和链接很相似的语法来标记图片，同样也允许两种样式：行内式和参考式。
### 行内式图片

![Alt text](/path/to/img.jpg)

![Alt text](/path/to/img.jpg "Optonal title")

详细叙述如下：
+ 一个惊叹号!
+ 接着一个方括号，里面放上图片的替代文字
+ 接着一个普通括号，里面放上图片的网址，最后还可以用引号包住并加上选择性的‘title’文字。

### 参考式图片
![Alt text][id]

其中，\[id]是图片参考的名称，图片参考的定义方式则和连接参考一样：

[id]: url/to/image "Optional title attribute"

到目前为止，Markdown都还不能指定图片的宽和高。

# 其他
## 自动链接
Markdown支持以比较简短的自动链接形式来处理网址和电子邮件信箱。只要用尖括号包起来，Markdown就会自动把它转成链接，一般网址的链接文字就和链接地址一样，例如：

<http://example.com/>

Markdown会转为：

<a href="http://example.com/">http://example.com/</a>

## 反斜杠
Markdown可以利用反斜杠来插入一些在语法中有其他意义的符号，例如上文中的\\*。

Markdown支持以下这些符号前面加上反斜杠来帮助插入普通的符号：
+ \    　　　反斜杠
+ `    　　　反引号
+ \*   　　　星号
+ _    　　　底线
+ {}   　　　花括号
+ []   　　　方括号
+ ()   　　　括弧
+ \#   　　　井字号
+ \+   　　　加号
+ \-   　　　减号
+ .   　　　英文句点
+ ！   　　　惊叹号