
### 兼容 HTML
Markdown是纯文本文件，其中可以使用html语言，html语言内部忽略Markdown语法(因此**示例1**中的Markdown不会加粗)。   
HTML 区块元素――比如`<div>、<table>、<pre>、<p>`等标签，必须在前后加上**空行**与其它内容区隔开，还要求它们的开始标签与结尾标签**不能用制表符或空格来缩进**。  
**注意**：要想让字符原样输出，而不转义成html语言，可在将需要原样输出的语句用反引号\`包裹起来，Markdown会将其替换成`<code>`标签。   
（在Sublime Text 3中，正常语句显示成白色，html标签显示成红色，转义字符为蓝紫色。）  

---

**示例1：**   
这是一个普通段落。   

<table>
    <tr>
        <td>Foo</td>
        <td>**Markdown**</td>
        <td>&amp;: and</td>
        <td>&: and</td>
    </tr>
</table>

这是另一个普通段落。   
&: and   
&copy;

### 特殊字符自动转换
html中由于<是标签符号，所以只能使用`&lt;`,markdown中既可以直接使用<，也可以使用转义后的`&lt;`。   

---

**示例2:**

4 < 5  Markdown会将其转换为：  4 `&lt;` 5   

## 区块元素
### 段落
一个 Markdown 段落是由**一个或多个连续的**文本行组成，它的前后要有一个以上的**空行**
（空行的定义是<u>显示上看起来像是空的，便会被视为空行</u>。
比方说，若某一行只包含空格和制表符，则该行也会被视为空行）。   
Markdown中空白符在很多语法中都有运用，需要小心灵活运用。     
因此，普通段落不该用空格或制表符来缩进。   

### 换行
两个或更多空格加回车，相当于`<br/>`。   
其优点是方便阅读,但两种写法的效果是一样的。   

### 标题
类 Setext 形式是用底线的形式，利用 = （最高阶标题）和 - （第二阶标题），如**示例3**。

---

**示例3：**  

This is an H1
=============

This is an H2
-------------

类 Atx 形式则是在行首插入1到6个#再加上一个**空格**，对应到标题 1 到 6 阶，如**示例4**.

---

**示例4：**

# 这是 H1
## 这是 H2
###### 这是 H6   ##
行尾可以添加#号，其个数**不需要**和行首的#号个数一致。   

### 区块引用 Blockquotes
+ 先分好行，然后在每行的前面加上>，一个>后不跟任何内容视为段落结束，如**示例5**。  
**示例5: 一个引用，两个段落**

> This is a blockquote with two paragraphs. Lorem ipsum dolor sit amet,
> consectetuer adipiscing elit. Aliquam hendrerit mi posuere lectus.
> Vestibulum enim wisi, viverra nec, fringilla in, laoreet vitae, risus.
> 
> Donec sit amet nisl. Aliquam semper ipsum sit amet velit. Suspendisse
> id sem consectetuer libero luctus adipiscing.

---
+ Markdown 也允许你偷懒只在整个段落的第一行最前面加上 > ,如**示例6**。  
**示例6: 两个引用，每个引用一个段落**

> This is a blockquote with two paragraphs. Lorem ipsum dolor sit amet,
consectetuer adipiscing elit. Aliquam hendrerit mi posuere lectus.
Vestibulum enim wisi, viverra nec, fringilla in, laoreet vitae, risus.

> Donec sit amet nisl. Aliquam semper ipsum sit amet velit. Suspendisse
id sem consectetuer libero luctus adipiscing.

---
+ 区块引用可以嵌套（例如：引用内的引用），只要根据层次加上不同数量的 > ：  
**示例7: 引用嵌套**

> This is the first level of quoting.
>
> > This is nested blockquote.
>
> Back to the first level.

---
+ 引用的区块内也可以使用其他的 Markdown 语法，包括标题、列表、代码区块等：   
**示例8:**

> ## 这是一个标题。
> 
> 1.   这是第一行列表项。
> 2.   这是第二行列表项。
> 
> 给出一些例子代码：
> 
>     return shell_exec("echo $input | $markdown_script");

### 列表
Markdown 支持有序列表和无序列表。   
无序列表使用**星号、加号或减号**加上一个或多个**空格**或**制表符**作为列表标记，同一列表中只能使用一种符号，下面是三个无序列表：   
*   Red
*   Green
*   Blue
+ Red
+ Green
+ Blue
+Red
+Green
+Blue
(单独一个换行，之前无两个空格，则视为一个空格分隔符。)
- Red
-	Green
-	Blue

有序列表则使用**数字**加上一个英文**句点**再加**空格**,从第一数字开始标号：  

7.  Bird
2.  McHale
3. Parish
3.  Parish
3.  Parish


<ol>
	<li>Bird</li>
	<li>McHale</li>
	<li>Parish</li>
</ol>

*   Lorem ipsum dolor sit amet, consectetuer adipiscing elit.
    Aliquam hendrerit mi posuere lectus. Vestibulum enim wisi,
    viverra nec, fringilla in, laoreet vitae, risus.
*   Donec sit amet nisl. Aliquam semper ipsum sit amet velit.
    Suspendisse id sem consectetuer libero luctus adipiscing.

*   Lorem ipsum dolor sit amet, consectetuer adipiscing elit.
Aliquam hendrerit mi posuere lectus. Vestibulum enim wisi,
viverra nec, fringilla in, laoreet vitae, risus.
*   Donec sit amet nisl. Aliquam semper ipsum sit amet velit.
Suspendisse id sem consectetuer libero luctus adipiscing.
* 	段落中多个空格视作一个空格。   
	两个空格加换行仍视为换行。

---
+ 如果列表项目间用空行分开，在输出HTML时，Markdown就会将项目内容用< p>标签包起来，举例来说：
*   Bird
*   Magic

会被转换为：

	<ul>
		<li>Bird</li>
		<li>Magic</li>
	<ul>

但是这个：
*   Bird

*   Magic

会被转换为：

	<ul>
	  <li><p>Bird</p></li>
	  <li><p>Magic</p></li>
	</ul>

---
+ 列表项目可以包含多个段落，每个项目下的段落都必须缩进 4 个空格或是 1 个制表符：

1.  This is a list item with two paragraphs. Lorem ipsum dolor
    sit amet, consectetuer adipiscing elit. Aliquam hendrerit
    mi posuere lectus.

    Vestibulum enim wisi, viverra nec, fringilla in, laoreet
    vitae, risus. Donec sit amet nisl. Aliquam semper ipsum
    sit amet velit.

	Vestibulum enim wisi, viverra nec, fringilla in, laoreet
vitae, risus. Donec sit amet nisl. Aliquam semper ipsum
sit amet velit.

    This is the second paragraph in the list item. You're
only required to indent the first line. Lorem ipsum dolor
sit amet, consectetuer adipiscing elit.

2.  Suspendisse id sem consectetuer libero luctus adipiscing.

---
+ 如果要在列表项目内放进引用，那 > 就需要缩进：??????

*   A list item with a blockquote:

	> This is a blockquote
	>
	> inside a list item.
	> 这一句和上一句在同一行内。
	>
	> 此引用在列表内

> This is a blockquote
>
> inside a list item.
> 这一句和上一句在同一行内。
>
> 此引用与上面的列表并列。

+ 如果要放代码区块的话，该区块就需要缩进两次，也就是 8 个空格或是 2 个制表符，且首尾有空行：

*   列表项包含一个代码区块：

        <font>font</font>
        上面一行代码，是一个段落，因为前后有空行，每行有缩进。
        一行不缩进则是html。


### 反斜杠转义
下面前两行是列表，第三行是普通语言。   

1986. What a great season.
1986. What a great season.

1986\. What a great season.   

### 代码区块
程序代码通常具有自己的排版，要想原样展示而非以一般段落的方式排版，Markdown会用`<pre>`和`<code>`标签来把代码区块包起来。   
如果代码一行长于页面宽度，会有*横向滑动条*。   
在代码区块里面，&、<和>会自动转成HTML实体，Markdown插入范例用的HTML代码，粘贴后加上**缩进**就可以了，剩下的 Markdown 都会自动处理。   
要在 Markdown 中建立代码区块很简单，只要简单地**缩进 4 个空格或是 1 个制表符**就可以。   
一个代码区块会一直持续到没有缩进的那一行（或是文件结尾）。   
例如，下面的输入：   

这是一个普通段落：

    这是一个代码区块。
    这是一个代码区块。
    这是一个代码区块。

Markdown 会转换成：

	<p>这是一个普通段落：</p>

	<pre><code>这是一个代码区块。<br/>这是一个代码区块。<br/>这是一个代码区块。</code></pre>

这个每行一阶的缩进（4 个空格或是 1 个制表符），都会被移除，例如：

Here is an example of AppleScript:

    tell application "Foo"
        beep
    end tell

会被转换为：

	<p>Here is an example of AppleScript:</p>

	<pre><code>tell application "Foo"
	    beep
	end tell
	</code></pre>

### 分隔线
你可以在一行中用三个以上的星号、减号、底线(标题使用的分割线)来建立一个分隔线，行内不能有其他东西，但可在星号或是减号中间插入空格。   
下面每种写法都可以建立分隔线：   

* * *

文中**n个以上**表示*n个或更多*。

***

*****

- - -

------------------------------------


## 区段元素
### 链接

Markdown 支持两种形式的链接语法： 行内式和参考式两种形式。

不管是哪一种，链接文字都是用 [方括号] 来标记。

要建立一个行内式的链接，只要在方块括号后面紧接着圆括号并插入网址链接即可，如果你还想要加上链接的 title 文字，只要在网址后面，用双引号把 title 文字包起来即可，例如：

	[显示的文本]（网址 "光标悬浮时显示的提示文字"）

This is [an example](http://example.com/ "Title") inline link.

[This link](http://example.net/) has no title attribute.
会产生：

	<p>This is <a href="http://example.com/" title="Title">
	an example</a> inline link.</p>

	<p><a href="http://example.net/">This link</a> has no
	title attribute.</p>

如果你是要链接到同样主机的资源，你可以使用相对路径：

See my [About](/about/) page for details.

---
参考式的链接是在链接文字的括号后面再接上另一个方括号，而在第二个方括号里面要填入用以辨识链接的标记：
This is [an example][id] reference-style link.   

你也可以选择性地在两个方括号中间加上一个空格：   
This is [an example] [foo3] reference-style link.

接着，在文件的任意处，你可以把这个标记的链接内容定义出来：   

[id]: http://example.com/  "Optional Title Here"

链接内容定义的形式为：   
方括号（前面可以选择性地加上至多三个空格来缩进），里面输入链接文字
接着一个冒号
接着一个以上的空格或制表符
接着链接的网址,可以使用或尖括号包裹
选择性地接着 title 内容，可以用单引号、双引号或是括弧包着
下面这三种链接的定义都是相同：

[foo1]: http://example1.com/  "Optional Title Here"
 [foo2]: <http://example2.com/>  "Optional Title Here"
  [foo3]: http://example3.com/
  		'Optional Title Here'
   [foo4]: http://example4.com/  (Optional Title Here)

请注意：有一个已知的问题是 Markdown.pl 1.0.1 会忽略*单引号*包起来的链接 title。

链接网址也可以用尖括号包起来：

[id]: <http://example.com/>  "Optional Title Here"
你也可以把 title 属性放到下一行，也可以加一些缩进，若网址太长的话，这样会比较好看：

[id]: http://example.com/longish/path/to/resource/here
    "Optional Title Here"

网址定义只有在产生链接的时候用到，并不会直接出现在文件之中。

链接辨别标签可以有字母、数字、空白和标点符号，但是并不区分大小写，因此下面两个链接是一样的：

	[link text][a]
	[link text][A]

---
隐式链接标记功能让你可以省略指定链接标记，这种情形下，链接标记会视为等同于链接文字，要用隐式链接标记只要在链接文字后面加上一个空的方括号，如果你要让 "Google" 链接到 google.com，你可以简化成：

[Google][]

然后定义链接内容：

[Google]: http://google.com/

由于链接文字可能包含空白，所以这种简化型的标记内也许包含多个单词：

Visit [Daring Fireball][] for more information.
然后接着定义链接：

[Daring Fireball]: http://daringfireball.net/
链接的定义可以放在文件中的**任何**一个地方，我比较偏好直接放在链接出现段落的后面，你也可以把它放在文件最后面，就像是注解一样。

下面是一个参考式链接的范例：

I get 10 times more traffic from [Google] [1] than from
[Yahoo] [2] or [MSN] [3].

  [1]: http://google.com/        "Google"
  [2]: http://search.yahoo.com/  "Yahoo Search"
  [3]: http://search.msn.com/    "MSN Search"
如果改成用链接名称的方式写：

I get 10 times more traffic from [Google][] than from
[Yahoo][] or [MSN][].

  [google]: http://google.com/        "Google"
  [yahoo]:  http://search.yahoo.com/  "Yahoo Search"
  [msn]:    http://search.msn.com/    "MSN Search"
上面两种写法都会产生下面的 HTML。

	<p>I get 10 times more traffic from 
	<a href="http://google.com/" title="Google">Google</a> 
	than from <a href="http://search.yahoo.com/" title="Yahoo Search">Yahoo</a>
	or <a href="http://search.msn.com/" title="MSN Search">MSN</a>.</p>
下面是用行内式写的同样一段内容的 Markdown 文件，提供作为比较之用：

I get 10 times more traffic from [Google](http://google.com/ "Google")
than from [Yahoo](http://search.yahoo.com/ "Yahoo Search") or
[MSN](http://search.msn.com/ "MSN Search").
参考式的链接其实重点不在于它比较好写，而是它比较好读，比较一下上面的范例，使用参考式的文章本身只有 81 个字符，但是用行内形式的却会增加到 176 个字元，如果是用纯 HTML 格式来写，会有 234 个字元，在 HTML 格式中，标签比文本还要多。

使用 Markdown 的参考式链接，可以让文件更像是浏览器最后产生的结果，让你可以把一些标记相关的元数据移到段落文字之外，你就可以增加链接而不让文章的阅读感觉被打断。

### 强调
_____
Markdown 使用星号（\*）和底线（\_）作为标记强调字词的符号，被\* 或\_ 包围的字词会被转成用`<em>`标签包围(**包围**的意思是**必须紧挨着内容**)，用两个\* 或\_ 包起来的话，则会被转成 `<strong>`，例如：   


*single asterisks*
_single underscores_

**double asterisks**
__double underscores__

会转成：

	<em>single asterisks</em>
	<em>single underscores</em>

	<strong>double asterisks</strong>
	<strong>double underscores</strong>

你可以随便用你喜欢的样式，唯一的限制是，**你用什么符号开启标签，就要用什么符号结束。**
  
斜体、强调也**可以直接插在文字中间**：  
un*frigging*believable  
un**frigging**believable  
但是如果你的 * 和 _ 两边都有空白的话，它们就只会被当成普通的符号。  
un* frigging* believable  
un** frigging** believable  
   
如果要在文字前后直接插入普通的星号或底线，你可以用反斜线转义：

\*this text is surrounded by literal asterisks\*

### 代码
如果要标记一小段行内代码，你可以用**一个或多个反引号(\`)**把它包起来,但前后必须一致，例如：   


Use the `printf()` function.

会产生：

	<p>Use the <code>printf()</code> function.</p>

如果要在代码区段内**插入反引号**，你可以用多个反引号来开启和结束代码区段：

``There is a literal backtick (`) here.``
这段语法会产生：

	<p><code>There is a literal backtick (`) here.</code></p>

代码区段的起始和结束端都可以放入一个空白，起始端后面一个，结束端前面一个，这样你就可以在区段的一开始就插入反引号：

A single backtick in a code span: `` ` ``

A backtick-delimited string in a code span: `` `foo` ``会产生：

	<p>A single backtick in a code span: <code>`</code></p>

	<p>A backtick-delimited string in a code span: <code>`foo`</code></p>

在代码区段内,&和尖括号都会被自动地转成 HTML 实体，这使得插入 HTML 原始码变得很容易，Markdown 会把下面这段：

Please don't use any `<blink>` tags.
转为：

	<p>Please don't use any <code>&lt;blink&gt;</code> tags.</p>

你也可以这样写：  
`&#8212;` is the decimal-encoded equivalent of `&mdash;`.
以产生：

	<p><code>&amp;#8212;</code> is the decimal-encoded
	equivalent of <code>&amp;mdash;</code>.</p>

### 图片
以链接形式插入图片，链接的行内式、参考式皆可。

行内式的图片语法看起来像是：  
语法如下：

	![alt text](photo_url)
	![alt text](photo_url "title")

一个惊叹号!
接着一个方括号，里面放上图片的替代文字
接着一个普通括号，里面放上图片的网址，最后还可以用引号包住并加上 选择性的 'title' 文字。

![壁纸 1](/img/wallpaper1.jpg)

![壁纸 2](/img/wallpaper2.jpg "wallpaper 2")

---
参考式的插入图片语法如下：  

	![Alt text 1][]
		提示文本(Alt text)就是参考名称		
	![Alt text 2][id]
		「id」是图片参考的名称，图片参考的定义与链接参考一样：

	[Alt text 1]: url/to/image  "Optional title attribute"
	[id]: url/to/image  "Optional title attribute"

**示例**

！[退不可得][]
！[不如进取][brjq]

[退不可得]: img/退不可得.jpg "狄龙-英雄本色"
[brjq]: img/不如进取.jpg "Mark哥-英雄本色"

到目前为止， Markdown 还没有办法指定图片的宽高，如果你需要的话，你可以使用普通的 `<img>`标签。

## 其它
### 自动链接
Markdown 支持以比较简短的自动链接形式来处理网址和电子邮件信箱，只要用尖括号包起来， Markdown 就会自动把它转成链接。  
一般网址的链接文字就和链接地址一样，例如：

<http://example.com/>  

Markdown 会转为：

	<a href="http://example.com/">http://example.com/</a>

邮址的自动链接也很类似，只是 Markdown 会先做一个编码转换的过程，把文字字符转成 16进位码的 HTML 实体，这样的格式可以糊弄一些不好的邮址收集机器人，例如：

<address@example.com>

Markdown 会转成：

	<a href="&#x6D;&#x61;&#x69;&#x6C;&#x74;&#x6F;&#x3A;
		&#x61;&#x64;&#x64;&#x72;&#x65;&#x73;&#x73;&#x40;
		&#x65;&#x78;&#x61;&#x6d;&#x70;&#x6C;&#x65;&#x2E;
		&#x63;&#x6F;&#x6D;">
		&#x61;&#x64;&#x64;&#x72;&#x65;&#x73;&#x73;&#x40;
		&#x65;&#x78;&#x61;&#x6d;&#x70;&#x6C;&#x65;&#x2E;
		&#x63;&#x6F;&#x6D
	</a>

在浏览器里面，这段字串（其实是 `<a href="mailto:address@example.com">address@example.com</a>`）会变成一个可以点击的「address@example.com」链接。

### 反斜杠
Markdown 可以利用反斜杠来插入一些在语法中有其它意义的符号，例如：如果你想要用星号加在文字旁边的方式来做出强调效果（但不用 `<em> `标签），你可以在星号的前面加上反斜杠：   
\*literal asterisks\*   

Markdown 支持以下这些符号前面加上反斜杠来帮助插入普通的符号：
1. \\   反斜线
1. \`   反引号
1. \*   星号
1. \_   底线
1. \{\}  花括号
1. \[\]  方括号
1. \(\)  括弧
1. \#   井字号
1. \+   加号
1. \-   减号
1. \.   英文句点
1. \!   惊叹号

## 注意
+  注意空白符的使用。
+  **段落、html语言**：首尾有空行，内容顶格写。
+  **代码区块**：首尾有空行，内容缩进4个空格或1个制表符。
+  **列表中的每个段落、引用**：内容缩进4个空格或1个制表符。
+  **列表中的代码区块**：首尾有空行，内容缩进8个空格或2个制表符。
+  **非1开始的有序列表**：首尾有空行。
+  **无序列表、1开始的有序列表**：首部无需空行，尾部无空格可能影响后面文本的显示，所以最好还是首尾有空行。  

## test
*  **<**
*  **8**
*  **=**
*  **+**
*  **\+**
*  **壹**
*  `<p>Please don't use any **<code>&lt;blink&gt;</code>** tags.</p>`
*

		<p>Please don't use any **<code>&lt;blink&gt;</code>** tags.</p>
		<p>Please don't use any **<code>&lt;blink&gt;</code>** tags.</p>
		<p>Please don't use any **<code>&lt;blink&gt;</code>** tags.</p>

<p>Please don't use any **<code>&lt;blink&gt;</code>** tags.</p>
<p>Please don't use any **<code>&lt;blink&gt;</code>** tags.</p>
<p>Please don't use any **<code>&lt;blink&gt;</code>** tags.</p>
	 
	<p>Please don't use any **<code>&lt;blink&gt;</code>** tags.</p>
	<p>Please don't use any **<code>&lt;blink&gt;</code>** tags.</p>
	<p>Please don't use any **<code>&lt;blink&gt;</code>** tags.</p>

**注意**：三行html段落代码出现三次。  
第一次作为列表中了代码区块，首尾有空行，缩进2个制表符；  
第二次作为列表中了html代码，首尾有空行，定格写；  
第三次作为列表中了代码区块，首尾有空行，缩进1个制表符；  
