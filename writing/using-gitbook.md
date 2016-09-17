# 使用gitbook
之前整理的习惯是使用Evernote，其实主要做的是收录（输入）的功能，东西多了，就难以消化掉（处理），以至于没有总结（输出）。Markdown格式是我很喜欢的一种书写格式，我觉得特别适合程序员，配合gitbook，就能达到写书的效果。

## Version 1.x.x
gitbook刚推出的时候，我就在使用，这个时候的版本都是1.x系列。安装方式是:

```
npm install -g gitbook
```

目录结构上，只要有`README.md`和`SUMMARY.md`即可。

使用方式:

```
gitbook build
```

即可完成编译。


## Version 2.x.x
最近再看gitbook的时候，发现它已经推出了2.x系列，安装方式也变化了。需要先删除之前1.x系列版本，再安装:

```
npm install -g gitbook-cli
```

## editor
关于editor，其实有两种选择:

- gitbook站点上edit，线上编辑
- 下载editor，本地编辑

### 线上编辑
先说说线上编辑，毕竟我刚刚使用了下，就是web版本的应用。有一点特别的好处是可以绑定github repo，编辑直接保存在github上。省去了本地编辑，再push的过程。

但是我也发现了一点点不方便的地方，就是无法上传整个目录文件，必须一个一个上传，且无法设置目录。。。很蛋疼。

### 本地编辑
就是一个本地软件，可以本地编辑，应该是通过图形化性质整合命令行，包含了build功能。1.x版本刚推出的时候，在window平台下体验过，会有再次打开丢失项目的情况，每次都要重新打开项目，很麻烦。但是新版应该有所改善。

本地编辑还有另外一个方式，就是我常用的手段：使用Sublime Text进行编辑，结合Markdown插件，产生预览。最后通过git提交到远程。


## 目录结构
官方的格式说明，[Format](http://help.gitbook.com/format/README.html)。必须的文件是`README.md`和`SUMMARY.md`。

## 使用方法
### init
`gitbook init`,根据`SUMMARY.md`生成目录。

### build
`gitbook build`，生成`_books`目录。

### serve
`gitbook serve`, 开启本地预览。

## 参考资料
- [Gitbook主页](https://www.gitbook.com)
- [Gitbook Help](http://help.gitbook.com/)
- [Version 2.0说明](https://github.com/GitbookIO/gitbook/pull/562)
- [github: GitbookIO](https://github.com/GitbookIO)
- [gitbook editor](https://github.com/GitbookIO/editor)