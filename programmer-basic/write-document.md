# 书写文档
一个程序员，最基本的是需要写代码，代码之中其实就包含了注释。如果是一个系统或者库文件，其实还需要书写文档以配合。本文就交大家如何书写文档。

## github如何管理文档
讨论一下我们如何使用 [Github Page](https://pages.github.com/) 服务运行 [Github 帮助文档](https://help.github.com/) （目前每月有上百万的访问量）的。

## 以前的流程
- 用于托管维护网站、管理网站所用资源和文档搜索增强的 Rails 应用程序
- 用户托管由一大堆 Markdown 文件组成的网站具体内容

我们正常的撰写流程可能是这个样子的:
- 当有新特征开发出来的时候文档团队首先编写好文档内容
- 创建一个新的 issue 去追踪这个特征
- 当文档更新完毕一切就绪之后，我们会发起一个 pull request 去迭代更新文档内容。
- PR 发起成功后，我们会使用 @ 方式提醒团队（比如 @github/docs ）并会让队友们审查一下我们的内容。
- 当这个特征开发完毕已经上线的时候，我们会合并之前创建的 PR。 使用 webhook 能够帮助我们在 内容仓库 快速激活我们部署的 Rails应用程序。webhook 承担了负责更新数据库的任务。


## 新的流程
当 Jekyll 2.0 发布的时候，我们看到了曙光，是时候该把我们这套该死的流程换成纯静态站了！特别是新增加的 Collections 文档类型能让你定义你需要的文件结构。另外，Jekyll 2.0 还增加了 Sass 和 CoffeeScript 的支持，这将使得编写前端代码变的更为简单便捷。



## 参考资料
- [Github 是如何用 Github 撰写 Github 文档的](https://segmentfault.com/a/1190000002473246)
- [markdown + git 最适合程序员的wiki系统](http://examplecode.github.io/tools/2014/09/26/install-gollum-in-mac-109/)
- [gollum](https://github.com/gollum/gollum): github的文档系统。
