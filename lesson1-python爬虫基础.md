# python全栈专项训练营
-------------------------
- **lesson1 python爬虫基础**
- **lesson2 招聘网站爬虫实战**
- **lesson3 数据可视化项目实战**

## python爬虫基础

##### 主要内容：
1. 爬虫基础知识
2. 爬虫请求的发送方法
3. 数据的提取方法
4. 案例：完成煎蛋网图片的爬虫http://jandan.net/ooxx

### 爬虫的定义与使用场景

#### 为什么学习爬虫

1. 学习爬虫，可以私人订制一个搜索引擎，同时可以对搜索引擎的数据采集工作原理进行更深层次地理解。

2. 大数据时代，要进行数据分析，首先要有数据源，而学习爬虫，可以让我们获取更多的数据源，并且这些数据源可以按我们的目的进行采集，去掉很多无关数据。

3. 对于很多SEO从业者来说，学习爬虫，可以更深层次地理解搜索引擎爬虫的工作原理

4. 从就业的角度来说，爬虫工程师目前来说属于紧缺人才，并且薪资待遇普遍较高

大量数据散落在互联网中，要分析析互联网上的数据，需要先把数据从网络中获取下来，这就需要爬虫技术，在爬虫系统中，待抓取URL队例是很重要的一部分，待抓取URL队列中的URL以什么样的顺序排列也是一个很重要的问题，因为其决定了先抓取哪个页面、后抓取哪个页面。而决定这些URL排列顺序的方法叫做抓取策略，下面介绍，几种常见抓取策略：

      1.深度优先遍历策略，深度优先遍历策略是指网络爬虫会起始页开始，一个链接一个链接跟踪下云，处理完这条线路之后，再转入下一个起始页，继续跟踪链接。
    
      2.宽度优先遍历策略，宽度优先遍历策略的基本思路是将新下载网页中发现的链接直接插入待抓取URL队列的末尾，也就是说，网络爬虫会先抓取起始网页中链接的所有网页，然后再选择其中的一个链接网页，继续抓取网页中链接的所有网页。
    
      3.反向链接数策略，反向链接数是指一个网页被其他网页链接指向的数量。反向链接数表示的是一个网页的内容受到其他人推荐的程度。因此，很多时候搜索引擎的抓取系统会使用这个指标来评价网页的重要程度，从而决定不同网页抓取顺序。
    
      4.大站优先策略，对于待抓取URL队列中的所有网页，根据所属的网站进行分类；对于待下载页面数多的网站，则优先下载。这种策略也因此被叫作大站优先策略。

**目前，人工智能，大数据广泛被企业应用起来，并且也开展了相关的业务，但是众所周知人工智能和大数据中有一个东西是非常重要的，那就是数据，那么数据从哪里来呢？又是怎么获得的呢？**

比如百度指数，阿里指数，360指数等等，这些网站有非常大的用户量，他们能够获取自己用户的数据进行统计和分析
- https://trends.so.com/?src=index.so.com 360
- http://index.baidu.com/v2/index.html#/ 百度
- https://index.1688.com/ 阿里

##### 1.数据的来源

- 去第三方的公司购买数据
- 去免费的数据网站下载数据(比如国家统计局)
- 通过爬虫爬取数据
- 人工收集数据(比如问卷调查)

##### 2.爬取到的数据用途


```python
from IPython.display import IFrame
# 百度新闻，一家并不是做新闻的公司，这个网站上的新闻数据从哪里来的呢？
IFrame('https://news.baidu.com/', width=1200, height=600)
```



<iframe
    width="1200"
    height="600"
    src="https://news.baidu.com/"
    frameborder="0"
    allowfullscreen
></iframe>




通过点击，我们可以发现，他的新闻数据都是其他网站上的，在百度新闻上仅仅做了展示
如果后续我们要做一个网站，天天新闻，是不是也可以这样做呢

爬虫获取的数据用途：
- 进行在网页或者app上进行展示
- 进行数据分析或者用于机器学习相关的项目

在上面的来源中：人工的方式费时费力，免费的数据网站上的数据质量不佳，很多第三方的数据公司他们的数据来源往往也是爬虫获取的，所以获取数据最有效的途径就是通过爬虫爬取

