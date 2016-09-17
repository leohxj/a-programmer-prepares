# 开发环境
在PC下，我一般都会安装好各种开发语言，设置好命令行工具，搭配好开发的编辑器或IDE。


## 开发语言
mac系统上自带了gcc, g++, ruby, python的环境。Objective-C的开发当安装上xCode之后也配置好了。

我一般还会安装上nodejs, git ,java。

安装的方式我会选择brew，类似linux系统下的apt-get。但有些命令比如git在xCode安装的时候就已经绑定了，这时需要我们将`/usr/local/bin`添加到PATH路径的最前面，保证系统优先调用到的是brew下载的。在命名行下输入:`echo export PATH='/usr/local/bin:$PATH' >> ~/.bash_profile`。

这一步也可以执行`brew doctor`来检测。

## 终端
### Finder中打开
通常Finder会搭配上XtraFinder插件，可以在目录中直接打开终端，且可指定终端为iTerm2。

### iTerm2
在我还没有使用mac的时候，我就常常看见别人推荐iTerm 2这个强大的终端软件，用来替代原生的终端。

目前我设置过的就是新建窗口的大小，默认是80x25我觉得太小了，改为了120x30。

下一步打算修改一下配色，以及设置一下全局开启的快捷键。

### zsh
shell是终端与系统交互的一种语言，默认的是bash，但是最好的是zsh。安装方式我使用:`brew install zsh`。

替换bash的方式：`chsh -s /bin/zsh`。关闭终端，再次打开即为zsh。

注意：之前我们使用bash，我们为了使用brew安装的软件，修改了`~/.bash_prorile`文件，新的zsh自己也有配置文件，是`~/.zshrc`，需要将配置拷贝到`~/.zshrc`中。

或者在安装完oh-my-zsh后，执行`echo export PATH='/usr/local/bin:$PATH' >> ~/.zshrc`。

### oh-my-zsh
由于zsh的配置是很复杂的，所以有这个一个开源项目[oh-my-zsh](https://github.com/robbyrussell/oh-my-zsh?source=c)，帮助我们简化zsh的配置。

官网有自动安装的方法，我选择的是: `curl -L http://install.ohmyz.sh | sh`。

安装完成后，重启终端就能看到界面的变化了。zsh的配置文件是`~/.zshrc`，配色对应的是`ZSH_THEME`.

### oh-my-zsh插件
oh-my-zsh的强大之处还在于提供了完善的插件系统。相关的文件存储在`~/.oh-my-zsh/plugins`中，默认提供了100多种。。。

默认提供的插件是git,需要添加的话，修改`~/.zshrc`中`plugins=(git autojump)`即可。

#### 自动跳转
[z](https://github.com/rupa/z)和[autojump](https://github.com/joelthelion/autojump)。是两个可以实现自动跳转的插件，都是可以通过brew下载的。

我目前使用的是`autojump`，通过`brew install autojump`下载，并且在`~/.zshrc`中修改`plugins=(git autojump)`。重启终端。

使用就可以使用j来代替cd命令了，并可以添加自定义目录，具体使用说明参考autojump的文档或者`autojump --help`。

## 参考资料
- [分享了下自己的终端环境，iTerm2,zsh,z,tmux。](http://www.v2ex.com/t/77918)
- [终极 Shell——ZSH](http://zhuanlan.zhihu.com/mactalk/19556676)




