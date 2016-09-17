# 快捷键设置
Mac与PC上手最大的不同，肯定就是按键问题了。我喜欢将普通键盘上的win与alt映射为mac下的option和command键。这样键盘的布局与标准的苹果键盘相似。

通常PC下很多ctrl的组合操作，都能对于为command的组合操作。

通过一段时间的使用，我发现我切换程序多使用的是`alfred2`+`Manico`+`快捷键`方式.

`option`按键主要用于切换程序，`shift+command+其他`主要用于程序的功能。

## 全局快捷键
先提一点，我喜欢把Mac键盘最上方的那一排保持F1~F12的功能，快捷功能通过fn的组合键形式实现，实现这一点请勾选：System Perference -> Keyboard -> Use all f1, f2, etc keys as standard function keys.

修改快捷键在:System Perference -> Keyboard -> Shortcuts中。

我的主要修改如下：

**Lunchpad & Dock**:

- Turn Dock Hiding On/Off: 取消设置。
- Show Launchpad: `F4`.

**Display**: 

默认。


**Mission Control**：

- Mission Control: `Ctrl+top`.
- Show Desktop: `F11`.
- Move left a space: `Ctrl+left`.
- Move right a space: `Ctrl+right`.
- Switch to Desktop: `Command+num`. 我个人是创建了四个桌面。

**Keyboard**:

默认。

**Input Sources**:

- Select the previous input source: `Command+Space`.
- Select next source in Input menu: 取消设置。

**Screen Shots**:

默认。

**Services**:

默认。

**Spotlight**:

- Show Spotlight search field: 取消设置。
- Show Spotlight window: 取消设置。

**Accessibility**:

默认。

**App Shortcuts**:

这里的内容，是设置全局的快捷键，也可以指定某个软件内的快捷键，但是需要设置对应的菜单项名称才OK。比如我设置Finder中的`New Terminal Here`, （此功能是通过Extra Finder插件实现的）。则添加:

- Finder.app: `New Terminal Here`, 设置`ctrl+command+t`.

## Karabiner
[Karabiner](https://pqrs.org/osx/karabiner/index.html.en), 原因叫做`KeyRemap4MacBook`是一款很出色的修改键盘映射的工具，我目前还没有开发出它的潜能，只是用来替换了左下角的fn与control。

此软件可以设置几个配置方案，比如我建立了`Default`和`Coding`两种方案。

## Seil
配合Karabiner,修改CapsLock按键作用。并且通过Karabiner,设置了双击shift切换CapsLock.

## SublimeText 3
单独开贴介绍了。

## Alfred 2
~~`alt+s`, 弹出窗口。~~

配合Karabiner+Seil, 映射到CapsLock上。

## Manico
默认， `alt+num`选择程序。

## Moom
**Mouse**:

- 开启Snap to Edges and Corners: 实现拖拽到边缘放大的功能。
- Delay设置了:0.1s。

**Custom**, 添加三种自定义的方式:

- Move & Zoom: 全屏，`shift+command+1`。
- Resize: 大小100x600, `shift+command+2`。
- Move & Zoom: 屏幕上方全屏， `shift+command+3`。

## ClipMenu
设置`shift+command+v`。弹出窗口。

## ExtraFinder
**Add items to Finder menus**: 

- Copy Path: Default: Path.
- Show Hidden Items: `shift+h`.
- New Terminal Here: `iTerm`.
- New File..: 勾上.

## EuDic
**通用**:

- 启动时最小化欧陆词典主窗口: 勾上.
- LightPeek 快捷搜索: 关闭.

**取词**:

- 开启鼠标自动取词功能: `command键按下`时启动。
- 开启划词搜索: 关闭.

**快捷键**:

- 显示/隐藏窗口: `shift+command+x`.
- 其余: 关闭.

## 1Password
被誉为最好的密码管理工具。名不虚传。默认没有直接打开界面的功能，所以我通过`Manico`绑定了`option+x`的快捷方式。

默认提供的快捷键修改为：
- Lock: ~~`shift+command+L`~~， 取消原因是和sublime有冲突。
- Show Mini: `shift+command+\`
- autofill: `command+\`

## SnapRuler
这是一个测量工具，也提供了截图的功能。索性我就用它来替换系统的截图工具吧。

从keyboard->shortcuts中取消系统的截图快捷键。设置SnapRuler的快捷键为`shift+command+4`。

图片保存路径为`Pictures->SnapRuler`。



## 参考资料
- [OS X：键盘快捷键](http://support.apple.com/kb/HT1343?viewlocale=zh_CN)
- [Karabiner](https://pqrs.org/osx/karabiner/index.html.en)