#### 什么是爬虫？

网络爬虫是一种按照一定的规则，自动地抓取万维网信息的程序或者脚本。
> 模拟浏览器发送网络请求，接收请求响应

Python爬虫是用Python编程语言实现的网络爬虫，主要用于网络数据的抓取和处理，

#### 爬虫的用途：
- 批量打包下载小说
- 下载各种图片
- 批量查询快递单号
- 采集数据并分类保存
- 下载音乐或视频
- 检查网站性能
- 监控数据，及时提醒、
- 开发聊天机器人
- 抢车票、机票
- ...

总之，用途很多，还待我们去探索。

### 爬虫的分类与爬虫的流程

#### 爬虫的分类

网络爬虫按照系统结构和实现技术，大致可以分为以下几种类型

- 通用网络爬虫

- 聚焦网络爬虫

- 增量式网络爬虫

- 深层网络爬虫

实际的网络爬虫是几种爬虫技术相结合实现的

<style>
table th:first-of-type {
    width: 10%;
}
table th:nth-of-type(2) {
    width: 30%;
}
table th:nth-of-type(3) {
    width: 30%;
}
table th:nth-of-type(4) {
    width: 30%;
}
</style>
|   名称    |  场景   |  特点    |   缺点   |
|  :----:  | :----  | :----  | :----  |
| 通用网络爬虫  | 门户站点搜索引擎、大型Web服务提供商采集数据 |爬行范围和数量巨大、爬行页面顺序要求低、并行工作方式，爬取互联网上的所有数据  |爬虫速度和存储空间要求高、刷新页面的时间长  |
| 聚焦网络爬虫  | 又称主题网络爬虫，只爬行特定的数据，商品比价 | 极大节省了硬件和网络资源，页面更新快 |  |
| 增量式网络爬虫  | 只抓取刚刚更新的数据 | 数据下载量少，及时更新已爬行的网页，减少时间可空间上的耗费、爬取到的都是最新页面 | 增加了爬行算法的复杂度和实现难度 |
| 深层网络爬虫  |   | 大部分内容不能通过静态链接获取，隐藏在搜索表单后，用户提交一些关键词才能获得 |   |

根据被爬网站的数量的不同，我们把爬虫分为：

通用爬虫 ：通常指搜索引擎的爬虫（https://www.baidu.com）

聚焦爬虫 ：针对特定网站的爬虫

#### 爬虫如何抓取网页数据？

1. 网页的三大特征（http://jandan.net/ooxx）：
    - 每个网页都有自己的URL（统一资源定位符）来定位
    - 网页都使用HTML(超文本标记语言)来描述页面信息
    - 网页都使用HTTP/HTTPS（超文本传输协议）来传输HTML数据

2. 爬虫的设计思路：
    - 首先确定需要爬取的网URL地址
    - 通过HTTP/HTTPS协议来获取对应的HTML页面
    - 提取HTML页面内有用的数据：
        - 如果是需要的数据--保存
        - 如果有其他URL，继续执行第二步

#### 通用爬虫
- 定义： 
搜索引擎用的爬虫系统

- 目标： 
把所有互联网的网页爬取下来，放到本地服务器形成备份，在对这些网页做相关处理（提取关键字，去除广告），最后提供一个用户可以访问的接口

- 抓取流程：
    - 首先选取一部分已有的URL， 把这些URL放到带爬取队列中
    - 从队列中取出来URL，然后解析NDS得到主机IP，然后去这个IP对应的服务器里下载HTML页面，保存到搜索引擎的本地服务器里，之后把爬过的URL放入已爬取队列
    - 分析网页内容，找出网页里其他的URL连接，继续执行第二步，直到爬取结束

- 搜索引擎如何获取一个新网站的URL：

    - 主动向搜索引擎提交网址： https://ziyuan.baidu.com/linksubmit/index
    - 在其他网站设置网站的外链： 其他网站上面的友情链接
    - 搜索引擎会和DNS服务商进行合作，可以快速收录新网站

