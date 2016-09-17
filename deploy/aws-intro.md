# AWS简介
AWS(amazon web service), 是Amazon推出的一套云计算服务，2014年进入中国，建立亚洲数据中心。但是国内账号和全球账号是独立的，这一点需要明白。新用户绑定信用卡，即可获得一年的免费使用权。

## 注册
注册国际版本的，需要一张信用卡，我用的是招行的VISA,还需要有一个手机验证的步骤，我的移动手机号没成功，借了同事的联通号码，然后验证通过了。我不确定是否是运营商的问题，或者是我的手机号注册过AWS的服务。。。

验证完成之后，我们就可以选择basic模式，开始免费之旅。

## 服务介绍
### S3
S3是`Simple Storage Service`的简称。第一次使用需要创建一个`bucket`,就相当于一个存储空间，这个命名需要唯一。然后上传文件到此目录即可。

如果我们要使用S3部署静态网站的话，我们还需要进行一些设置， 记住一点，创建的bucket要和域名一致:

- 在S3上创建一个`bucket`，会根据命名获得一个s3对应的访问域名，比如命名为`legacydemo.com`会生成`legacydemo.com.s3-website-us-west-2.amazonaws.com`
- 右击新创建的`bucket`，在属性中，开启静态部署，设置`index Document`和`Error Document`。
- 到域名注册商那里，在`DNS Records`中添加一条`CNAME`,指向S3给我们提供的域名
- 等待域名更新，访问自己的域名

## 参考资料
- [amazon web services](https://aws.amazon.com/): 官网
- [中文官网](http://aws.amazon.com/cn/)
- [AWS Documentation](http://aws.amazon.com/documentation/)