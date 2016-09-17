# 如何翻墙
既然想学点东西，就不能被网络束缚住。国内的网络环境，并不利于我们成长。

## 什么是墙
[great firewall](http://baike.baidu.com/link?url=Ko6D0GzKfQ2gXQ3oXLr-6_Racoa5uo8UApoNRRV5Jc8LyCYv1fGBGDxMxOV7ULARGidRgcoM6DVh3m06PMD_y823plq8PCCs51xmz6aJoY_), 中国特有的。就是国家对网络的封锁。想要看看外面的世界，就得翻墙。

## 如何翻墙
翻墙的服务一般都是收费的，免费的除了goAgent，其他都不要尝试了，不然只是在浪费生命。我比较提倡用钱能解决的问题，尽量还是花些钱吧。

目前来说，我了解的方式主要有两种：VPN和Shadowsocks。

## VPN
在公用网络上建立专用网络，进行加密通讯。原理是在一个国外网络无阻的机器上与本地机器通信。

优点是方便设置，网络速度稳定。

缺点是稳定的服务价格不便宜，且本地流量全部走的是代理。

### 配合VPN实现国内外分流访问
“分流”，这个词不知道说的准不准确，意思就是实现对不需要翻墙的网站直接连接，需要翻墙的网站走VPN代理。这样国内的网站访问不受影响，又能正常访问国外站点。

实现方式就是修改系统的路由表，网络上有这样的开源项目，专门收集国内被“墙”的网站。利用这些数据，让vpn客户端在进行连接的时候自动执行.

通过这些路由脚本, 可以让用户在使用vpn作为默认网络网关的时候, 不使用vpn进行对中国国内ip的访问, 从而减轻vpn的负担, 和增加访问国内网站的速度.

**Mac设置**：

1. 下载附件mac.zip, 并将其中的ip-up, ip-down两个文件放入到 /etc/ppp目录中。
2. 开终端，执行命令  cd  /private/etc/ppp，进入/etc/ppp目录下。
3. 在该目录下执行sudo chmod a+x ip-up ip-down
4. 好了，可以连接VPN试试了。

**Windows设置**：

1. 下载附件windows.zip, 并将其中的vpnup.bat, ivpndown.bat两个文件解压到任意目录。
2. 右击vpnup.bat，选择以管理员权限运行，然后会弹出cmd窗口，等待运行完毕，窗口会自动关闭。（Windows需要每次开机时执行一次）
3. 好了，可以连接VPN试试了。

**测试方式**:连接VPN后，可以访问ip.cn查看当前的ip,如果显示南京就对了，然后再打开youtube.com看看能否访问。

**一点说明**: ip-down和vpndown.bat是恢复路由表的脚本。

## goagent
[goagent](https://github.com/goagent/goagent), 项目主页里有详细的安装使用指南。需要你注册google的GAE服务。

当然，你可以用来当做教育网加速，或者穿透公司内网。我目前放在SAE上用来穿透公司http代理。

使用的过程之后，可能会遇到证书错误而不受信任的情况，解决方式就是导入证书。详情可见: [解决GoAgent打开https网站SSL证书错误 (安全证书不受信任)](http://blog.netsh.org/posts/goagent-https-ssl-error_1013.netsh.html)


## Shadowsocks
shadowsocks的出现，我觉得真是一大利好。它解决了网络流量分配的问题，借助代理插件，可以方便的实现只针对需要翻墙的网站都代理访问。且价格便宜。

一般情况下，我使用Chrome的插件: [Proxy SwitchySharp](https://chrome.google.com/webstore/detail/dpplabbmogkhghncfbfdeeokoefdjegm)。

shadowsocks的服务，如果自己有vps的话，就自己搭建一个，分分钟的事情，自己搜搜教程。如果没有的话，也可以去买这样的服务，我用东哥的ss，包年100，速度很好。

## chnroutes
[chnroutes](https://github.com/fivesheep/chnroutes)，此项目通过修改路由表，解决通过VPN链接网络时的流量转向问题。达到不需要翻墙的访问走正常网络，需要翻墙的请求走VPN。


## ChinaDNS
[ChinaDNS](https://github.com/clowwindy/ChinaDNS), 此项目解决的是DNS污染问题，我还没搞明白。。。

## 参考资料
- [Chnorutes生成的脚本下载地址](http://chnroutes-dl.appspot.com/): 需要翻墙。