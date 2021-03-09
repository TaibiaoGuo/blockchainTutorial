#  blockchainTutorial markdown语法规范

## 引言

对于blockchainTutorial的编辑，主要需求有：

 * 可使用Pandoc进行格式转换：通过Markdown生成多种格式的文档，至少包含Docx、PDF、HTML；
 * 可视化编辑：可方便及时得到文档的展示；
 * 科学文档：支持数学公式、引用、参考文献等；
 * 自动化输出：支持以自动化的形式输出文档。

我们对以下格式进行了分析：

 * GitHub Flavored Markdown: 
    * 优点：直接在Github上展示，IDE支持好
    * 缺点：不支持数学公式、参考文献等功能
 * Pandoc Markdown:
    * 优点：功能丰富，表达能力强，包括HTML、Latex等内联支持，与Pandoc兼容性好
    * 缺点：学习门槛高
 * Typora Markdown:
    * 优点：功能丰富，在Typora中易用性强
    * 缺点：闭源软件，无法通过命令行形式与Pandoc交互
 * Docx：
    * 优点：所见即所得
    * 缺点：难做版本控制，格式互转不方便
 * LaTex：
    * 优点：功能强大
    * 缺点：学习门槛高

综合考虑，最接近我们需求的是GitHub Flavored Markdown和Pandoc Markdown，但考虑到拓展GFM不原生支持数学公式，这会给我们的书籍编写工作带来了困难。因此，我们参考GitHub Flavored Markdown规范，选取了Pandoc Markdown格式的子集作为我们书籍编写的规范格式。

这样的选择，可以较好的满足我们的需求。

## BTM规范

在书籍编写时，只能使用BTM规范中提及的语法进行编写。BTM规范包含以下内容。

### 标题

BTM规范与GFM规范一致。特别规定，最多允许使用五级标题。标题与正文间必须空一行。
```
# 一级标题
## 二级标题
### 三级标题
#### 四级标题
#### 五级标题
```

### 清单

清单包含无序清单和有序清单，可以使用`Tab`来构造多级清单。其中无序清单使用 `*`号作为标记，有序清单使用数字接一个英文句点作为标记。

项目符号不能直接从行首最左边处输入，而必须以一至三个空格符作缩进。项目符号后必须跟着一个空格符。项目符号与上一段文字间必须空一行。

无序例子如下：
```
 * Red
 * Green
    * Yellow
    * Black
 * Blue
```

 * Red
 * Green
    * Yellow
    * Black
 * Blue

有序例子如下，数字本身代表的数值会被忽略：
```
1.  Bird
2.  McHale
3.  Parish
    1. Cat
    2. Dog
```

1. Bird
2. McHale
3. Parish
    1. Cat
    2. Dog

清单可以包含多个段落，每個項目下的段落都必須縮排4個空白或是一個tab：
```
1. This is a list item with two paragraphs. Lorem ipsum dolor
    sit amet, consectetuer adipiscing elit. Aliquam hendrerit
    mi posuere lectus.

    Vestibulum enim wisi, viverra nec, fringilla in, laoreet
    vitae, risus. Donec sit amet nisl. Aliquam semper ipsum
    sit amet velit.

2. Suspendisse id sem consectetuer libero luctus adipiscing.
```

1. This is a list item with two paragraphs. Lorem ipsum dolor
    sit amet, consectetuer adipiscing elit. Aliquam hendrerit
    mi posuere lectus.

    Vestibulum enim wisi, viverra nec, fringilla in, laoreet
    vitae, risus. Donec sit amet nisl. Aliquam semper ipsum
    sit amet velit.

2. Suspendisse id sem consectetuer libero luctus adipiscing.

如果要添加程序到清单中，则该清单对应部分要缩进两次，也就是2个Tab:

```
* A list item with a code block:

        <code goes here>
```

* A list item with a code block:

        <code goes here>

### 代码块

代码块的包含内联代码块和独立代码块。

其中，内联代码块使用成对的\`\`标志将代码嵌入到文本中。

独立代码块使用成对的\`\`\`标志让代码独立成行。我们前面所展示的markdown对这两种标志都有使用，请参见前面的例子。

### 图片

可以使用如下格式来添加图片，所有图片应当保存在当前项目中。

```
![Alt text](/path/to/img.jpg)
```

### 表格

Pandoc支持4类表格，但为了与GFM兼容，我们只使用管线表格（pipe tables）。开始与结尾的管线字符是可选的，但各直行间则必须以管线区隔。上面范例中的冒号表明了对齐方式。表头可以省略，但表头下的水平虚线必须保留，因为虚在线定义了数据域的对齐方式。

| Right | Left | Default | Center |
|------:|:-----|---------|:------:|
|   12  |  12  |    12   |    12  |
|  123  |  123 |   123   |   123  |
|    1  |    1 |     1   |     1  |

Table: 标题以Table英文冒号开头.

### 强调

使用成对的`*`可以对文本进行*倾斜*，使用成对的`**`可以对文本进行**加粗**。

### 引用

BTM规范指定BibLaTeX(.bib)作为我们管理文档参考文献的指定格式。

### 数学

BTM规范支持内联数学公式如 $1 \neq 2$ 和独行数学公式：
$$1 \neq 2$$


内联数学公式使用成对的`$`进行标记，独行数学公式使用成对的`$$`进行标记。数据公式会被TeX数学公式处理。

### 其他

中英文间请勿空格，否则Docx格式中会意外换行，谢谢合作。

### 不能使用的功能

一些功能，在本项目中不应被使用。不能被使用的功能如下：

 * 引言
 * 分割线
 * HTML标记
 * 脚注
 * 删除线
 * 上下标

## BTM带版本管理的编写工具链

 * Markdown格式：扩展GFM（GitHub Flavored Markdown）；
 * 推荐编辑器：`Visual Studio Code`+`Pandoc Markdown Preview`插件或`typora`；
 * 格式转换器：Pandoc（非必须）。

## BTM自动化流程

1. Github Action被触发，拉取Main分支代码；
2. Pandoc工具将指定BTM格式Markdown文件编译成Docx、PDF、HTML的构件；
3. 如需要发布新的Release，则构建被打包到release中可以被其他人下载；
4. 发布的Release可以被选择更新到项目的网站。

## 附录

Markdown是一种简单的标记语言，它允许人们使用文本编辑器编写文档并将这些文档转换为许多不同的格式。除其他功能外，它还可以很好地用于记录源代码，因为可以使用Git或您选择的源代码控制系统检入Markdown文档并对其进行版本控制。

Pandoc是一种功能强大的“瑞士军刀”工具，用于在各种格式之间转换文档。它不限于Markdown作为输入（源）格式，而是在此上下文中广泛使用。

Visual Studio Code是Microsoft创建的可靠，轻量级的代码编辑器。

如果您不熟悉 Markdown 语法，请查看 Adam Pritchard 的 Markdown 备忘单，其中包括标准 Markdown 语法以及我们将在编辑器中使用的扩展 GFM（GitHub Flavored Markdown）。 Markdown 是一种易于学习的语法，而且，额外的好处是，您不必费心使用尖括号，打开和关闭标签等。