- 通用爬虫注意事项

    - 通用爬虫并不是万物皆可以爬，它必须遵守规则：
    - Robots协议：协议会指明通用爬虫可以爬取网页的权限
    - 我们可以访问不同网页的Robots权限
    
- Robots协议：网站通过Robots协议告诉搜索引擎哪些页面可以抓取，哪些页面不能抓取，但它仅仅是互联网中的一般约定

- 通用爬虫通用流程：
  ![image.png](attachment:image.png)

   爬取页面->存储数据->内容处理->提供检索->排名服务

- 通用爬虫缺点
    - 只能提供和文本相关的内容(HTML,WORD,PDF)等，不能提供多媒体文件(msic,picture, video)及其他二进制文件
    - 提供结果千篇一律，不能针对不同背景领域的人听不同的搜索结果 
    - 不能理解人类语义的检索

#### 聚焦爬虫
- 爬虫程序员写的针对某种内容的爬虫-> 面向主题爬虫，面向需要爬虫

#### 爬虫的流程

- 向起始url发送请求，并获取响应
- 对响应进行提取
- 如果提取url，则继续发送请求获取响应
- 如果提取数据，则将数据进行保存

## 请求的发送方法

### requests模块的使用

#### requests模块发送简单的get请求、获取响应
##### 需求：通过requests向百度首页发送请求，获取百度首页的数据https://www.baidu.com


```python
import requests

# 目标url地址
url = 'https://www.baidu.com'

# 向目标url发送get请求，获取响应
response = requests.get(url)

# 打印响应内容
print(response.content.decode() )
```

    <!DOCTYPE html>
    <!--STATUS OK--><html> <head><meta http-equiv=content-type content=text/html;charset=utf-8><meta http-equiv=X-UA-Compatible content=IE=Edge><meta content=always name=referrer><link rel=stylesheet type=text/css href=https://ss1.bdstatic.com/5eN1bjq8AAUYm2zgoY3K/r/www/cache/bdorz/baidu.min.css><title>百度一下，你就知道</title></head> <body link=#0000cc> <div id=wrapper> <div id=head> <div class=head_wrapper> <div class=s_form> <div class=s_form_wrapper> <div id=lg> <img hidefocus=true src=//www.baidu.com/img/bd_logo1.png width=270 height=129> </div> <form id=form name=f action=//www.baidu.com/s class=fm> <input type=hidden name=bdorz_come value=1> <input type=hidden name=ie value=utf-8> <input type=hidden name=f value=8> <input type=hidden name=rsv_bp value=1> <input type=hidden name=rsv_idx value=1> <input type=hidden name=tn value=baidu><span class="bg s_ipt_wr"><input id=kw name=wd class=s_ipt value maxlength=255 autocomplete=off autofocus=autofocus></span><span class="bg s_btn_wr"><input type=submit id=su value=百度一下 class="bg s_btn" autofocus></span> </form> </div> </div> <div id=u1> <a href=http://news.baidu.com name=tj_trnews class=mnav>新闻</a> <a href=https://www.hao123.com name=tj_trhao123 class=mnav>hao123</a> <a href=http://map.baidu.com name=tj_trmap class=mnav>地图</a> <a href=http://v.baidu.com name=tj_trvideo class=mnav>视频</a> <a href=http://tieba.baidu.com name=tj_trtieba class=mnav>贴吧</a> <noscript> <a href=http://www.baidu.com/bdorz/login.gif?login&amp;tpl=mn&amp;u=http%3A%2F%2Fwww.baidu.com%2f%3fbdorz_come%3d1 name=tj_login class=lb>登录</a> </noscript> <script>document.write('<a href="http://www.baidu.com/bdorz/login.gif?login&tpl=mn&u='+ encodeURIComponent(window.location.href+ (window.location.search === "" ? "?" : "&")+ "bdorz_come=1")+ '" name="tj_login" class="lb">登录</a>');
                    </script> <a href=//www.baidu.com/more/ name=tj_briicon class=bri style="display: block;">更多产品</a> </div> </div> </div> <div id=ftCon> <div id=ftConw> <p id=lh> <a href=http://home.baidu.com>关于百度</a> <a href=http://ir.baidu.com>About Baidu</a> </p> <p id=cp>&copy;2017&nbsp;Baidu&nbsp;<a href=http://www.baidu.com/duty/>使用百度前必读</a>&nbsp; <a href=http://jianyi.baidu.com/ class=cp-feedback>意见反馈</a>&nbsp;京ICP证030173号&nbsp; <img src=//www.baidu.com/img/gs.gif> </p> </div> </div> </div> </body> </html>



