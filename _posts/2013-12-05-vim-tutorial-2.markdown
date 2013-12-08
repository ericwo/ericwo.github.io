---
layout: post
title:  "Vim Tutorial (2)"
date:   2013-12-05 22:00:00
categories: jekyll update
---

Vim的强大不仅体现在各种高效的操作，更有各种高端大气上档次的插件。当你安装了一定数量的插件以后，就遇到了怎么去管理插件的问题了。在这里推荐我觉得最好的插件管理工具[Vundle](https://github.com/gmarik/vundle)。

#### Vundle

Vundle是一款插件管理工具。

1. 安装

   `$ git clone https://github.com/gmarik/vundle.git ~/.vim/bundle/vundle`

2. 在.vimrc文件中设置：

   {% highlight vim%}
   set nocompatible              " be iMproved
   filetype off                  " required!

   set rtp+=~/.vim/bundle/vundle/
   call vundle#rc()

   " let Vundle manage Vundle
   " required! 
   Bundle 'gmarik/vundle'

   " My bundles here:
   "
   " original repos on GitHub
   Bundle 'tpope/vim-fugitive'
   Bundle 'Lokaltog/vim-easymotion'
   Bundle 'rstacruz/sparkup', {'rtp': 'vim/'}
   Bundle 'tpope/vim-rails.git'
   " vim-scripts repos
   Bundle 'L9'
   Bundle 'FuzzyFinder'
   " non-GitHub repos
   Bundle 'git://git.wincent.com/command-t.git'
   " Git repos on your local machine (i.e. when working on your own plugin)
   Bundle 'file:///Users/gmarik/path/to/plugin'
   " ...

   filetype plugin indent on     " required!
   {% endhighlight %}
   
3. 安装插件

   `:BundleInstall`

#### NERDTree 

NERDTree是Vim最常用的插件之一，如果你用惯了其他编辑器中显示目录和文件结构，那么[NerdTree](https://github.com/scrooloose/nerdtree)可以实现你需要的功能。

下面是一些关于NERDTree的常用设置，需要加到你自己的`.vimrc`文件中：

- `autocmd vimenter * NERDTree`：当启动VIM时就开启NERDTree
- `map <C-n> :NERDTreeToggle<CR>`：绑定`Ctrl+n`快捷键来开闭NERDTree，你可以设置任何适合自己的快捷键
- `autocmd vimenter * if !argc() | NERDTree | endif`：只是打开VIM，但还是自己启动NERDTree

#### CtrlP

[CtrlP](https://github.com/kien/ctrlp.vim)主要的功能是用来快速查找项目中的文件。在VIM正常模式中，按下ctrl+p，然后出入你想要查找文件的文件名就可以了。CtrlP还提供一些高级的查找功能。

下面是一些CtrlP的快捷键的介绍：

- `F5`：清除所在目录下的缓存
- `ctrl + j`：向下选择文件
- `ctrl + k`：向上选择文件
- `ctrl + v`：分(竖)屏打开选中的文件
- `ctrl + s`：分(横)屏打开选中的文件