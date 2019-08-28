---
title: Markdown教程
date: 2019-01-15 18:22:37
tags: Markdown
categories: Essay
img: /img/markdown.jpg
preview: /img/markdown.jpg
---
想写博客记录自己学习的点点滴滴吗？点开这里 =>[***传送门***](https://github.com/Lee981265/Free-Style/blob/master/Markdown.md)<!--more  -->

## Guide

这是一篇讲解如何正确使用 **Markdown** 的排版示例，学会这个很有必要，能让你的文章有更佳清晰的排版。


> 引用文本：Markdown is a text formatting syntax inspired

## 语法指导

### 普通内容

这段内容展示了在内容里面一些小的格式，比如：


- **加粗** - `**加粗**`
- *倾斜* - `*倾斜*`
- ~~删除线~~ - `~~删除线~~`
- `Code 标记` - ``Code 标记``
- [超级链接](https://github.com) - `[超级链接](https://github.com)`
- [username@gmail.com](mailto:username@gmail.com) - `[username@gmail.com](mailto:username@gmail.com)`


### 表情符号 Emoji

支持大部分标准的表情符号，可使用输入法直接输入

#### 一些表情例子

:smile: :laughing: :dizzy_face: :sob: :cold_sweat: :sweat_smile:  :cry: :triumph: :heart_eyes: :relaxed:
:+1: :-1: :100: :clap: :bell: :gift: :question: :bomb: :heart: :coffee: :cyclone: :bow: :kiss: :pray: :anger:

效果如图所示：

<div align=center>![表情符号](/img/emoji.png)

### 大标题 - Heading 3

你可以选择使用 H1 至 H6，使用 ##(N) 打头。

> NOTE: 别忘了 # 后面需要有空格！

#### Heading 4

##### Heading 5

###### Heading 6

### 图片

```
![alt 文本](https://lee981265.github.io/img/Leebolg.png)
![alt 文本](https://lee981265.github.io/img/Leebolg.png "图片 Title 值")
```

效果如图所示：

<img alt="lee" src="https://lee981265.github.io/img/Leebolg.png" width="240" height="275">
支持复制粘贴直接上传。

### 代码块

#### 普通

```
*emphasize*    **strong**
_emphasize_    __strong__
var a = 1
```

#### 语法高亮支持

如果在 ``` 后面跟随语言名称，可以有语法高亮的效果哦，比如:

##### 演示 Go 代码高亮

```Go
package main

import "fmt"

func main() {
	fmt.Println("Hello, 世界")
}
```

##### 演示 Java 高亮

```java
public class HelloWorld {

    public static void main(String[] args) {
        System.out.println("Hello World!");
    }

}
```

效果如图所示：

<div align=center>![Go](/img/go.png)

<div align=center>![Java](/img/java.png)

> Tip: 语言名称支持下面这些: `ruby`, `python`, `js`, `html`, `erb`, `css`, `coffee`, `bash`, `json`, `yml`, `xml` ...

### 有序、无序列表

#### 无序列表

- Java
  - Spring
    - IoC
    - AOP
- Go
  - gofmt
  - Wide
- Node.js
  - Koa
  - Express

#### 有序列表

1. Node.js
   1.1. Express
   1.2. Koa
   1.3. Sails
2. Go
   2.1. gofmt
   2.2. Wide
3. Java
   3.1. Latke
   3.2. IDEA

### 表格

如果需要展示数据什么的，可以选择使用表格。

| header 1 | header 3 |
| -------- | -------- |
| cell 1   | cell 2   |
| cell 3   | cell 4   |
| cell 5   | cell 6   |

### 隐藏细节
<details>
<summary>Summary</summary>
Details
</details>

### 段落

留空白的换行，将会被自动转换成一个段落，会有一定的段落间距，便于阅读。

请注意后面 Markdown 源代码的换行留空情况。

### 数学公式

$$a^2 + b^2 = \color{red}c^2$$

效果如图所示：

<div align=center>![数学公式](/img/Qmath.png)

### 复选框

command line  
- [ ] initiate  
- [ ] participate  
- [ ] redeem  
- [ ] refund  

doc  
- [x] ReadMe
- [x] ReadMe_CN

### 流程图

```flow
st=>start: Start
op=>operation: Your Operation
cond=>condition: Yes or No?
e=>end

st->op->cond
cond(yes)->e
cond(no)->op
```

效果如图所示：

<div align=center>![流程图](/img/流程图.png)

### 时序图

```sequence
张三->李四: 嘿，小四儿, 写博客了没?
Note right of 李四: 李四愣了一下，说：
李四-->张三: 忙得吐血，哪有时间写。
```

效果如图所示：

<div align=center>![时序图](/img/时序图.png)

### 2019

弹指间2018悄然溜走，我也在昨天渡过22岁生日。新的一年祝大家好运常来，在2019我决定开始学习python和java，也会在这里和大家分享一下我踩过的坑和笔记。***2019加油！*** :smirk_cat:）