##### response的常用属性：
- response.text 响应体 str类型
- respones.content 响应体 bytes类型
- response.status_code 响应状态码
- response.request.headers 响应对应的请求头
- response.headers 响应头
- response.request._cookies 响应对应请求的cookie
- response.cookies 响应的cookie（经过了set-cookie动作）


```python

```

##### response.text 和response.content的区别
- response.text

    - 类型：str
    - 解码类型： requests模块自动根据HTTP 头部对响应的编码作出有根据的推测，推测的文本编码
    - 如何修改编码方式：response.encoding=”gbk”
- response.content

    - 类型：bytes
    - 解码类型： 没有指定
    - 如何修改编码方式：response.content.deocde(“utf8”)

- 获取网页源码的通用方式：

    - response.content.decode()
    - response.content.decode("GBK")
    - response.text

以上三种方法从前往后尝试，能够100%的解决所有网页解码的问题

所以：更推荐使用response.content.deocde()的方式获取响应的html页面

##### 把网络上的图片保存到本地
我们来把百度的logo图片保存到本地，图片的url: https://www.baidu.com/img/bd_logo1.png

- 思考：
    - 以什么方式打开文件
    - 保存什么格式的内容
- 分析：
    - 图片的url: https://www.baidu.com/img/bd_logo1.png
    - 利用requests模块发送请求获取响应
    - 以2进制写入的方式打开文件，并将response响应的二进制内容写入

```python
from ipywidgets import Image
# Image.from_url('https://www.baidu.com/img/bd_logo1.png')
Image.from_file("baidu.png")

import requests
url = 'https://www.baidu.com/img/bd_logo1.png'
res = requests.get(url)
# print(res.content)
with open('baidu.png','wb')as f:
    f.write(res.content)
!ls
```

#### 发送带header的请求
- header的形式：字典
  
    headers = {"User-Agent": "Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_5) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/84.0.4147.135 Safari/537.36"}

- 用法
requests.get(url, headers=headers)


```python
import requests

url = 'https://www.baidu.com'

headers = {"User-Agent": "Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_5) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/84.0.4147.135 Safari/537.36"}

# 在请求头中带上User-Agent，模拟浏览器发送请求
response = requests.get(url, headers=headers) 

# print(response.content.decode())

# 打印请求头信息
print(response.request.headers)

// 反爬有点效果
from fake_useragent import UserAgent
ua = UserAgent()
for i in range(10):
    print(ua.random)
```

    {'User-Agent': 'Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_5) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/84.0.4147.135 Safari/537.36', 'Accept-Encoding': 'gzip, deflate', 'Accept': '*/*', 'Connection': 'keep-alive'}


##### 为什么请求需要带上header？
- 模拟浏览器，欺骗服务器，获取和浏览器一致的内容


```python
import requests
url = 'https://www.baidu.com'
response = requests.get(url) 
# print(response.content.decode())

import requests
url = 'https://www.baidu.com'
headers = {"User-Agent": "Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_5) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/84.0.4147.135 Safari/537.36"}
# 在请求头中带上User-Agent，模拟浏览器发送请求
response = requests.get(url, headers=headers) 
# print(response.content.decode())
```

#### 发送带参数的请求
- https://www.baidu.com/
- https://www.baidu.com/s?ie=utf-8&f=8&rsv_bp=1&rsv_idx=1&tn=baidu&wd=python&fenlei=256&rsv_pq=aa00d99800001846&rsv_t=d2950XXxSwQWnn5AuJaHDBxPVRUVquhFCYYquXPWObURUKmD5j4eSSMQ%2BNg&rqlang=cn&rsv_enter=1&rsv_dl=tb&rsv_sug3=7&rsv_sug1=6&rsv_sug7=100&rsv_sug2=0&rsv_btype=i&inputT=1862&rsv_sug4=1862&rsv_sug=2

