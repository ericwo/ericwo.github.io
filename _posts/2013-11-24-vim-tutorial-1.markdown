---
layout: post
title:  "Vim Tutorial (1)"
date:   2013-11-24 22:30:00
categories: jekyll update
---

#### 关于VIM

如果你的工作语言是ruby, python, perl, c, shell等，如果你需要一个编辑器拥有快速的移动，只想要使用键盘编写代码，那么你懂的，VIM真的是能给你的带来无穷的乐趣的，当然是在你学会怎么使用这个现在最流行的文本编辑器。

在Mac或者Linux下你可以下载GVIM，里面集成了一些操作，比如你可以用`Command + s`来保存，也有tab的概念。当然打开Terminal然后使用VIM是最方便的。

#### 初级

- `i`：Insert模式，按ESC回到Normal模式
- `x`：删除当前光标所在的一个字符
- `s`：删除当前光标所在的一个字符并且变成Insert模式
- `:w`：保存
- `:q`：退出
- `hjkl`：光标上下左右的移动
- `dd`：删除当前行(delete)
- `yy`：复制当前行(copy)
- `p`：粘贴最近剪贴板的内容(paste)
- `g + 数字`：是光标跳到这个行

#### 中级

- `a`：在光标后插入
- `A`：在光标所在行末插入
- `o`：在当前光标所在行`后`插入新的一行
- `O`：在当前光标所在行`前`插入新的一样
- `cw`：删除从光标所在位置的一个完整单词
- `0`：到行首
- `^`：到本行第一个不是blank字符的位置
- `$`：到本行行末
- `g_`：到本行最后一个不是blank的字符
- `u`：undo, 撤销上次操作
- `/ruby`：搜索ruby字符串

#### 高级

- `.`：可以重复上一次的操作
- `dt + 某个字符`：删除到某个字符(delete till)
- `ct + 某个字符`：删除到某个字符并且变为Insert模式(change till)
- 'ci + 【】、{}、（）、“”、‘’'：将光标移动到这些符号里面，删除输入符号内的内容并且变成Insert模式(change inside) `这个是我最喜欢用的`
- `ctrl + v`：进入可视化模式
- `shift + v`：选中光标所在的行，并且进入可视化模式
- `:split`：创建分屏
- `:vsplit`：创建垂直分屏

#### 超高级

未完待续……（下一篇会介绍包括rails.vim, nerdtree, ctrlp, vundle等和一些比较好的vim配置和组合键的操作)
大家可以参考下我的[vimrc文件](https://github.com/eric5/vimrc/blob/master/.vimrc)
