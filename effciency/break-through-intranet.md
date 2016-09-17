# 突破内网
有的公司网络环境是受限的，上外网是需要通过代理的，并且对一些娱乐性质的网站进行了屏蔽。我们的目标就是要消除这个现象！

## 准备条件
- 电脑一台
- 一个可以上外网的公司代理
- goagent/shadowsocks，并且有账号
- proxifier: 控制网络请求
- SwitchOmega: chrome的插件

## 实现原理
普通的科学上网上一节已经介绍过了，一般能直连外网的情况下都适用，但是在需要代理上网的环境下，就需要借助其他软件了。

普通环境下上网的过程是: 请求->goagent/shadowsocks->访问。

但是内网代理环境下，所有需要访问外网的请求必须先经过代理。由于shadowsocks/goagent没有设置代理的选项(其实goagent有，但是不稳定)，那么我们就需要借助proxifier类似的工具，先设置goagent/shadowsocks走代理访问外部，再将其他网络请求走goagent/shadowsocks创建的本地代理。这样我们就实现了穿越http代理。

关于这个穿越http代理，我说一下我的理解：
    就是我们通过代理和外界进行了沟通，形成了一个隧道。我们将真实的请求通过这个隧道传递/接受,而代理只看到隧道有流量，却不知道里面具体是什么。

## 科学上网
科学上网目前首选的工具是shadowsocks，它可以创建一个本地的1080端口的socks5的代理，如果设置了允许局域网访问，还会在本地创建一个8123端口的http代理。

下面我们就要使用Proxifier这个软件，控制代理规则。具体的操作如下:

- Profile -> Advance -> Http Proxy Servers -> 开启
- Profile -> Proxifier -> 添加可以访问外网的代理
- Profile -> Proxification Rules -> Add 
    1. 命名随意，比如`ss`
    2. 应用软件添加shadowsocks.exe
    3. action选择第二步添加的可以访问外网的代理
    4. 如果http的代理不可用，可在第二步时，添加或追加一个相同地址的https代理
    5. 记得把新添加的放在最上面，规则是从上往下执行的，并且保留最后一个defalut,不然其他情况上不了网了。。
- Save

接着开启shadowsocks，启用系统代理（关于这个系统代理，我是将ie下面的Lan代理选择了自动模式）。

最后，安装chrome的插件SwitchOmega（其实就是proxySwitchy的新版本）。添加新规则，选择socket5代理，地址填写127.0.0.1, 端口1080。使用新的规则模式上网，比如twitter.com进行一下测试，或者查看一下ip地址。

关于SwitchOmega这个插件，我推荐大家再建立一个规则，设置为公司提供的代理。并且在自动切换模式下，将公司代理设置为默认访问方式。这样下来，通过chrome上网就不存在障碍了。

## 内网加速
进行了一番科学上网的设置后，基本所有的网络都是可以上了。缺点也有，就是公司封锁了的地址需要借助代理，这些大多的是国内的网站，走代理速度肯定不太好。那么我们还有什么办法可以让被公司封锁了的国内应用访问更加自如呢？这个想法我想在国外的留学生朋友一定也有需求，国外看国内的视频网站也是被封锁的，所以需要借助国内的服务器，进行一下代理，这里我~~推荐一下goagent+SAE的方法。~~其实还是推荐自己在国内的vps上搭建一下shadowsocks，使用确实速度快，稳定。这两点我个人感觉比goagent好得多。

说了这么一大推，下面实践一下(原理还是和上面一样的)。

### goagent+SAE
**必备条件**：
- SAE账号，便于创建应用
- goagent
- proxifier

**步骤**:
- 在SAE上创建一个应用，记住生成的地址(其实就是your_app_name.sinaapp.com这样的)
- 将goagent/serve/php下目录文件打包上传SAE(SAE应用有上传代码的菜单)
- 编辑goagent/local/proxy.ini
    - [gae] -> enable属性 -> 由1修改为0,关闭gae模块
    - [pac] -> 如果不需要切换的话，也是由1修改为0
    - [php] -> enable -> 设置为1， 表示开启
    - [php] -> fetchserver -> 设置为应用地址，就是类似`http://xxx.sinaapp.com/`
- 开启goagent.exe， 如果有警告你需要使用管理员权限运行，而普通权限暂时也没问题的情况下，忽略那个警告吧。

开启之后，本地就会有一个8088端口的http代理，这样就可以通过proxifier或者switchOmega设置代理规则了。

### shadowsocks+阿里云
**必备条件**:
- 国内的vps
- shadowsocks客户端: [shadowsocks-qt5](https://github.com/librehat/shadowsocks-qt5/releases)
- proxifier

我的国内代理搭建在阿里云上（ps:国内vps确实贵，带宽还小）。搭建的方式使用的是`docker`，具体操作可以查阅: [搭建shadowsocks](/software/develop-tool/shadowsocks.html)。

shadowsocks的客户端可以选择qt5,这样本地就可以开多个shadowsocks客户端了。

**步骤**:
- 服务器上搭建好`shadowsocks`
- 开启一个shadowsocks客户端,输入账号，指定本地端口
- proxifier rules添加一个规则，针对这个shadowsocks客户端，使其走公司提供的外网代理
- 浏览器或者proxifier可以使用本地端口的socks5代理

这样的话，国内访问速度就会比较流畅了，唯一的缺点就是国内vps价格比较贵。

## 参考资料
- [goagent](https://github.com/goagent/goagent)
- [shadowsocks](https://github.com/shadowsocks/shadowsocks)
- [proxifier](https://www.proxifier.com/)
- [利用Proxifier把shadowsocks转为全局代理](http://dangger.net/2014/07/24/17.html)
- [利用BAE搭建Goagent代理服务突破内网封锁](http://goodbai.com/secure/UseGoagentCrossLan.html)
- [利用Sina App Engine翻墙回国内看优酷土豆等网络视频](http://www.lovelucy.info/sae-china-proxy.html)
- [使用Proxifier解决Dropbox无法实时更新问题](http://hazelzhu.com/archives/1294)