##### 什么叫做请求参数：
- ？后边的就是请求参数，又叫做查询字符串


##### 请求参数的形式：字典
> kw = {'wd':'python'}


##### 请求参数的用法
> requests.get(url,params=kw)


##### 关于参数的注意点
- 在url地址中， 很多参数是没有用的，比如百度搜索的url地址，其中参数只有一个字段有用，其他的都可以删除 如何确定那些请求参数有用或者没用：挨个尝试！ 对应的,在后续的爬虫中，都可以尝试删除参数


```python
# 方式一：利用params参数发送带参数的请求
import requests

headers = {"User-Agent": "Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/54.0.2840.99 Safari/537.36"}

# 这是目标url
# url = 'https://www.baidu.com/s?wd=python' 

# 最后有没有问号结果都一样
url = 'https://www.baidu.com/s?' 

# 请求参数是一个字典 即wd=python
kw = {'wd': 'python'} 

# 带上请求参数发起请求，获取响应
response = requests.get(url, headers=headers, params=kw) 

# 当有多个请求参数时，requests接收的params参数为多个键值对的字典，比如 '?wd=python&a=c'-->{'wd': 'python', 'a': 'c'}

print(response.content)
```

    b'<!DOCTYPE html>\n<html lang="zh-CN">\n<head>\n    <meta charset="utf-8">\n    <title>\xe7\x99\xbe\xe5\xba\xa6\xe5\xae\x89\xe5\x85\xa8\xe9\xaa\x8c\xe8\xaf\x81</title>\n    <meta http-equiv="Content-Type" content="text/html; charset=utf-8">\n    <meta name="apple-mobile-web-app-capable" content="yes">\n    <meta name="apple-mobile-web-app-status-bar-style" content="black">\n    <meta name="viewport" content="width=device-width, user-scalable=no, initial-scale=1.0, minimum-scale=1.0, maximum-scale=1.0">\n    <meta name="format-detection" content="telephone=no, email=no">\n    <link rel="shortcut icon" href="https://www.baidu.com/favicon.ico" type="image/x-icon">\n    <link rel="icon" sizes="any" mask href="https://www.baidu.com/img/baidu.svg">\n    <meta http-equiv="X-UA-Compatible" content="IE=Edge">\n    <meta http-equiv="Content-Security-Policy" content="upgrade-insecure-requests">\n    <link rel="stylesheet" href="https://wappass.bdimg.com/static/touch/css/api/mkdjump_8befa48.css" />\n</head>\n<body>\n    <div class="timeout hide">\n        <div class="timeout-img"></div>\n        <div class="timeout-title">\xe7\xbd\x91\xe7\xbb\x9c\xe4\xb8\x8d\xe7\xbb\x99\xe5\x8a\x9b\xef\xbc\x8c\xe8\xaf\xb7\xe7\xa8\x8d\xe5\x90\x8e\xe9\x87\x8d\xe8\xaf\x95</div>\n        <button type="button" class="timeout-button">\xe8\xbf\x94\xe5\x9b\x9e\xe9\xa6\x96\xe9\xa1\xb5</button>\n    </div>\n    <div class="timeout-feedback hide">\n        <div class="timeout-feedback-icon"></div>\n        <p class="timeout-feedback-title">\xe9\x97\xae\xe9\xa2\x98\xe5\x8f\x8d\xe9\xa6\x88</p>\n    </div>\n\n<script src="https://wappass.baidu.com/static/machine/js/api/mkd.js"></script>\n<script src="https://wappass.bdimg.com/static/touch/js/mkdjump_1448d18.js"></script>\n</body>\n</html>'



```python
# 方式二：直接发送带参数的url的请求
import requests

headers = {"User-Agent": "Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/54.0.2840.99 Safari/537.36"}

url = 'https://www.baidu.com/s?wd=python'

# kw = {'wd': 'python'}

# url中包含了请求参数，所以此时无需params
response = requests.get(url, headers=headers)
```

