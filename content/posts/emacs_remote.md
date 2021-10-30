---
title: "Emacs Remote"
date: 2021-10-31T00:25:19+08:00
draft: false
---

最近一段时间，因为种种原因，无法在本地开发公司的项目。我们每一个人分配了开发机，在开发机上配置好开发环境。因为一直是用的 emacs， 所以在终端上使用 emacs 感觉也还行。之前一直是用 GUI emacs，在使用 terminal emacs 的过程中，发现有一些问题是无法解决的。比如无法查看图片，treemacs 无法显示 icon, 主题颜色无法很好地展示。有一些问题属于可以解决但是似乎并不值得去做的，比如 ssh 连接断开之后还等重新打开文件，这可以通过用 tmux 等方式来解决。

vscode 的 remote-ssh 可以很方便地在本地编辑远程文件，可以算的上是杀手级功能了。查了一下怎么在本地编辑远程文件，有以下几种方式。

### 文件同步
把本地文件自动同步到远程目录，可以使用 sshfs、unionfs 等方式。本质上还是编辑本地文件。
这种方式在大多数情况下是没问题的，但是有些比较底层的项目对系统和共享库有较深的依赖，可能无法在本地正确地编译、补全。

### tramp
emacs 使用 tramp 可以做到无感地在本地编辑远程的文件。但是发现跟 lsp-mode, flycheck 集成有问题。tramp 历史很古老，但是没有 lsp-mode, flycheck， 基本没法用了。

### emacs server
另一种思路是在远程机器上开启 emacs server, 在本地用 emacsclient 连接上 emacs server. 可以用 ssh 解决 port forwading 的问题。但是遗憾地是，用 emacsclient 打开文件，结果还是在远程机器上创建了 frame。理论上，emacs server 只能在启动的机器上创建 frame。

最终还是得用终端的方式来使用 emacs. 眼看着 vscode 在易用性和功能上都超越了 emacs，或许终结编辑器圣战的将会是 vscode 吧。
