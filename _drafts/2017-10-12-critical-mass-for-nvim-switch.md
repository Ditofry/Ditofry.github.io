---
layout: post
title: "Reaching Critical Mass with NVIM"
subtitle: "What I needed to know in order to start really using NVIM"
categories: nvim vim
---

### Plugins
There's new hotness for plugin management, but I'm just using vim plug for
now.

### Critical Plugins
 - Linting
 - Bulk-indent
 - Bulk-comment

### Finding shit
This is one area where I decided to NOT go with what is available to nvim
natively.  Rather, I went with (fzf.vim)[https://github.com/junegunn/fzf.vim]
.  It's righteous, and I would recommend it.

### File management and navigation
This is without using the super popular and seemingly really cool Nerd Tree,
which I will definitely explore once the other sections in this post feel
comfortable. Until then I'll be using the default file viewer.
**Enter File Explorer from terminal** `nvim .` (or `nvim path`)
**Enter File Explorer from opened file** `-`
**Move up and down** `jk` or arrows
**Search current buffer (view)** `/file-name` 
**Step into dir or Open File** `<return>` or `<enter>`
**Step back up to higher directory (same as** `cd ..`**)** `-`

**Create new dir** `d`
**Create new file** `%`
**Duplicate file**
**Duplicate dir**
**Delete file or dir under cursor** `D`
**Rename file or dir under cursor** `R`

### Multi tasking/viewing
In the beginning I would `nvim` into a file, do some stuff, and then open
a new terminal tab, or worse, `:q` out and navigate to a new file.  It was
untenable in comparison to having a file tree, tabs, and split panes in my
editor.

Here's what I needed in order to make this part of editing not awful.
In an NVIM buffer:
 - **Split pane** `:vsplit` and `:hsplit` for vert/horiz splits **or...**
 - **Split pane** `ctrl-w, v` for vertical split, `ctrl-w, S` for horizontal split
 - **Switch focused pane** `ctrl-w, (direction)` or `ctrl-w, ctrl-w` to jump to "next pane".
 - **Close pane** `ctrl-w, q`
 - **Open Terminal in current pane** `:terminal`
 - **Switch buffer** e.g. between code and terminal `number+ctrl-^`, no number toggles between what was last used
     
### Editing text

