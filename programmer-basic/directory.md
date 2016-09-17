# 目录结构
不管大型还是小型项目，清晰的目录结构是开发过程的好的开始。以我常用的web项目为例，搭建一下目录结构.

## 总览
```bash
├── src
│   ├── js
│   │   ├── main.js
│   │   ├── plugins.js
│   │   └── vendor
│   │       └── modernizr-2.8.3.min.js
│   ├── css
│   │   └── main.css
│   ├── img
│   ├── favicon.ico
│   ├── humans.txt
│   ├── index.html
│   ├── 404.html
│   ├── apple-touch-icon.png
│   ├── browserconfig.xml
│   ├── crossdomain.xml
│   ├── robots.txt
│   ├── tile-wide.png
│   └── tile.png
├── test
│   ├── file_content.js
│   └── file_existence.js
├── dist
│   ├── 404.html
│   ├── LICENSE.txt
│   ├── apple-touch-icon.png
│   ├── browserconfig.xml
│   ├── crossdomain.xml
│   ├── css
│   │   ├── main.css
│   │   └── normalize.css
│   ├── favicon.ico
│   ├── humans.txt
│   ├── img
│   ├── index.html
│   ├── js
│   │   ├── main.js
│   │   ├── plugins.js
│   │   └── vendor
│   │       ├── jquery-1.11.2.min.js
│   │       └── modernizr-2.8.3.min.js
│   ├── robots.txt
│   ├── tile-wide.png
│   └── tile.png
├── CHANGELOG.md
├── CONTRIBUTING.md
├── LICENSE.txt
├── README.md
├── gulpfile.js
├── package.json
```

目录结构清晰是首要目标，至于命名只要能达到表意的目的即可。

## src
此目录专注于开发，存放的都是源文件，不需要压缩合并。目录下主要分为：

- css(styles): 样式文件
- js(scripts): 脚本文件
- img(images): 图片素材
- font(fonts): 存放字体
- 其他: 按照分类不同划分目录

文件名上面，简写的话都使用单数形式，全称的话使用复数形式。

## dist
此目录为编译生成目录，用于部署环境，目录结构和src保持一致。

## test
此目录为测试目录，存放和项目测试相关的文件。

## doc
如果存在文档说明，放置在此目录下。

## 其他根目录文件
根目录下的其他文件，一般还有:

- .editorconfig: 代码样式统一格式文件
- .jscsrc: 
- .travis.yml:
- .jshintrc: jshint配置文件
- csscomb.json: csscomb配置文件
- .gitignore: git忽略文件
- .gitattributes: git属性文件
- .bowerrc
- bower.json
- package.json
- gruntfile.js/gulpfile.js

## 参考资料
- [Baidu EFE team](https://github.com/ecomfe)
- [Baidu EFE team: spec](https://github.com/ecomfe/spec)
- [HTML5-boilerplate](https://github.com/h5bp/html5-boilerplate)