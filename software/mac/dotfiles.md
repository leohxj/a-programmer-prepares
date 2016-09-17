# dotfiles
dotfiles就是软件的配置文件。一般用于软件设置，可以通过备份dotfiles的方式，同步软件设置。

## 同步原理
主要是应用了`ln`软连接的功能，命名格式如下:

```
ln [参数][源文件或目录][目标文件或目录]
```

在我们备份dotfiles中常用的参数有ln -s软链接，s是代号symbolic的意思，所谓软链接，她只会在你选定的位置上生成一个镜像，而不会占用磁盘空间，而如果使用ln不带参数的话，则就是硬链接，会在选定的位置上生成一个和源文件大小相同的文件，占用磁盘空间。注意在创建软连接之前，保证目标文件是不存在的。

## 如何同步
可以使用git/dropbox管理dotfiles。~~之前使用过dropbox，受限于国内网速问题，多台设备常常会出现版本冲突。以后索性使用git管理吧，创建一个dotfiles目录，将所有的文件放置到此目录下。~~

还是按照需要同步的频率决定使用什么方式管理dotfile吧，dropbox里面还是放置一些常用的配置文件，git还是用来管理所有配置项。

```
cd ~
mv .zshrc  ~/Users/l/dotfiles/zshrc
ln -s ~/Users/l/dotfiles/zshrc .zshrc
```

这里举例的是zsh的配置文件，其他原理同此。最后把git push到服务器端既可。

## 如何恢复
首先更新下对应的dotfiles目录，然后删除掉恢复的配置文件，再次使用软连接恢复。

```
git clone xxxx
rm -rf .zshrc
ln -s dotfiles/zshrc .zshrc
```

关于恢复，还可以通过脚本文件实现自动化。以后补充。

## 不同
- zsh配置文件
- SublimeText3配置文件
- dash

## 参考资料
- [dotfiles](https://github.com/mathiasbynens/dotfiles)
- [dotfiles.github.io](http://dotfiles.github.io/)
- [mackup](https://github.com/lra/mackup)
