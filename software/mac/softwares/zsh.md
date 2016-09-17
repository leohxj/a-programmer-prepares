# zsh
zsh是shell语言类型，兼容bash，提供强大的命令行功能，比如tab补全，自动纠错功能等。缺点就是配置太麻烦，好在有一个叫做`oh-my-zsh`的开源项目，很好的弥补了这一缺陷，只需要修修改改配置文件，就能很顺手。


## 安装zsh
安装方式我使用:`brew install zsh`。

替换bash的方式：`chsh -s /bin/zsh`。关闭终端，再次打开即为zsh。

注意：之前我们使用bash，我们为了使用brew安装的软件，修改了`~/.bash_prorile`文件，新的zsh自己也有配置文件，是`~/.zshrc`，需要将配置拷贝到`~/.zshrc`中。

或者在安装完oh-my-zsh后，执行`echo export PATH='/usr/local/bin:$PATH' >> ~/.zshrc`。


### oh-my-zsh
由于zsh的配置是很复杂的，所以有这个一个开源项目[oh-my-zsh](https://github.com/robbyrussell/oh-my-zsh?source=c)，帮助我们简化zsh的配置。

官网有自动安装的方法，我选择的是: `curl -L http://install.ohmyz.sh | sh`。

安装完成后，重启终端就能看到界面的变化了。zsh的配置文件是`~/.zshrc`，配色对应的是`ZSH_THEME`.

### zshrc
zshrc是zsh的配置文件，我会在此添加一些alias设置。比如:
```
alias st='open -a "Sublime Text"'
```

### oh-my-zsh插件
oh-my-zsh的强大之处还在于提供了完善的插件系统。相关的文件存储在`~/.oh-my-zsh/plugins`中，默认提供了100多种。。。

默认提供的插件是git,需要添加的话，修改`~/.zshrc`中`plugins=(git autojump)`即可。

#### 自动跳转
[z](https://github.com/rupa/z)和[autojump](https://github.com/joelthelion/autojump)。是两个可以实现自动跳转的插件，都是可以通过brew下载的。

我目前使用的是`autojump`，通过`brew install autojump`下载，并且在`~/.zshrc`中修改`plugins=(git autojump)`。重启终端。

使用就可以使用j来代替cd命令了，并可以添加自定义目录，具体使用说明参考autojump的文档或者`autojump --help`。

#### fasd
[fasd](https://github.com/clvv/fasd), 功能上和z, autojump差不多，功能和速度上更优。它会按照访问的频率记录下文件，帮助用户快速访问。

安装还是通过brew: `brew install fasd`，安装之后，我安装官网的步骤，执行了:`eval "$(fasd --init auto)"`, 且在zshrc中开启对应的配置：`plugins=(git fasd)`, 重启终端即可使用。

asd comes with some useful aliases by default:

```
alias a='fasd -a'        # any
alias s='fasd -si'       # show / search / select
alias d='fasd -d'        # directory
alias f='fasd -f'        # file
alias sd='fasd -sid'     # interactive directory selection
alias sf='fasd -sif'     # interactive file selection
alias z='fasd_cd -d'     # cd, same functionality as j in autojump
alias zz='fasd_cd -d -i' # cd with interactive selection
```

Example:

```
f foo           # list frecent files matching foo
a foo bar       # list frecent files and directories matching foo and bar
f js$           # list frecent files that ends in js
f -e vim foo    # run vim on the most frecent file matching foo
mplayer `f bar` # run mplayer on the most frecent file matching bar
z foo           # cd into the most frecent directory matching foo
open `sf pdf`   # interactively select a file matching pdf and launch `open`
```


## 参考资料
- [分享了下自己的终端环境，iTerm2,zsh,z,tmux。](http://www.v2ex.com/t/77918)
- [终极 Shell——ZSH](http://zhuanlan.zhihu.com/mactalk/19556676)