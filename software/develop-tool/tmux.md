# tmux
tmux是指通过一个终端登录远程主机并运行后，在其中可以开启多个控制台而的终端复用软件。使用了tmux，你就可以在一个终端中同时运行多个会话，只需开启一个终端。

## 为什么使用tmux
如果只是分隔屏幕，配色的变化，其实客户端item2以及screen就已经很好了。那我们为什么要使用tmux呢？

为什么使用tmux： 

- 保持会话： 断开ssh或关闭电脑，你的ssh可以重新连接，能够保持你的工作环境连续性。前提实在服务器端装上tumx

使用tmux会话的分离与连接就可以轻松解决以上问题，分离（detach）可以使终端会话在后台运行，连接（attach）可以重新打开在后台运行的会话，也可以多个终端连接同一会话。

## 安装
### Mac
`brew install tmux`即可

### Linux
`yum install tmux`类似命令即可

### Windows
Windows下可以使用cygwin来安装 cygwin，cygwin是图形安装界面，请确保在 Select Packages 界面出现时，选中 tmux 即可。

## tmux的基本概念
启动之后，可以看到命令行最底部多了一条绿色的状态条，上面显示了一些信息，比如计算机名和时间等。

### Session(会话)
一组窗口的集合，通常用来概括同一个任务。session可以有自己的名字便于任务之间的切换。

### Window(窗口)
单个可见窗口。Windows有自己的编号，也可以认为和ITerm2中的Tab类似。

当你新建一个会话的时候，tmux 已经自动给你在新会话中自动创建了一个窗口(Window)，窗口的编号从`0`开始，名称则默认为当前工作目录或者当前运行的程序，都显示在下方的状态条中。如下图所示，我将工作目录切换到了`~/Documents`，窗口`0`的名称也随之变换。

### Pane(窗格)
tmux 下可以有多个会话，会话下又可以有多个窗口，那么同样，窗口下还可以有多个窗格, 一个窗口可以切分成多个窗格，主要的切分方法有两种，垂直切分和水平切分。

## tmux的基本操作
前置操作(`Prefix-Command`)，所有下面介绍的快捷键，都必须以前置操作开始。tmux默认的前置操作是`CTRL+b`。

### 会话相关
- 新建会话(create): `tmux new-session -s <会话名称>` or `tmux new -s <会话名称>`
- 分离会话(detach): `prefix d`,退出tmux但是不关闭掉进程，方便下次进入
- 连接会话(attach): `tmux attach -t <目标会话名>` or `tmux a -t <目标会话名>`, 被分离的会话，还可以重新连接上
- `tmux ls`: 列出所有的会话
- `prefix $`: 重命名当前会话

### 窗口相关
- `tmux new -n <窗口名>`: 创建会话的时候附上 `-n` 参数，来给窗口制定一个名称
- 新建窗口: `prefix c`
- 上一个窗口（previous）: `prefix p`
- 下一个窗口（next）: `prefix n`
- 切换到上一个活动的窗口: `prefix space`
- 使用窗口号切换: `prefix 窗口号`
- 窗口列表: `prefix w`
- 关闭一个窗口: `prefix &`
- 更改窗口名称: `prefix ,`

## 窗格相关
- 查看所有窗格的编号: `prefix q`
- 垂直切分（把窗口垂直切分成左右两等分）：`prefix %` 
- 水平切分（把窗口水平切分成上下两等分）：`prefix "` 
- 窗格切换: `prefix o`
- 按制定方向切换窗格: `prefix 方向键`
- 更改窗格布局: `prefix 空格`, 可以在这五个默认的窗格布局之中轮流切换:
    - 水平平分（even-horizontal）
    - 垂直平分（even-vertical）
    - 主窗格最大化，其他窗格水平平分（main-horizontal）
    - 主窗格最大化，其他窗格垂直平分（main-vertical）
    - 平铺，窗格均等分（tiled）

## 参考资料
- [Tmux - Linux从业者必备利器](http://cenalulu.github.io/linux/tmux/)
- [图灵: tmux入门](http://www.ituring.com.cn/minibook/10707)