#### 使用requests发送POST请求

> 思考：哪些地方我们会用到POST请求？

- 登录注册（ POST 比 GET 更安全）
- 需要传输大文本内容的时候（ POST 请求对数据长度没有要求）

所以同样的，我们的爬虫也需要在这两个地方回去模拟浏览器发送post请求

##### requests发送post请求语法：
- 用法：

>  response = requests.post("http://www.baidu.com/", data = data, headers = headers)

- data 的形式：字典

##### POST请求练习
- 下面我们通过手机版百度翻译的例子看看post请求如何使用：
    - 地址：http://fanyi.baidu.com/

- 思路分析
    - 确定请求的url地址
    - 确定请求的参数
    - 确定返回数据的位置
    - 模拟浏览器获取数据

在模拟登陆等场景，经常需要发送post请求，直接使用requests.post(url,data)即可


```python
import requests

# 浏览器代{过}{滤}理
headers = {
    "user-agent": "Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/78.0.3904.97 Safari/537.36"
}

Unknown = input("请输入你要翻译的内容：")
url = "https://fanyi.baidu.com/sug"
data = { "kw":Unknown }
values = requests.post(url,data=data,headers=headers).json()
print(values)
x = 1
# 判断字符串是否包含中文
for i in Unknown:
    # 中文在正则里的范围是\u4e00-\u9fff
    if u'\u4e00' <= i <= u'\u9fff':
        x = 0
        break

# 英译中 和 中译英 输出的不一样 所有两种输出方法
if x!=0:
    print(values["data"][0]["v"])
else:
    # 因为中文的翻译输出的英文会包含中文的拼音 所以这里处理掉了
    value = values["data"][0]["v"].split("]")[1:]
    print(value[0].replace(" ",""))

```

    请输入你要翻译的内容：你好
    {'errno': 0, 'data': [{'k': '你好', 'v': '[nǐ hǎo] how do you do; how are you; hello;'}, {'k': '你好，陌生人', 'v': '网络 Hello Stranger; knowing me knowing you;'}, {'k': '你好吗', 'v': 'How are you; How are you doing; How do you do;'}]}
    howdoyoudo;howareyou;hello;


#### 使用代理
##### 为什么要使用代理
- 让服务器以为不是同一个客户端在请求
- 防止我们的真实地址被泄露，防止被追究

##### 代理的使用
- 用法：
    - requests.get("http://www.baidu.com",  proxies = proxies)
- proxies的形式：字典



### requests模块处理cookie

#### 爬虫中使用cookie
> 为了能够通过爬虫获取到登录后的页面，或者是解决通过cookie的反爬，需要使用request来处理cookie相关的请求

#### 爬虫中使用cookie的利弊
- 带上cookie的好处
    - 能够访问登录后的页面
    - 能够实现部分反反爬

- 带上cookie的坏处
    - 一套cookie往往对应的是一个用户的信息，请求太频繁有更大的可能性被对方识别为爬虫

#### requests处理cookie的方法
- 使用requests处理cookie有三种方法：
    - cookie字符串放在headers中
    - 把cookie字典放传给请求方法的cookies参数接收
    - 使用requests提供的session模块

#### cookie添加在heades中
- 复制浏览器中的cookie到代码中使用

>headers = {
    "User-Agent":"。。。",
    "Cookie":"。。。"}

>requests.get(url,headers=headers)

- 注意：
cookie有过期时间 ，所以直接复制浏览器中的cookie可能意味着下一程序继续运行的时候需要替换代码中的cookie，对应的我们也可以通过一个程序专门来获取cookie供其他程序使用；当然也有很多网站的cookie过期时间很长，这种情况下，直接复制cookie来使用更加简单


#### 使用requests.session处理cookie
requests 提供了一个叫做session类，来实现客户端和服务端的会话保持

- 会话保持有两个内涵：
    - 保存cookie，下一次请求会带上前一次的cookie
    - 实现和服务端的长连接，加快请求速度

- 使用方法

>session = requests.session()

>response = session.get(url,headers)

session实例在请求了一个网站后，对方服务器设置在本地的cookie会保存在session中，
下一次再使用session请求对方服务器的时候，会带上前一次的cookie

