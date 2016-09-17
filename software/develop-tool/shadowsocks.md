# shadowsocks
换上Mac后，发现shadowsocks居然可以设置全局和自动代理，真实比Windows下方面多了！之前我一直购买的是东哥的服务，一年才50RMB,速度也还可以，720p无压力。自己另有一台DigitalOcean VPS,不用也浪费，搭建一个好了。

## Docker安装Shadowsocks
这是我试过最便捷的方式了，**强烈推荐**。只要下载docker镜像的速度够快，搭建真实几分钟的事情，命令也就两三条，咱们来试试：

### 配置docker
如果是DigitalOcean或者国内的阿里云，现在都可以选择在创建的时候Docker镜像。这样开启vps就能直接使用docker了。服务器一般我会选择Ubuntu 14.04版本。

如果没有Docker可选，那么也没关系，进如vps之后，自己安装一下即可。

### 安装shadowsocks
首先通过ssh连接到vps上。因为有了docker之后，就可以下载shadowsocks的镜像：

```
docker pull oddrationale/docker-shadowsocks
```

我在国内的阿里云上下载的时候会比较慢，因为不是官方的镜像（官方的镜像阿里云都有备份，这点确实做的很体贴）。

### 运行设置shadowsocks
输入:

```
docker run -d -p 1984:1984 oddrationale/docker-shadowsocks -s 0.0.0.0 -p 1984 -k paaassswwword -m aes-256-cfb
```

这里的`1984`是服务器端的端口号，`paaassswwword`是密码， `aes-256-cfb`是加密方式。

运行:

```
docker ps
```

查看shadowsocks是否运行起来了，没问题的话就可以`exit`退出vps的登录了。

### 客户端设置
客户端填写好公网ip,端口，加密方式，即可连接。

## Ubuntu下安装
首先，建议使用root用户登录，或者使用sudo命名，我这里以root用户为例把。请按顺序执行下面操作哦！

### 安装shadowsocks
第一次装的时候乱七八杂，也记不起来顺序了，反正用到的就是python版本，通过python-pip下载安装的`shadowsocks`:

```
apt-get install python-pip
pip install shadowsocks
```

### 配置shadowsocks
配置文件需要自行创建：

```
vim /etc/shadowsocks.json
```

写入：

```
{
    "server":"0.0.0.0", # replace your server IP
    "server_port":4762,
    "local_port":1080,
    "password":"8d779a1ee2db776db8e20adffaa12d0c",
    "timeout":300,
    "method":"aes-256-cfb"
}
```

### 安装Supervisor
```
apt-get update
apt-get install python-pip python-m2crypto supervisor
```

### 配置Supervisor
编辑或创建:

```
vim /etc/supervisor/conf.d/shadowsocks.conf
```

如果端口 < 1024，把上面的 user=nobody 改成 user=root。

### 优化
在 `/etc/default/supervisor` 最后加一行：

```
ulimit -n 51200
```

### 启动shadowsocks服务
使用Supervisor后台运行shadowsocks:

```
service supervisor start
supervisorctl reload
```




### 查看服务状态
运行状态：
`supervisorctl status`

如果遇到问题，可以检查日志：
```
supervisorctl tail -f shadowsocks stderr
```


### 重启服务
如果修改了 shadowsocks 配置 /etc/shadowsocks.json， 可以重启 shadowsocks：
`supervisorctl restart shadowsocks`

如果修改了 Supervisor 的配置文件 /etc/supervisor/*， 可以更新 supervisor 配置：
`supervisorctl update`

## 可能出现的异常情况
在我第一次安装的时候，出现过`unable to resolve host`的情况。解决方法就是将其指向127.0.0.1,编辑`/etc/hosts`文件,在`127.0.0.1`后面，添加上自己主机的名称。


## 参考资料
- [Shadowsocks 使用说明](https://github.com/clowwindy/shadowsocks/wiki/Shadowsocks-%E4%BD%BF%E7%94%A8%E8%AF%B4%E6%98%8E)
- [用 Supervisor 运行 Shadowsocks](https://github.com/clowwindy/shadowsocks/wiki/%E7%94%A8-Supervisor-%E8%BF%90%E8%A1%8C-Shadowsocks)
- [在 Linode 上快速搭建 Shadowsocks](https://github.com/clowwindy/shadowsocks/wiki/%E5%9C%A8-Linode-%E4%B8%8A%E5%BF%AB%E9%80%9F%E6%90%AD%E5%BB%BA-Shadowsocks)
- [sudo 出现unable to resolve host 解决方法](http://blog.csdn.net/ichuzhen/article/details/8241847)
- [Docker + DigitalOcean + Shadowsocks 5分钟科学上网](http://liujin.me/blog/2015/05/27/Docker-DigitalOcean-Shadowsocks-5-%E5%88%86%E9%92%9F%E7%A7%91%E5%AD%A6%E4%B8%8A%E7%BD%91/)