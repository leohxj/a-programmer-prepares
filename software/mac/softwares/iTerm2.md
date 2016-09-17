# iTerm2
早就听说这个终端工具了，可以完全替代terminal。

## 设置


## 配色
[Solarized](http://ethanschoonover.com/solarized), 是目前最完整的 Terminal/Editor/IDE 配色项目，几乎覆盖所有主流操作系统（Mac OS X, Linux, Windows）、编辑器和 IDE（Vim, Emacs, Xcode, TextMate, NetBeans, Visual Studio 等），终端（iTerm2, Terminal.app, Putty 等）。类似的项目还有 [Tomorrow Theme](https://github.com/chriskempson/tomorrow-theme)。

拿tomorrow-theme举例，下载Tomorrow-Night-Eighties.itermcolors文件，双击自动导入到iTerm2中，在Perferences->Profiles->Colors->Load Presets中可以看到对应的配色。修改即可。

## 中文乱码问题
确保Preferences->Profiles->Terminal->Terminal Emulation中的字符编码为UTF-8。

中文乱码的问题需要设置一下locale， 在对于的shell配置文件中，比如bash对应的就是`~/.bashrc`， zsh对应的就是`~/.zshrc`, 这里以zsh为例，打开.zshrc文件，修改其中`# You may need to manually set your language environment
export LANG=en_US.UTF-8`：

```
# You may need to manually set your language environment
export LANG=en_US.UTF-8
```


接着重启一下终端，或者输入: `source ~/.zshrc`。

## 一些快捷操作
- `command+方向键`: 切换tab。
- `command+enter`: 全屏模式。
- `command+f`: 搜索，支持正则表达式。
- `command+d`: 垂直分屏。
- `command+shift+d`: 水平分屏。
- `command+[ 或 command +]`: 在最近使用的分屏直接切换。
- `command+t`: 打开新标签。
- `command+w`: 关闭新标签。
- `command+;`: 自动补全历史命令。
- `command+r`: 清除屏幕，相当与clear.
- `command+p/n`: 上一条/下一条命令，相当于方向键上和下。
- `ctrl+r`: 搜索命令历史。

### 编辑操作
基本的Emacs移动光标方式。还有一些很好的操作方式，我觉得都可以借鉴配置到SublimeText中。

- `ctrl+d`: 删除当前字符。
- `ctrl+h`: 删除之前的字符。
- `ctrl+u`: 删除整行。
- `ctrl+k`: 删除当前到文本末尾的字符。
- `ctrl+w`: 删除光标前的单词。
- `ctrl+t`: 交换当前光标和前一个位置，互换。

## 参考资料
- [官方文档](http://iterm2.com/documentation.html)
- [我在用的mac软件(1)--终端环境之iTerm2](http://foocoder.com/blog/wo-zai-yong-de-macruan-jian.html/)