## 数据提取方法

### 数据提取的概念与数据分类

##### 在爬虫爬取的数据中有很多不同类型的数据,我们需要了解数据的不同类型并且有规律的提取和解析数据.
- 结构化数据：json，xml等 
    - 处理方式：直接转化为python类型 
- 非结构化数据：HTML 
    - 处理方式：正则表达式、xpath 

### 数据提取之json

#### json模块

<img src="https://images-cdn.shimo.im/NTBsFJ7p0w2dVD6W.png" width=50%>


```python
import json

mydict = {
    "errno": 0,
    "data": [{
        "k": "你好",
        "v": "[nǐ hǎo] how do you do; how are you; hello;"
    }, {
        "k": "你好，陌生人",
        "v": "网络 Hello Stranger; knowing me knowing you;"
    }, {
        "k": "你好吗",
        "v": "How are you; How are you doing; How do you do;"
    }]
}
```


```python
# json.dumps 实现python类型转化为json字符串
# indent实现换行和空格
# ensure_ascii=False实现让中文写入的时候保持为中文
json_str = json.dumps(mydict, indent=2, ensure_ascii=False)
print('json.dumps python_type-->json_str: {}'.format(type(json_str)))
```


```python
# json.loads 实现json字符串转化为python的数据类型
my_dict = json.loads(json_str)
print('json.loads json_str-->python_type: {}'.format(type(my_dict)))
```


```python
# json.dump 实现把python类型写入类文件对象
with open("json模块示例文件.txt", "w") as f:
    json.dump(mydict, f, ensure_ascii=False, indent=2)
print('json.dump 已成功写入文件')
```


```python
# json.load 实现类文件对象中的json字符串转化为python类型
with open("json模块示例文件.txt", "r") as f:
    my_dict = json.load(f)
    print('json.load 读取文件--> {}: {}'.format(type(my_dict), my_dict))
```

#### jsonpath模块
用来解析多层嵌套的json数据;JsonPath 是一种信息抽取类库，是从JSON文档中抽取指定信息的工具，提供多种语言实现版本，包括：Javascript, Python， PHP 和 Java。
- 安装方法：pip install jsonpath
- JsonPath 对于 JSON 来说，相当于 XPath 对于 XML

### 数据提取之正则

#### 什么是正则表达式
- 用事先定义好的一些特定字符、及这些特定字符的组合，组成一个规则字符串，这个规则字符串用来表达对字符串的一种过滤逻辑。

#### re模块的常见方法
- re.match（从头找一个）
- re.search（找一个）
- re.findall（找所有）
- re.sub（替换）
- re.compile（编译，提升匹配速度）

### 数据提取之xpath

#### 什么是xpath
- XPath (XML Path Language) 是一门在 HTML\XML 文档中查找信息的语言，可用来在 HTML\XML 文档中对元素和属性进行遍历。

#### xpath语法

<img src="https://images-cdn.shimo.im/aQAkWIYopQCErsgI.png" width=70%>

### 数据提取之lxml

#### lxml的安装
- 安装方式：pip install lxml

#### lxml的使用

- 导入lxml 的 etree 库 
    - from lxml import etree
    - 利用etree.HTML，将字符串转化为Element对象,Element对象具有xpath的方法,返回结果的列表，能够接受bytes类型的数据和str类型的数据

        >html = etree.HTML(text) 
        
        >ret_list = html.xpath("xpath字符串")
        
    - 把转化后的element对象转化为字符串，返回bytes类型结果 etree.tostring(element)

### 数据提取之beautifulsoup

- 和 lxml 一样，Beautiful Soup 也是一个HTML/XML的解析器，主要的功能也是如何解析和提取 HTML/XML 数据。
- lxml 只会局部遍历，而Beautiful Soup 是基于HTML DOM的，会载入整个文档，解析整个DOM树，因此时间和内存开销都会大很多，所以性能要低于lxml。
- BeautifulSoup 用来解析 HTML 比较简单，API非常人性化，支持CSS选择器、Python标准库中的HTML解析器，也支持 lxml 的 XML解析器。

