# node
node由于各个版本特性不同，很多项目需要使用不同版本的node，所以推荐使用[nvm(Node Version Manager)](https://github.com/creationix/nvm)进行管理。


## Mac下安装
### brew方式
如果机器没有安装过node，那么首先`brew install nvm`安装nvm。

其次需要在shell的配置文件(~/.bashrc, ~/.profile, or ~/.zshrc)中添加如下内容：

```
# For NVM
export NVM_DIR=~/.nvm
source $(brew --prefix nvm)/nvm.sh
```

注意配置的顺序，以防开启新终端，node出现找不到的情况。

重启终端，命令行下即可使用nvm，使用`nvm install <version>`进行对应的node版本安装，写这篇文章时，我使用的是`nvm install 0.10`，安装的版本是v0.10.32。使用`nvm use <version>`使用， 再通过`nvm alias default <version>`确保有默认版本。最后使用`nvm ls`查看。


### brew方式补充
如果之前通过'brew install node'方式安装过node，那么需要先删除系统中存在的node：

```
brew remove --force node
sudo rm -r /usr/local/lib/node_modules

brew prune
sudo rm -r /usr/local/include/node

# 检查brew是否正常
brew doctor
```

### nvm安装方式
`curl https://raw.githubusercontent.com/creationix/nvm/v0.17.2/install.sh | bash`进行安装，安装完成后，运行`nvm`测试命令是否正确，如果不正确，参考官网提供的说明，也是需要在shell的配置文件中加入相应的配置。

如果安装正确，同样使用`nvm install <version>`安装对应版本node，使用`nvm use <version>`使用， 再通过`nvm alias default <version>`确保有默认版本。最后使用`nvm ls`查看。


设置完nvm之后，node的路径其实是`/Users/#{username}/.nvm/#{nodeVersion}/bin/node`, 一些sublimeText插件默认的路径是`/usr/local/bin/node`。个人建议创建一个软连接:

```
ln -s /Users/#{username}/.nvm/#{nodeVersion}/bin/node /usr/local/bin/node
```

## Windows下安装
window下我之前都是直接node官网下载mis文件安装。后续尝试使用类nvm工具安装管理。

### nvm-windows方式
睡觉前看了一眼，简直不能再便捷了！！！项目地址: [nvm-windows](https://github.com/coreybutler/nvm-windows)

下载安装包，不管之前系统安装过node与否，安装过会接管。就能直接使用nvm命令。

## npm的管理
通过nvm安装的node，每个版本都有一个对应的npm。每次切换，可以使用`npm update -g`进行一次升级，安装程序的话，需要使用sudo权限。

有一点疑问，如何同步之前安装的所有-g模块。。？？

## 参考资料
- [node包教不包会](https://github.com/alsotang/node-lessons)