# EditorConfig
[EditorConfig](http://editorconfig.org/):

    EditorConfig helps developers define and maintain consistent coding styles between different editors and IDEs. The EditorConfig project consists of a file format for defining coding styles and a collection of text editor plugins that enable editors to read the file format and adhere to defined styles. EditorConfig files are easily readable and they work nicely with version control systems.

简单的说，就是一个代码缩减格式化辅助工具，需要编辑器或者IDE插件支持。

## 配置示例

```
# EditorConfig helps developers define and maintain consistent
# coding styles between different editors and IDEs
# editorconfig.org

root = true


[*]

# change these settings to your own preference
indent_style = space
indent_size = 4

# we recommend you to keep these unchanged
end_of_line = lf
charset = utf-8
trim_trailing_whitespace = true
insert_final_newline = true

[*.md]
trim_trailing_whitespace = false

[{package,bower}.json]
indent_style = space
indent_size = 4

```


## 参考资料
- [EditorConfig](http://editorconfig.org/)
- [SublimeText Plug: editorconfig](https://github.com/sindresorhus/editorconfig-sublime)