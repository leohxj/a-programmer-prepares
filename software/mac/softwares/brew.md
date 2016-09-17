# brew

## homebrew
[homebrew](https://github.com/Homebrew/homebrew)，是mac下类似apt-get的软件管理工具。

通常情况下brew安装的软件都会在`brewprefix`返回的目录中，不会在额外创建文件。

### 安装
没啥说的，直接安装官方提供的方式，终端下运行：`ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"`

### 使用
安装完brew之后，执行`brew update`和`brew doctor`，然后按照提示稍微设置下，需要我们将`/usr/local/bin`添加到PATH路径的最前面，保证系统优先调用到的是brew下载的。在命名行下输入:`echo export PATH='/usr/local/bin:$PATH' >> ~/.bash_profile`。

一般来说，我会用brew安装git, nvm, zsh。V2EX有人统计了下常用的安装软件:

```
wget=26
pkg-config=17
automake=17
autoconf=17
readline=15
git=14
gettext=14
libtool=14
xz=14
pcre=13
imagemagick=12
zsh=12
jpeg=12
gdbm=12
openssl=11
mongodb=11
cmake=11
coreutils=11
libevent=11
tree=11
freetype=11
sqlite=11
libpng=10
macvim=10
mtr=10
libyaml=10
mysql=9
node=9
mercurial=9
tig=9
nginx=9
gnutls=8
redis=8
libgpg-error=8
ack=8
gmp=8
tmux=8
libtiff=8
glib=7
go=7
libksba=7
nettle=7
p11-kit=7
unrar=7
phantomjs=7
python=7
libffi=7
gawk=7
libtasn1=7
lua=7
apple-gcc42=7
libxslt=7
dos2unix=6
fontconfig=6
python3=6
htop-osx=6
pixman=6
ctags=6
gd=5
intltool=5
git-extras=5
swig=5
curl=5
neon=5
jasper=5
curl-ca-bundle=5
icu4c=5
p7zip=5
postgresql=5
zlib=5
libxml2=5
```

### 删除
这个说一下吧，因为公司的电脑是别人之前使用的，暂时有些资料需要保存，我无法删除，我新建了个用户继续使用。

之前的brew可能是其他用户安装的，导致我的新用户能使用brew命令，但是无法安装，更新（应该是权限读取的问题）。所以我想卸载brew重新安装。官方提供的一个脚本好像是几年前的，[uninstall_homebrew.sh](https://gist.github.com/mxcl/1173223)。而我找到一个说明，感觉比较简单明了：


**Uninstall**

WARNING: Before copying and pasting these commands on your shell, make sure the first one (`brew –prefix`) returns the path where homebrew was installed properly. If not, you might ending up removing stuff from your computer you did not intend to remove.

```
cd `brew --prefix`
rm -rf Cellar
brew prune
rm -rf Library .git .gitignore bin/brew README.md share/man/man1/brew
rm -rf ~/Library/Caches/Homebrew
http://superuser.com/questions/203707/how-to-uninstall-homebrew-osx-packet-> manager
```

**Reinstall**

```
ruby -e "$(curl -fsSL https://raw.github.com/mxcl/homebrew/go)"
https://github.com/mxcl/homebrew/wiki/Installation
```

也许第一次删除安装还是会出问题，那就结合官方提供的shell里的路径，全部删除，再次重启。

#### 特别说明
我这里删除再安装之后，可以通过`brew install`安装软件，比如git。但是执行`brew doctor`时，会报告`link`的错误: `You have unlinked kegs in your Cellar`，执行`brew link git`之后，会提示`could not symlink opt is not writable`。

此问题是`/usr/local`目录缺少权限，执行`sudo chmod -R g+w /usr/local`，再次`brew link git`即可。

## homebrew-cask
[cask](http://caskroom.io/), 它是brew的一个扩展，提供命令行下安装软件的功能。它所安装的所有软件都在`/opt/homebrew-cask/Caskroom`目录下，自动完成了软连接到`Application`。


### 安装
`brew install caskroom/cask/brew-cask`，一键安装。

如果已经安装的用户，可以升级到最近版本：

```
brew update && brew upgrade brew-cask && brew cleanup && brew cask cleanup
```

还有要说明的一点：默认通过brew cask安装的软件，是软连接到`~/Applications`目录下，这是可以通过设置修改的，具体的使用可以通过`man brew-cask`查看。

我是直接`echo export PATH='/usr/local/bin:$PATH' >> ~/.zshrc`，写入到配置文件中。

### 运行
第一次安装过后，执行`brew cask --help`查看下说明（其实只要是第一次运行），需要你提供root权限，方便cask软连接到Application中。

安装其他软件的话，可以先使用`brew cask search <name>`查看是否有匹配的。再使用`brew cask install <name>`进行安装。成功之后，就可以直接在Application中找到刚刚安装的软件。

## 关联Alfred2
安装完应用之后，如果你是Alfred2用户，还需要设置一下link，使得Alfred可以搜索通过brew cask安装的应用，操作方法是:

```
# 查看状态
brew cask alfred status
# 设置连接
brew cask alfred link
```

## 使用brew cask安装的软件
- Dropbox
- QQ
- TextExpander

## LaunchRocket
LaunchRocket是一个管理brew安装的service的工具，安装之后可以看所有的service的运行状态。

## 参考资料
- [homebrew-FAQ](https://github.com/Homebrew/homebrew/wiki/FAQ)
- [使用brew cask来安装Mac应用](http://blog.devtang.com/blog/2014/02/26/the-introduction-of-homebrew-and-brewcask/)
- [LaunchRocket](https://github.com/jimbojsb/launchrocket)