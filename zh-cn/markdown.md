---
contributors:
    - ["Dan Turkel", "http://danturkel.com/"]
translators:
    - ["Fangzhou Chen","https://github.com/FZSS"]
    - ["Luffy Zhong", "https://github.com/mengzhongshi"]
    - ["Yuchen Liu", "https://github.com/smallg0at"]
    - ["Coldle", "https://github.com/yocoldle"]
filename: learnmarkdown.md
---

Markdown 由 John Gruber 于 2004年创立. 它旨在成为一门容易读写的语法结构，并可以便利地转换成 HTML（以及其他很多）格式。

在不同的解析器中，Markdown 的实现方法有所不同。
此教程会指出哪些特征是通用，哪一些只对某一解析器有效。

## HTML标签

Markdown 是 HTML 的父集，所以任何 HTML 文件都是有效的 Markdown。

```md
<!--这意味着我们可以在 Markdown 里使用任何 HTML 元素，比如注释元素，
且不会被 Markdown 解析器所影响。不过如果你在 Markdown 文件内创建了 HTML 元素，
你将无法在 HTML 元素的内容中使用 Markdown 语法。-->
```

## 标题

通过在文本前加上不同数量的hash(#), 你可以创建相对应的 `<h1>` 到 `<h6>` HTML元素。

```md
# 这是一个 <h1>
## 这是一个 <h2>
### 这是一个 <h3>
#### 这是一个 <h4>
##### 这是一个 <h5>
###### 这是一个 <h6>
```

实际效果（最终显示时会因设置而看起来不同）：

# 这是一个
## 这也是一个
### 这还是一个
#### 这依旧是一个
##### 这真的是一个
###### 这...是一个

对于 `<h1>` 和 `<h2>` 元素，Markdown 额外提供了两种添加方式。

```md
这是一个 h1
=============

这是一个 h2
-------------
```

## 文本样式

文本的*斜体*，**粗体**在 Markdown 中可以轻易实现。

```md
*此文本为斜体。*
_此文本也是。_

**此文本为粗体。**
__此文本也是__

***此文本是斜体加粗体。***
**_或者这样。_**
*__这个也是！__*
```

GitHub 也支持 Markdown，在 GitHub 的 Markdown 解析器中，我们可以使用~~删除线~~：

```md
~~此文本为删除线效果。~~
```

## 段落

段落由一个句子或是多个中间没有空行的句子组成，每个段落由一个或是多个空行分隔开来。
（注：部分解析器有无需空行就能换行的设置，这个主要看个人喜好）

```md
这是第一段落. 这句话在同一个段落里，好玩么？

现在我是第二段落。
这句话也在第二段落！


这句话在第三段落！
```

如果你想插入一个 `<br />` 标签，你可以在段末加入两个以上的空格，然后另起一
段。

(译者注：试了一下，很多解析器，并不需要空两个空格，直接换行就会添加一个`<br />`)

```md
此段落结尾有两个空格（选中以显示）。  

上文有一个 <br /> ！
```

段落引用可由 `>` 字符轻松实现。

> 对的很轻松

```md
> 这是一个段落引用。 你可以
> 手动断开你的句子，然后在每句句子前面添加 `>` 字符。或者让你的句子变得很长，以至于他们自动得换行。
> 只要你的文字以 `>` 字符开头，两种方式无异。

> 你也可以对文本进行
>> 多层引用
> 这多机智啊！
```

## 列表

- 无序列表可由星号，加号或者减号来创建

```md
* 项目
* 项目
* 另一个项目

或者

+ 项目
+ 项目
+ 另一个项目

或者

- 项目
- 项目
- 最后一个项目
```

有序序列可由数字加上点 `.` 来实现

```md
1. 项目一
2. 项目二
3. 项目三
```

即使你的数字标签有误，Markdown 依旧会呈现出正确的序号，
不过这并不是一个好主意

```md
1. 项目一
1. 项目二
1. 项目三
```

(此段与上面效果一模一样)

你也可以使用子列表

```md
1. 项目一
2. 项目二
3. 项目三
    * 子项目
    * 子项目
4. 项目四
```

你甚至可以使用任务列表，它将会生成 HTML 的选择框（checkboxes）标签。

```md
下面方框里包含 'x' 的列表，将会生成选中效果的选择框。
- [ ] 任务一需要完成
- [ ] 任务二需要完成
下面这个选择框将会是选中状态
- [x] 这个任务已经完成
```

- [ ] 你看完了这个任务（注：此选择框是无法直接更改的，即禁用状态。）

## 代码块

代码块（HTML中 `<code>` 标签）可以由缩进四格（spaces）
或者一个制表符（tab）实现

```md
    This is code
    So is this
```

在你的代码中，你仍然使用tab（或者四个空格）可以进行缩进操作

```md
    my_array.each do |item|
      puts item
    end
```

内联代码可由反引号 ` 实现

```md
John 甚至不知道 `go_to()` 函数是干嘛的!
```

在GitHub的 Markdown（GitHub Flavored Markdown）解析器中，你可以使用特殊的语法表示代码块

````md
```ruby
def foobar
  puts "Hello world!"
end
```
````

以上代码不需要缩进，而且 GitHub 会根据<code>```</code>后指定的语言来进行语法高亮显示

## 水平线分隔

水平线（`<hr/>`）可由三个或以上的星号或是减号创建，它们之间可以带或不带空格

```md
***
---
- - -
****************

下面这个就是示例
```

---

## 链接

Markdown 最棒的地方就是便捷的书写链接。把链接文字放在中括号[]内，
在随后的括弧()内加入url就可以了。

```md
[点我点我!](http://test.com/)
```

你也可以在小括号内使用引号，为链接加上一个标题（title）

```md
[点我点我!](http://test.com/ "连接到Test.com")
```

相对路径也可以有

```md
[去 music](/music/).
```

Markdown同样支持引用形式的链接

```md
[点此链接][link1] 以获取更多信息！
[看一看这个链接][foobar] 如果你愿意的话。
[link1]: http://test.com/
[foobar]: http://foobar.biz/
```

对于引用形式，链接的标题可以处于单引号中，括弧中或是忽略。引用名可以在文档的任何地方，并且可以随意命名，只要名称不重复。

“隐含式命名” 的功能可以让链接文字作为引用名

```md
[This][] is a link.
[This]: http://thisisalink.com/
```

但这种用法并不常用。

### 目录

部分 Markdown 方言样式通过列表、链接以及标题的组合来创建文章的目录。
在这种情况下，可使用填充了 hash(`#`) 的小写标题名称作为链接 id。
如果标题由多个单词组成的，可通过连字符（`-`）连接在一起。（原标题中的部分特殊字符可能被省略）

```md
- [Heading](#heading)
- [Another heading](#another-heading)
- [Chapter](#chapter)
  - [Subchapter <h3 />](#subchapter-h3-)
```

注意，这一特性未必在所有的 Markdown 解析器中以相同的方式实现。

## 图片

图片与链接相似，只需在前添加一个感叹号

```md
![这是alt,请把鼠标放在图片上](http://imgur.com/myimage.jpg "这是title")
```

引用形式也同样起作用

```md
![这是alt][myimage]
[myimage]: relative/urls/cool/image.jpg
```

## 杂项
### 自动链接

```md
<http://testwebsite.com/> 与
[http://testwebsite.com/](http://testwebsite.com/) 等同
```

### 电子邮件的自动链接

```md
<foo@bar.com>
```

### 转义字符

```md
我希望 *将这段文字置于星号之间* 但是我不希望它被
斜体化, 这么做: \*这段置文字于星号之间\*。
```

对比一下：*将这段文字置于星号之间* 和 \*将这段文字置于星号之间\*

### 键盘上的功能键

在 GitHub 的 Markdown 中，你可以使用 `<kbd>` 标签来表示功能键。

```md
你的电脑死机了？试试
<kbd>Ctrl</kbd>+<kbd>Alt</kbd>+<kbd>Del</kbd>
```

<kbd>Ctrl</kbd>+<kbd>Alt</kbd>+<kbd>Del</kbd>

（译注：可能由于网站本身样式问题，效果不明显）

### 表格

下面示例的表格长这样：

| 第一列        | 第二列    | 第三列       |
| :----------- | :-------: | ----------: |
| 我是左对齐    | 居个中    | 右对齐       |
| 注意          | 冒       | 号           |

工整一点的写法是这样的：

```md
| 第一列        | 第二列    | 第三列       |
| :----------- | :-------: | ----------: |
| 我是左对齐    | 居个中    | 右对齐       |
| 注意          | 冒       | 号           |
```

好吧，强行对齐字符是很难的。但是，至少比下面这种写法好一点——

```md
我是超级超级长的第一列 | 第二列 | 第三列
:-- | :-: | --:
这真的太丑了 | 药不能 | 停！！！！
```

## Markdownlint（Markdown 的静态分析工具）

`Markdownlint` 被创建用于简化 Markdown 的工作流程并统一编码样式。
其作为[独立工具](https://github.com/markdownlint/markdownlint)以及某些 IDE 的插件使用，可确保 Markdown 文档的有效性和可读性。

---

更多信息, 请于[此处](http://daringfireball.net/projects/Markdown/syntax)参见 John Gruber 关于语法的官方帖子，及于[此处](https://github.com/adam-p/Markdown-here/wiki/Markdown-Cheatsheet) 参见 Adam Pritchard 的摘要笔记。

如果您想了解更多主流 Markdown 方言样式的特性，请参阅：

- [GitHub Flavored Markdown](https://docs.github.com/en/github/writing-on-github/getting-started-with-writing-and-formatting-on-github/basic-writing-and-formatting-syntax)
- [GitLab Flavored Markdown](https://docs.gitlab.com/ee/user/markdown.html)