<img src="https://images-cdn.shimo.im/tKlh0Hv9tH6RMqhy.png" width=80%>

### 煎蛋网图片的爬取：
http://jandan.net/ooxx/


```python
# 原生爬取
import requests
import os

def url_open(url):
    headers = {
        "User-Agent": "Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/54.0.2840.99 Safari/537.36"
    }
    req = requests.get(url, headers=headers)
    html = req.content
    return html

def get_next_page_url(url):
    html = url_open(url).decode()
    a = html.find('current-comment-page') + 23
    b = html.find(']', a)
    c = html.find('<a href=', b) + 9
    if c -b != 94:
        return None
    d = html.find('">', c)
    return html[c:d]

def find_imgs(url):
    html = url_open(url).decode()
    img_addrs = []

    a = html.find('img src=')

    while a != -1:
        b = html.find('.jpg', a, a+255)

        if b != -1:
            img_addrs.append(html[a+9:b+4])
        else:
            b = a + 9

        a = html.find('img src=', b)

    return img_addrs


def save_imgs(folder, img_addrs):
    for each in img_addrs:
        filename = each.split('/')[-1]
        with open(filename, 'wb')as f:
            img = url_open('http:' + each)
            f.write(img)


def download_imgs(folder='imgs'):
    os.mkdir(folder)
    os.chdir(folder)
    # os.chdir() 方法用于改变当前工作目录到指定的路径。

    url = "http://jandan.net/ooxx/"
    all_imgs = []
    
    img_adds = find_imgs(url)
    print(img_adds)
    all_imgs.extend(img_adds)
    while get_next_page_url(url):
        url = "http:" + get_next_page_url(url)
        img_adds = find_imgs(url)
        print(img_adds)
        all_imgs.extend(img_adds)
    save_imgs(folder, all_imgs)
    return all_imgs

if __name__ == '__main__':
    download_imgs()

# url = "http://jandan.net/ooxx/"http://wx4.sinaimg.cn/large/0076BSS5ly1gia7d0h5l2j30u0190drq.jpg
# html = url_open(url)
# a = html.find('current-comment-page') + 23
# b = html.find(']', a)
# c = html.find('<a href=', b) + 9
# d = html.find('">', c)
# a,b,c,d,c-b
# get_next_page_url(url)
# find_imgs(url)
```

    # 运行结果



```python
# Xpath 爬取
import requests   #倒入requests库
from lxml import etree   #倒入lxml 库（没有这个库，pip install lxml安装）
url = "http://jandan.net/ooxx/"  #请求地址
headers = {
        "User-Agent": "Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/54.0.2840.99 Safari/537.36"
    }
response = requests.get(url= url, headers=headers)   #返回结果
wb_data = response.text   #文本展示返回结果
html = etree.HTML(wb_data)   #将页面转换成文档树
b = html.xpath('//*[@id="comments"]/ol/li//p/img/@src')  
print(b)   #打印b，这里的b是一个数组
# print(b[0]) #打印b的第一项数据
```

    ['//wx3.sinaimg.cn/mw600/006v1hQCgy1fygmyw3m14j30zk1hcali.jpg', '//wx1.sinaimg.cn/mw600/006v1hQCgy1fygmywfs3pj30iz0sg0vp.jpg',  '//wx1.sinaimg.cn/mw600/0076BSS5ly1gia6zhj9ggj30tm18gwis.jpg']


## 课后练习
### 完成百度翻译接口的爬取
### 完成煎蛋网图片的爬取（尝试不同方法）


```python
# 使用beautifulsoup爬取

import requests
import os
from bs4 import BeautifulSoup

headers = { "User-Agent": "Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/54.0.2840.99 Safari/537.36"}

response = requests.get('http://jandan.net/ooxx/',headers=headers).text
bs = BeautifulSoup(response,'lxml')
bs_imgs = bs.find_all('img')
for bs_img in bs_imgs:
    img_url = bs_img['src']
    print(img_url)
```

###### 下节课招聘网站爬虫实战
- **lesson1 python爬虫基础**
- lesson2 招聘网站爬虫实战
- lesson3 数据可视化项目实战
