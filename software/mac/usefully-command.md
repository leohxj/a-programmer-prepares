# 常用终端命令
介绍一些终端下常用的命令。首先说明一下，本人的环境为：iTerm2+zsh。

## 常用的
先插一句，说一个好玩的，可以查看最近经常使用的命令，在终端执行:
```
history | awk '{CMD[$2]++;count++;} END { for (a in CMD )print CMD[ a ]" " CMD[ a ]/count*100 "% " a }' | grep -v "./" | column -c3 -s " " -t |sort -nr | nl | head -n10
```

- clear: 清除屏幕。
- pwd: 查看当前路径。
- cd: 进入目录，常常配合一些字符使用。比如：
    - `..`: 返回上级目录。
    - `~`: 返回用户主目录。
    - `-`: 返回上次操作目录。
    - `/`: 返回系统根目录。
- ls: 列出目录信息。
- mkdir: 创建目录。
- touch: 创建文件。
- cp: 拷贝文件。
- mv: 移动文件，或者重命名文件。
- rm：删除文件。
- cat: 查看文件内容。
- grep: 查找文本信息。
- man: 手册命名，查看各个命名的帮助。


## 系统操作
- open: 可以打开文件，目录和程序。通过man open查看具体内容，我常用来在终端下打开Finder， 比如`open .`。Windows下对应的使用`explorer`命令。或者打开Applications下的程序，使用`open "/Applications/Sublime Text.app" test.md`。



