# 善用搜索
学会了如何提问，其实已经能把握住问题的中心，也就可以先使用搜索去尝试解决问题。

## 搜索引擎选择
通常我也会根据具体的搜索内容决定使用什么引擎，比如我要搜技术类的问题，肯定优先考虑google。搜索下载资源，优先考虑相应的下载资源网站。做到缩小搜索范围，才能让搜索结果的质量得到提高。

其实配合上`site`的用法，在google上也能很快锁定搜索结果。

常用的几个站点：
- [google](http://google.com/ncr)
- [baidu](http://baidu.com)
- [Duck Duck Go](http://duckduckgo.com)
- [海盗湾](http://thepiratebay.se/)
- [天天美剧](http://www.ttmeiju.com/)
- [豆瓣](http://douban.com)

## 设置Chrome的搜索
Chrome是我最常用的浏览器，大部分搜索我都是在它之中完成的，那么如何节约时间呢。首先了解一个快捷键：`command+l`,快速定位到地址栏。

其次借助Chrome的地址栏搜索功能，快速搜索。中文版默认的可能是百度搜索，我比较喜欢设置google搜索，打开`Setting->Search->Manage search engines`，修改defalut search为：

```
Google google.com {google:baseURL}search?q=%s&{google:RLZ}{google:originalQueryForSuggestion}{google:assistedQueryStats}{google:searchFieldtrialParameter}{google:bookmarkBarPinned}{google:searchClient}{google:sourceId}{google:instantExtendedEnabledParameter}{google:omniboxStartMarginParameter}{google:contextualSearchVersion}ie={inputEncoding}
```

如果设置了代理的，可以先访问google.com/ncr选择为通用版本。确保访问到页面是通用版本，在地址栏里搜索试试。如果还会自动转向到代理的国家，Chrome也会提示你继续使用还是切换为google.com。同时需要设置`Setting->Currently showing search results in`为English, 中文 (简体)。

如果只选择结果为English,那么挂上日本的代理，出现的结果优先会是日文。

### 其他搜索设置
在Chrome的地址栏中，也可以设置快捷键触发其他搜索, 在`Setting->Search->Manage search engines`，添加：

```
DDK duckduckgo.com https://duckduckgo.com/?q=%s
```

类似的规则，在地址栏中输入duckduckgo然后按一下tab，就可以选择自定义的引擎进行搜索。



## 搜索技巧
直接给一张图解释:
![善用google搜索技巧](http://pic3.zhimg.com/91d36cd9e5bef1030380894911782358_b.jpg)

## 参考资料
- [Google语法详解](http://www.docin.com/p-201879681.html)
- [搜索引擎有哪些常用技巧？](http://www.zhihu.com/question/19847393)
- [如何用好 Google 等搜索引擎](http://www.zhihu.com/question/20161362)