# 前言
本篇文章主要记录阅读掘金小册[你不知道的Chrome调试技巧](https://juejin.im/book/5c526902e51d4543805ef35e/section/5c5269026fb9a049f1549e4a)时，平时工作中不常关注的点，用以加深记忆和理解。

## 了解面板
[Chrome DevTools]() 主要面板：
1. 元素面板(Elements)
2. 控制台面板(Console)
3. 源代码面板(Sources)
4. 网络面板(NetWork)
5. 性能面板(Performance)
6. 内存面板(Memory)
7. 应用面板(Application)
8. 安全面板(Security)

## 通用篇 - 使用Command
Command菜单可以帮助我们快速找到那些被隐藏起来的功能；可以使用快捷键<kbd>ctrl</kbd> + <kbd>shift</kbd> + <kbd>p</kbd>  功能大致分类如下：  
![Chrome Devtools Command 集合](https://user-gold-cdn.xitu.io/2018/12/11/1679a2e13926d71b?imageView2/0/w/1280/h/960/format/webp/ignore-error/1)
常用功能点
* 能对DOM节点进行截图
* 快速切换面板
* 快速切换主题

## 通用篇 - 代码块的使用
使用**Sources**面板中的[Snippets](#)可以保存常用的JavaScript代码块，用于日常脚本的保存