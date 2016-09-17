# Sublime Text 3--Mac版
Mac篇其实应该和Windows差不多，主要区别是一些按键的设置和插件的配置。

## 特色功能
- super+p，搜索。这个搜索可以左侧的Folders里所以文件，而且是模糊搜索，不需要完整的文件名。配合#, @, :可以搜索变量，函数，行数。
- 多行编辑。按住super加左击，可以出现多个光标位置。
- 多重选择， super+d可以多重选择，结合光标键，可以批量修改。
- 多屏编辑，super+alt+数字键。
- Projects，通过View->Side Bar->show Side Bar左侧文件结构管理。
- snippet, 不同格式的文件，可以设置不同的snippet,就是简写，通过tab扩展成相应的内容。
- 各种插件支持
- 正则表达式搜索,比如我要删除所有的空行，可以使用`^[\s]*\n`来选择所有空行。可以使用`(?<=<h2>).+(?=</h2>)`来匹配h2标签内的内容。
- super+shift+p，功能菜单。只有你想不到，没有做不到的事情。

## 下载安装
ST3虽然没有提供稳定版本，但是相比ST2，速度提升还是很明显的。缺点就是插件不够完善，以及插件的编写全部采用Python3.x版本。这里给出ST3[下载地址](http://www.sublimetext.com/3)。
 
个人最喜欢的一点新特性是：新增了跳转到函数定义处功能，在大菜单Goto中可以查看到。

首次使用，建议先打开侧栏，方便管理文件结构。打开方式:`View->Side Bar->Show Side Bar`。

## 插件安装
插件通过[Package Control](https://sublime.wbond.net/installation#Simple)来管理。
 
### 安装Package Control
进入Package Control页面，选择对应版本的代码进行复制，比如ST3如下：
```
import urllib.request,os,hashlib; h = '7183a2d3e96f11eeadd761d777e62404' + 'e330c659d4bb41d3bdf022e94cab3cd0'; pf = 'Package Control.sublime-package'; ipp = sublime.installed_packages_path(); urllib.request.install_opener( urllib.request.build_opener( urllib.request.ProxyHandler()) ); by = urllib.request.urlopen( 'http://sublime.wbond.net/' + pf.replace(' ', '%20')).read(); dh = hashlib.sha256(by).hexdigest(); print('Error validating download (got %s instead of %s), please try manual install' % (dh, h)) if dh != h else open(os.path.join( ipp, pf), 'wb' ).write(by)
```
 
使用`View->Show Console`打开控制台，粘贴复制的代码，敲击回车运行。待程序右下角提示`success`后，重启ST。
 
再次进入ST后，可以通过菜单`Preferences->Package Control`或者按键`ctrl+shift+p`查找`install package`。输入对应的插件名称，即可安装插件。
 
更多插件，可以通过Package Control中的[search](https://sublime.wbond.net/search)查找。
 
## 配置修改
配置包括Preferences->Settings-Default和Key Bindings-Default。
 
修改配置文件时，以上两个默认文件最好不要修改，自行讲需要设置的参数写入到Settings-User和Key Bindings-User里，它们会自动覆盖Default相同属性。
 
### 备份配置
配置文件的路径，点击Preferences->Browse Packages打开目录，找到User目录，这里的文件就是自己的配置文件，最好备份，方便下次替换。
 
## 插件推荐

### 已安装的插件

```
{
    "in_process_packages":
    [
    ],
    "installed_dependencies":
    [
        "0_package_control_loader",
        "bz2"
    ],
    "installed_packages":
    [
        "AlignTab",
        "All Autocomplete",
        "AutoFileName",
        "BracketHighlighter",
        "CSScomb",
        "DocBlockr",
        "EditorConfig",
        "Emmet",
        "Git",
        "HTML-CSS-JS Prettify",
        "JSHint Gutter",
        "LiveStyle",
        "Markdown Preview",
        "Modific",
        "Package Control",
        "SideBarEnhancements",
        "Sublimerge Pro",
        "Terminal",
        "Theme - Phoenix"
    ]
}
```

### 主题配色和代码配色
配色其实分为主题配色和代码配色。主题配色就是程序的外形设置，代码配色则是打开文件高亮显示的配置。
 
代码配色我是选择的自己备份的主题`Peacock (SL).tmTheme`,放置在了`Packages/User/theme/`目录下，主要是我针对`markdown`语法进行了设置，其他可选择的推荐`Dayle Rees Color Schemes`插件。
 
主题配色我使用的是`Theme-Phoenix`插件，插播一句，编程的字体应该选择等宽类型的，所以Mac下选择的是`Monaco`字体。 

 
安装完了插件，可以在`Perferences->Color Scheme`中查看修改。也可以通过配置文件修改：
```
{
    "caret_style": "phase",
    "color_scheme": "Packages/User/theme/Peacock (SL).tmTheme",
    "default_line_ending": "unix",
    "font_face": "Monaco",
    "font_size": 18.0,
    "highlight_line": true,
    "hot_exit": false,
    "highlight_modified_tabs": true,
    "show_encoding": true,
    "ignored_packages":
    [
        "Vintage"
    ],
    "original_color_scheme": "Packages/User/theme/Peacock (SL).tmTheme",
    "phoenix_color_green": true,
    "phoenix_dirty_bottom_bar_red": true,
    "phoenix_eighties": true,
    "phoenix_highlight_current_tab": true,
    "phoenix_sidebar_tree_large": true,
    "phoenix_solid_current_tab": true,
    "phoenix_tabs_medium": true,
    "rulers":
    [
        80,
        100,
        120
    ],
    "soda_folder_icons": false,
    "tab_size": 4,
    "theme": "Phoenix Dark.sublime-theme",
    "translate_tabs_to_spaces": true,
    "word_separators": "./\\()\"':,.;<>~!@#$%^&*|+=[]{}`~?",
    "word_wrap": true,
    "wrap_width": 0
}
```
这里我列出的是我的全部配置文件，可以看到相关的主题配色、代码配色和字体设置。
 
### ST辅助类
- **SideBarEnhancements**
提升右侧导航栏功能
 
- **Sublimerge Pro**
文件对比功能
 
- **Markdown Preview**
书写markdown格式文本，预览等功能。
 
- **Terminal**
直接在对应文件所在目录打开terminal功能。
 
### 代码显示辅助类
- **BracketHighlighter**
高亮显示匹配括号，会在左侧的行号标识处显示对应的括号位置和范围。
 
- **HTML-CSS-JS Prettify**
格式化代码工具，默认快捷键`ctrl+shift+h`。
 
- **CSScomb**
按照一定规律格式化CSS的属性顺序。
 
### 代码书写辅助类
- **Emmet**
必装插件，辅助书写HTML, CSS。
 
- **AutoFileName**
书写代码时，自动提示补充文件路径。
 
- **DocBlockr**
辅助书写注释。
 
- **JSHint Gutter**
利用`jslint`检测js代码是否规范的插件。
 
- **LiveStyle**
配合对应的chrome插件，可以达到修改文件后，自动刷新页面的效果。但目前对`less`,`sass`之类预编译语言支持不够好。
 
- **AlignTab**
变量竖向对齐工具。

- **All Autocomplete**
代码补全插件。

- **EditorConfig**
代码编码规范。

- **MultiEditUtils**
增强了SublimeText内置的“multi-cursor”和“multi-selection”功能

## 使用技巧
### 快捷键操作
默认的快捷操作，可以查看`Preferences->Key Binding`，或者文档:[Keyboard Shortcuts-Windows/Linux](http://docs.sublimetext.info/en/latest/reference/keyboard_shortcuts_win.html)和[Keyboard Shortcuts-OSX](http://docs.sublimetext.info/en/latest/reference/keyboard_shortcuts_osx.html)。

个人常用的快捷键设置如下：
```
[
    /*============= Emacs Style =============*/
    { "keys": ["ctrl+b"], "command": "move", "args": {"by": "characters", "forward": false} },
    { "keys": ["ctrl+f"], "command": "move", "args": {"by": "characters", "forward": true} },
    { "keys": ["ctrl+p"], "command": "move", "args": {"by": "lines", "forward":
    false} },
    { "keys": ["ctrl+n"], "command": "move", "args": {"by": "lines", "forward":
    true} },
    { "keys": ["ctrl+a"], "command": "move_to", "args": {"to": "bol", "extend": false} },
    { "keys": ["ctrl+e"], "command": "move_to", "args": {"to": "eol", "extend": false} },
    { "keys": ["ctrl+l"], "command": "show_at_center" },
    /*============= End Emacs Style =============*/

    /*============= switch tabs =============*/
    { "keys": ["ctrl+1"], "command": "select_by_index", "args": { "index": 0 } },
    { "keys": ["ctrl+2"], "command": "select_by_index", "args": { "index": 1 } },
    { "keys": ["ctrl+3"], "command": "select_by_index", "args": { "index": 2 } },
    { "keys": ["ctrl+4"], "command": "select_by_index", "args": { "index": 3 } },
    { "keys": ["ctrl+5"], "command": "select_by_index", "args": { "index": 4 } },
    { "keys": ["ctrl+6"], "command": "select_by_index", "args": { "index": 5 } },
    { "keys": ["ctrl+7"], "command": "select_by_index", "args": { "index": 6 } },
    { "keys": ["ctrl+8"], "command": "select_by_index", "args": { "index": 7 } },
    { "keys": ["ctrl+9"], "command": "select_by_index", "args": { "index": 8 } },
    { "keys": ["super+shift+t"], "command": "reopen_last_file" },
    /*============= End switch tabs =============*/

    /*============= Modify Default key-mapping  =============*/
    { "keys": ["super+a"], "command": "select_all" },
    { "keys": ["super+t"], "command": "new_file" },
    { "keys": ["f5"], "command": "open_in_browser" },
    // autocomplate
    { "keys": ["ctrl+/"], "command": "auto_complete" },
    // paste
    { "keys": ["super+v"], "command": "paste_and_indent" },
    { "keys": ["super+shift+v"], "command": "paste" },
    // reindex
    { "keys": ["ctrl+i"], "command": "reindent" },
    // find and goto
    { "keys": ["super+f"], "command": "show_panel", "args": {"panel": "find"} },
    { "keys": ["super+p"], "command": "show_overlay", "args": {"overlay": "goto", "show_files": true} },
    { "keys": ["super+r"], "command": "show_overlay", "args": {"overlay": "goto", "text": "@"} },
    { "keys": ["super+l"], "command": "show_overlay", "args": {"overlay": "goto", "text": ":"} },
    { "keys": ["super+;"], "command": "show_overlay", "args": {"overlay": "goto", "text": "#"} },
    { "keys": ["super+d"], "command": "goto_definition" },
    { "keys": ["super+-"], "command": "jump_back" },
    { "keys": ["super+="], "command": "jump_forward" },
    // keep the shortcut as Windows
    { "keys": ["ctrl+d"], "command": "find_under_expand" },
    { "keys": ["ctrl+g"], "command": "find_all_under" },
    { "keys": ["ctrl+j"], "command": "join_lines" },
    { "keys": ["ctrl+shift+j"], "command": "expand_selection", "args": {"to": "indentation"} },
    { "keys": ["ctrl+shift+k"], "command": "run_macro_file", "args": {"file": "res://Packages/Default/Delete Line.sublime-macro"} },
    /*============= End Modify Default key-mapping  =============*/

    /*============= Plugin =============*/
    // Emmet expand
    {"keys": ["super+e"], "args": {"action": "expand_abbreviation"}, "command": "run_emmet_action", "context": [{"key": "emmet_action_enabled.expand_abbreviation"} ] },
    // js Hint Grunt
    {"keys": ["super+j"], "command": "jshint"},
    // markdown preview
    { "keys": ["super+m"], "command": "markdown_preview", "args": {"target": "browser", "parser":"markdown"} },
    // terminal
    { "keys": ["ctrl+super+t"], "command": "open_terminal" },
    { "keys": ["ctrl+shift+super+t"], "command": "open_terminal_project_folder" }
    /*============= End Plugin =============*/
]
```

其中涉及到了emacs移动光标，多标签切换，以及快速查找等方式。

### snippet
snippet是代码片段，可以方便的自动补全。创建方式通过`Tools->New Snippet`完成。

默认的文件如下:
```
<snippet>
    <content><![CDATA[
Hello, ${1:this} is a ${2:snippet}.
]]></content>
    <!-- Optional: Set a tabTrigger to define how to trigger the snippet -->
    <!-- <tabTrigger>hello</tabTrigger> -->
    <!-- Optional: Set a scope to limit where the snippet will trigger -->
    <!-- <scope>source.python</scope> -->
</snippet>
```
代码段写在`CDATA[]`中，`${}`为占位字符。 

`tabTrigger`为自动补全需要的字符，`scope`设置的是文件格式。

创建完成之后，个人建议保存在`User->snippet`目录下，`snippet`需要自行创建，方便管理。

### build命令和Macro命令
这些命令的使用请参考文档->[Reference](http://docs.sublimetext.info/en/latest/reference/reference.html)。


## 参考文档
- [sublimeText官网](http://www.sublimetext.com/)
- [非官方手册](http://docs.sublimetext.info/en/latest)
- [Package Control](https://sublime.wbond.net/installation#Simple)
- [推荐！Sublime Text 最佳插件列表](http://blog.jobbole.com/79326/)
- [Gif多图：我常用的 16 个 Sublime Text 快捷键](http://blog.jobbole.com/82527/)