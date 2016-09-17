# Git
git是一种分布式版本控制系统，是目前项目管理使用较多的一种工具。

## 下载安装
### windows
[官网](http://www.git-scm.com/)，下载安装包，直接运行之后命令行就可以运行了。

### Mac
如果是安装了xcode的话，会自带一个版本的git。

如果想要安装新版本的git，推荐使用[**Homebrew**](http://brew.sh/): mac下的apt-get。   
安装brew，它下载的命令是存在放`/usr/local/bin`中的，所以要想正常工作，还需要在PATH中添加这个路径，在命名行下输入:`echo export PATH='/usr/local/bin:$PATH' >> ~/.bash_profile`。

### Linux
Linux下可以使用`apt-get install git`来安装。

## 学习教程
- [最好的中文教程](http://www.liaoxuefeng.com/wiki/0013739516305929606dd18361248578c67b8067c8c017b000)
- [Git Magic](http://www-cs-students.stanford.edu/~blynn/gitmagic/intl/zh_cn/): 网上较火的一套教程。
- [GotGithub](https://github.com/gotgit/gotgithub): 一本中文的介绍github使用的书。
- [Git Tutorials](https://www.atlassian.com/git?atl_source=cac-bitbucket-1&atl_medium=ace&atl_campaign=ACE-158-Stash-GIT-on-Bitbucket-CAC_git): bitbucket的教程。
- [Try Git](http://try.github.com/)： codeschool教程。
- [Git Immersion](http://gitimmersion.com/index.html): 答题的形式学习git.
- [Learn Version Control with Git](http://www.git-tower.com/learn/)
- [githug](https://github.com/Gazler/githug): Git your game on!
- [git-game](https://github.com/hgarc014/git-game): terminal game to test git skills.
- [Learn Git Branching](http://pcottle.github.io/learnGitBranching/): 形象直观的图形化练习网站。

## 使用技巧
### 资料
- [GitHub秘籍](https://github.com/tiimgreen/github-cheat-sheet/blob/master/README.zh-cn.md)
- [Set up Git](https://confluence.atlassian.com/display/BITBUCKET/Set+up+Git): bitbucket教程。
- [Github Help](https://help.github.com/)
- [使用git和github进行协同开发流程](http://livoras.com/post/28)

### 配置文件
一般都在`/user`下，window对应的目录是`C:\Users\username`，mac和linux对于的就是用户主目录`/Users/username`。配置文件名称为`.gitconfig`。

通常我们使用git的时候最先会去配置username和email:

```
git config --global user.name "FIRST_NAME LAST_NAME"
git config --global user.email "MY_NAME@example.com"
```

一般而言，我会使用`git add . -> git commit -m "xxxx" -> git push`的方式提交，第一次git操作的时候，git会给我如下的提示：

```
warning: push.default is unset; its implicit value has changed in
Git 2.0 from 'matching' to 'simple'. To squelch this message
and maintain the traditional behavior, use:

  git config --global push.default matching

To squelch this message and adopt the new behavior now, use:

  git config --global push.default simple

When push.default is set to 'matching', git will push local branches
to the remote branches that already exist with the same name.

Since Git 2.0, Git defaults to the more conservative 'simple'
behavior, which only pushes the current branch to the corresponding
remote branch that 'git pull' uses to update the current branch.

See 'git help config' and search for 'push.default' for further information.
(the 'simple' mode was introduced in Git 1.7.11. Use the similar mode
'current' instead of 'simple' if you sometimes use older versions of Git)
```

其实就是告诉我要设置下push.default,执行`git config --global push.default simple`即可。

### 存储密码
#### https协议
如果使用的是https协议访问git仓库，与服务器端同步的时候每一次都会提示输入密码。解决这个问题的方式就是能让密码保存起来。

在windows下，我使用的是[git-credential-winstore](http://gitcredentialstore.codeplex.com/)。下载安装即可使用。

在Mac下，我使用的是[git-credential-osxkeychain](http://github-media-downloads.s3.amazonaws.com/osx/git-credential-osxkeychain)。首先在终端中检测是否已经有git-credential-osxkeychain，`git credential-osxkeychain`。提示`usage: git credential-osxkeychain <get|store|erase>`, 代表有。

如果没有，下载这个工具，执行：

```
Move the file to the /usr/local/bin directory.
$ sudo mv git-credential-osxkeychain /usr/local/bin/

Make the file an executable:
$ chmod u+x /usr/local/bin/git-credential-osxkeychain 
Configure git to use the helper.

$ git config --global credential.helper osxkeychain
# Set git to use the osxkeychain credential helper
```

如果存在的话，直接执行`git config --global credential.helper osxkeychain`。


在Linux下，执行`git config --global credential.helper store`。

-----

操作完之后，检查下`.gitconfig`文件，看是否添加了`[credential]`字段。

如果需要取消设置，执行`git config --unset --global credential.helper`。

#### ssh协议
需要设置ssh的私钥和公钥。

### 切换协议
查看当前remote: `git remote -v`。

更新remote: `git remote set-url origin https://git.oschina.net/username/YourRepo`