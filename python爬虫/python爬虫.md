# python爬虫

## 1.页面结构的介绍

2、HTML介绍
1、什么是HTML
HTML是 HyperText Mark-up Language 的首字母简写，意思是超文本标记语言。

通过HTML标记（标签）对网页中的文本、图片、多媒体等内容进行描述。

说明：

“超文本”：不仅能承载简单的文字、还能包含超链接、图片、音频、视频等。

“标记语言”：标记语言是由一套标记标签组成的。

2、HTML文档——网页
HTML文档也被称为网页

后缀名.html

文件名格式： 主文件名.后缀名

创建HTML文档

1）新建一个后缀名为.html的文件

2）添加基本结构：英文状态下!回车

3) 输入HTML：5

3、标记（标签）
构成网页的基本单位

标签：由尖括号括起来的关键词

单标签：<标签名 >或 <标签名 />

双标签：<开始标签名>[内容]</结束标签名>

元素：标签及内容的整体

属性

<标签名 属性名1="属性值1"  属性名2="属性值2"></标签名>
<后面的第一个单词叫做标签的名字，标签名空格之后的叫做标签的属性。

属性由属性名和属性值组成，属性名和属性值用等号连接

属性值用引号引起来。 多个属性之间用空格隔开。

4、HTML注释
注释即对代码的解释和说明，不会被浏览器解析执行

注释内容不会出现在网页中，只是对代码的一个说明

语法

<!-- html注释内容 -->
HTML中的注释以`<!--`开头，以`-->`结束，开始和结束中间为注释内容。
ctrl + /

alt + shift + a: 可以在一行代码的后面进行注释

5、HTML文档的基本结构

<!DOCTYPE html>
<!-- 
    <!doctype> 文件类型定义DTD 
    作用：告诉浏览器该文档的版本信息，让浏览器解析器知道使用哪种语法解析文档
    文档第一代码是HTML5标准网页声明，告知浏览器用HTML5标准解析此网页。
    不是标签，是声明语句
    必须写在HTML文档的第一行
-->
<html lang="en">
<!-- 
 网页的根元素 
 定义整个HTML文档，包含head和body

  lang属性
- 作用：定义当前文档显示文字的语言
- 语法：lang=“en”
  (lang是language的简写)
- 取值:
  en定义语言为英语
  zh-CN定义语言为中文   -->

<head>
    <!--
网页的头部信息 其内容不会显示在网页中
定义文档的头部，包含文档的标题（title），可以包含文档脚本（script），样式（style），meta信息以及更多的其他信息。
-->
    <meta charset="UTF-8">
    <!-- 
文档字符集
字符集(Character set)是多个字符的集合，便于计算机识别和存储各种文字。
在<head>标签内,通过<meta> 标签的 charset 属性来规定 HTML 文档应该使用哪种字符编码。
            charset属性:设置编码方式
            UTF-8：万国码，通用性较好
(2)常用的字符集
- UTF-8被称为万国码，包含全世界所有国家需要用到的字符
- GB2312简单中文，包括6763个汉字
- GBK包含全部中文字符，是GB2312的扩展，加入对繁体字的支持，兼容GB2312
- BIG5繁体中文，港澳台等用
        -->
    <title>标题</title>
    <!--
网页标题
添加到收藏夹时的标题显示在搜索引擎结果中的页面标题。
-->
</head>
<body>
    <!-- 网页的主体内容     定义文档的主体，在浏览器窗口中可以看到的所有内容都包含在它内部。-->
    父子关系——嵌套关系
    兄弟关系——并列关系
</body>
</html>

一.html标签
整个网页从<html>开始，到<html>结束。


二.head标签
不需要掌握
此标签内定义的内容在浏览器中不可见。

表1  <head>内部标签

<head>内部标签	说明
<title>	定义网页标题
<meta>	定义网页的基本信息（供搜索引擎）
<style>	定义CSS样式
<link>	链接外部CSS文件或脚本文件
<script>	定义脚本语言

三.body标签
用于定义网页展示内容


1.段落标签
表1  段落标签
标签	语义	说明
<h1>~<h6>	header	标题
<p>	paragraph	段落
<br>	break	换行
<hr>	horizontal rule	水平线
<div>	division	分割（块元素）
<span>	span	区域（行内元素）
2.文本标签
表2  文本标签
标签	语义	说明
```html
<strong>	strong	加粗
<i>	italic	斜体标签
<em>	emphasized（强调）	斜体
<cite>	cite（引用）	斜体
<sup>	superscripted	上标
<sub>	subscripted	下标
<b>	boid	加粗显示
<del>	delete	删除线
<bdo>	设置文本的方向	通过属性dir=“ltr” left to 		  right “rtl” right to left从右至左
<abr>	设置文字的缩写	通过title属性设置当鼠标停留在		 文字上时显示的提示 内容
<ins>	下划线	
<small>	相对于当前文字的字号小一号	
<big>	相当于当前文字的字号大一号
```

2）标签的分类
①一般标签：开始符号和结束符号均有。这之间可以插入其他标签或者文字

②自闭合标签：只有开始符号，不插入其他标签或者文字，只能定义自身的属性。
如：<br/>、<hr/>


（3）HTML元素分类
HTML元素根据浏览器表现形式分为两类：①块元素；②行内元素

①块元素：独占一行、其内部可以容纳其他块元素或行内元素。

如：<div>、<p>、<h1>~<h6>、<br>、<ol>、<ul>

②行内元素（内联元素）：在浏览器中可以与其它行内元素共占一行，只有当多个元素的总宽度大于浏览器的宽度时，才会换行显示。

如：<a>、<span>、<strong>、<b>、<em>、<i>、<img>、<input>、<select>

4.列表标签
表4   列表标签
标签	语义	说明

```html
<ul>	unordered list	无序列表
<ol>	ordered list	有序列表
<dl>	definition list	定义列表
```

**http协议**

服务器和客户端进行数据交互的一种形式

**常用请求头信息**

User-Agent：请求载体的身份标识

Connection：请求完毕后，是断开还是保持连接

**常用响应头信息**

Content-Type：服务器响应客户端的数据类型

**https协议**

安全的超文本传输协议

**加密方式**

对称密钥加密

非对称密钥加密

证书密钥加密

**UA伪装**

UA：User-Agent(请求载体的身份标识)

门户网站的服务器会监测对应请求的载体身份标识，如果检测到请求的载体身份标识为某一款浏览器，那么就说明该请求是一个正常的请求。但是如果检测到请求的载体身份标识不是为某一款浏览器的，则表示该请求为不正常的请求(爬虫)，则服务器端就很有可能拒绝该次请求。

## 2.爬虫相关概念

### 1.爬虫的解释

1.通过一个程序，根据url进行爬取网页，获取有用信息

2.使用程序模拟浏览器，去向服务器发送请求，获取响应信息

### 2.爬虫核心

1.爬取网页：爬取整个网页，包含网页中所有的内容

2.解析数据：将网页中你得到的数据进行解析

3.难点：爬虫与反爬虫之间的博弈

### 3.爬虫分类

1.通用爬虫

2.聚焦爬虫

设计思路：

1.确定要爬取的url

2.模拟浏览器通过http协议访问url，获取服务器返回的html代码

3.解析html字符串

### 4.反爬手段

1.User-Agent

2.代理IP

3.验证码访问

4.动态加载网站

5.数据加宽

### 5.urllib库使用

![image-20240808222418159](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240808222418159.png)

#### 5.1 urllib基本使用

```python
#使用urllib来获取百度首页的源码
import urllib.request

#定义一个url
url = "http://www.baidu.com"
#模拟浏览器向服务器发生请求
response = urllib.request.urlopen(url)
#获取响应中的页面的源码
#read方法：返回的是字节形式的二进制数据
#我们要将二进制的数据转换为字符串
#二进制 --》字符串 解码 decode('编码的格式‘)
content = response.read().decode('utf-8')
#打印数据
print(content)
```

#### 5.2 一个类型和六个方法

```python
import urllib.request

url = 'http://www.baidu.com'
#模拟浏览器发送请求
resopnse = urllib.request.urlopen(url)

# 一个类型和六个方法
#resopnse是HTTPResponse的类型
print(type(resopnse))
# 按照一个字节一个字节的去读
#content = resopnse.read()
#print(content)
#括号里面的5指的是返回5个字节
#content = resopnse.read(5)
#print(content)
#读取一行
#content = resopnse.readline()
#print(content)
#读取到结束
#content = resopnse.readlines()
#print(content)
# 返回状态码 如果是200了，那么证明我们的逻辑没有错
print(resopnse.getcode())
# 返回url地址
print(resopnse.geturl())
# 获取的状态信息
print(resopnse.getheaders())
```

#### 5.3 urllib下载

```python
import urllib.request

#下载网页
#url_page = 'http://www.baidu.com'
#url代表的是下载的路径 filename文件的名字
#在python中可以写变量的名字，也可以直接写值
#urllib.request.urlretrieve(url=url_page, filename='baidu.html')
#下载图片
#url_img = 'https://tse3-mm.cn.bing.net/th/id/OIP-C.whSJWoFAmXAVHwuWzFVTPQHaJQ?rs=1&pid=ImgDetMain'
#urllib.request.urlretrieve(url=url_img, filename='lisa.jpg')
#下载视频
url_video = 'http://www.baidu.com/link?url=sskNEBWgOyIV742RnLA-DRN6UWx56rtrtEpCTYWcOxKJOwO28oepaAEVlvEUX3Z9wGwDXdvgMR8ta8fA8O0aUu3-5S2kD-76DaUj196hHje'
urllib.request.urlretrieve(url=url_video, filename='vedio.mp4')
```

### 6.请求对象的定制

![image-20240810221704929](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240810221704929.png)

```python
import urllib.request

url = 'https://www.baidu.com'
# url的组成
#https://www.baidu.com/s?wd=%E5%91%A8%E6%9D%E4%BC%A6
# http/https  www.baidu.com     80/443    s   wd = Lisa   #
#    协议         主机            端口号    路径   参数      锚点
# http 80
# https 443
# MySQL 3306
# Oracle 1521
# redis 6379
# mongodb 17017
headers = {
     'User-Agent':'Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/127.0.0.0 Safari/537.36 Edg/127.0.0.0'
}
#请求对象的定制
request = urllib.request.Request(url, headers=headers)
response = urllib.request.urlopen(request)
content = response.read().decode('utf-8')
print(content)
```

### 7.编解码

#### 7.1 urllib_get请求的quote方法

get请求方式：urllib.parse.quote()

![image-20240811221357017](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240811221357017.png)

代码实现：

```python
import urllib.request
import urllib.parse
#需求 获取https://www.baidu.com/s?wd=周杰伦的网页源码
url = 'https://www.baidu.com/s?wd='
#请求对象的定制是为了解决反爬的第一中手段
headers = {
    'User-Agent':'Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/127.0.0.0 Safari/537.36 Edg/127.0.0.0'
}
#要将周杰伦三个字变成Unicode编码的形式
#我们需要依赖于urllib.parse
name = urllib.parse.quote('周杰伦')
url = url + name
#请求对象的定制
request = urllib.request.Request(url, headers=headers)
#模拟浏览器向服务器发送请求
response = urllib.request.urlopen(request)
#获取响应的内容
content = response.read().decode('utf-8')
#打印数据
print(content)
```

#### 7.2 urllib_get请求的urlencode方式

get请求方式：urllib.parse.urlencode()

代码实现：

```python
import urllib.parse
import urllib.request
#urlencode应用场景：多个参数时
#https://www.baidu.com/s?wd=周杰伦&sex=男

#data = {
#    'wd':'周杰伦',
#    'sex':'男',
#    'location':'中国台湾省'
#}
#a = urllib.parse.urlencode(data)
#print(a)

#获取网页源码
base_url = 'https://www.baidu.com/s?'
data = {
    'wd':'周杰伦',
    'sex':'男',
    'location':'中国台湾省'
}
new_data = urllib.parse.urlencode(data)
#请求资源路径
url = base_url + new_data
headers ={
    'User-Agent':'Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/127.0.0.0 Safari/537.36 Edg/127.0.0.0'
}
#请求对象的定制
request = urllib.request.Request(url=url,headers=headers)
#模拟浏览器向服务器发送请求
response = urllib.request.urlopen(request)
#获取网页源码的数据
content = response.read().decode('utf-8')
#打印数据
print(content)
```

#### 7.3 post请求方式

Python中的POST请求是HTTP协议中的一种请求方法，用于向服务器提交数据。与GET请求不同，POST请求将数据封装在请求体中，而不是在URL中传递。通常情况下，POST请求用于向服务器提交表单数据、上传文件等操作。

1.post请求

```py
import urllib.request
import urllib.parse
#post请求
url = 'http://fanyi.baidu.com/sug'
headers = {
    'User-Agent':'Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/127.0.0.0 Safari/537.36 Edg/127.0.0.0'
}
data = {
    'kw':'spider'
}
# post请求的参数 必须要进行编码
data = urllib.parse.urlencode(data).encode('utf-8')
request = urllib.request.Request(url=url, data=data, headers = headers)
# 模拟浏览器向服务器发送请求
response = urllib.request.urlopen(request)
#获取响应数据
content = response.read().decode('utf-8')
#字符串 --> json对象
import json
obj = json.loads(content)
print(obj)
```

新反爬手段：cookie

### 8.ajax的get请求

#### 8.1 获取豆瓣电影的第一页

```py
# get请求
# 获取豆瓣电影的第一页数据，并保存起来
import urllib.request
url = 'https://movie.douban.com/j/chart/top_list?type=5&interval_id=100%3A90&action=&start=0&limit=20'

headers = {
    'User-Agent':'Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/127.0.0.0 Safari/537.36 Edg/127.0.0.0'
}

# (1)请求对象的定制
request = urllib.request.Request(url, headers=headers)
# (2)获取响应的数据
response = urllib.request.urlopen(request)
content = response.read().decode('utf-8')
# (3)数据下载到本地
# open方法默认情况下使用的是gbk的方法
# fp = open('douban.json','w',encoding='utf-8')
# fp.write(content)
with open('douban.json','w',encoding='utf-8') as fp:
    fp.write(content)
```

#### 8.2 获取豆瓣电影的前十页

```py
# https://movie.douban.com/j/chart/top_list?type=5&interval_id=100%3A90&action=&start=0&limit=20
# https://movie.douban.com/j/chart/top_list?type=5&interval_id=100%3A90&action=&start=20&limit=20
# https://movie.douban.com/j/chart/top_list?type=5&interval_id=100%3A90&action=&start=40&limit=20
# page  1   2   3   4
# start 0   20  40  60
# start = (page-1)*20
import urllib.parse
import urllib.request
import ssl
context = ssl._create_unverified_context()
def create_request(page):
    base_url = 'https://movie.douban.com/j/chart/top_list?type=5&interval_id=100%3A90&action=&'
    params = {
        'start': (page - 1) * 20,
        'limit': 20
    }
    url = base_url + urllib.parse.urlencode(params)
    headers = {
        'User-Agent': 'Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/127.0.0.0 Safari/537.36 Edg/127.0.0.0'
    }

    request = urllib.request.Request(url=url, headers=headers)
    return request


def get_content(request,context):
    response = urllib.request.urlopen(request,context=context)
    content = response.read().decode('utf-8')
    return content


def down_load(page, content):
    with open("douban_page_" + str(page) + ".json", 'w', encoding='utf-8') as fp:
        fp.write(content)


# 程序入口
if __name__ == '__main__':
    start_page = int(input("起始的页码: "))
    end_page = int(input("结束的页码: "))
    for page in range(start_page, end_page + 1):
        request = create_request(page)
        content = get_content(request,context)
        down_load(page, content)
```

### 9.ajax的post请求

#### 9.1 post请求获取麦当劳信息

```py
# https://www.kfc.com.cn/kfccda/ashx/GetStoreList.ashx?op=cname
# post请求
# cname: 南充
# pid:
# pageIndex: 1
# pageSize: 10
# 第二页
# cname: 南充
# pid:
# pageIndex: 2
# pageSize: 10
import urllib.request
import urllib.parse
# base_url = 'https://www.kfc.com.cn/kfccda/ashx/GetStoreList.ashx?op=cname'
def create_request(page):
    base_url = 'https://www.kfc.com.cn/kfccda/ashx/GetStoreList.ashx?op=cname'
    data = {
        'cname': '南充',
        'pid':'',
        'pageIndex': page,
        'pageSize': 10
    }
    data = urllib.parse.urlencode(data).encode('utf-8')
    headers = {
        'User-Agent': 'Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/127.0.0.0 Safari/537.36 Edg/127.0.0.0'
    }
    request = urllib.request.Request(base_url, data, headers)
    return request
def get_content(request):
    response = urllib.request.urlopen(request)
    content = response.read().decode('utf-8')
    return content
def down_load(content,page):
    with open('kfccda'+str(page)+'.json', 'w',encoding='utf-8') as fp:
        fp.write(content)
if __name__ == '__main__':
    start_page = int(input("起始页码："))
    end_page = int(input("终止页码："))
    for page in range(start_page, end_page+1):
        #请求对象的定制
        request = create_request(page)
        #获取网页源码
        content = get_content(request)
        #下载
        down_load(content,page)
```

### 10.URLError\HTTPError

简介:

1.HTTPError类是URLError类的子类 

2.导入的包urllib.error.HTTPError urllib.error.URLError 

3.http错误：http错误是针对浏览器无法连接到服务器而增加出来的错误提示。引导并告诉浏览者该页是哪里出 了问题。 

4.通过urllib发送请求的时候，有可能会发送失败，这个时候如果想让你的代码更加的健壮，可以通过try‐ except进行捕获异常，异常有两类，URLError\HTTPError

代码实现：

```py
import urllib.request
url = 'https://blog.csdn.net/sulixu/article/details/1198189491'

headers = {
    'User-Agent': 'Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/127.0.0.0 Safari/537.36 Edg/127.0.0.0'
}

try:
    request = urllib.request.Request(url, headers=headers)
    response = urllib.request.urlopen(request)
    content = response.read().decode('utf-8')
    print(content)
except urllib.error.HTTPError:
    print('HTTPError')
```

### 11.微博的cookie登录

refer和cookie一般都加上

代码实现：

```py
# 适用的场景：数据采集的时候，需要绕过登录，然后进入到某个页面
# 个人信息页面是utf-8 但是还报错了编码错误，因为并没有进入到个人信息页面，而是跳转到登录页面
# 那么登录页面不是utf-8，所有报错

# 什么情况下访问不成功
# 因为请求头的信息不够，所以访问不成功
import urllib.request
#url = "https://weibo.com/"
#headers = {
    #'user-agent':'Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/127.0.0.0 Safari/537.36 Edg/127.0.0.0',
    #'cookie':'PC_TOKEN=57cff4c61a; XSRF-TOKEN=rk5VxA-ZFuZvvO8-QqNShNxp; SCF=AoboNi6rD7dstxjnz7VrZ-9eIrxxDM5r21tD3-hXgQYYmf3osFKuj7fQuiUzLHqxKLbkmAJl85JQ--OTNk_EGGs.; SUB=_2A25Lun58DeRhGeFG41IS8y7Oyj6IHXVotv-0rDV8PUNbmtAbLVHEkW9NeNDCD2PLJaiBIH_RSi58tYLgjXo6ZoJV; SUBP=0033WrSXqPxfM725Ws9jqgMF55529P9D9WF.aXPxOedpHjGfE0RMz8ZF5NHD95QN1hn7e0e7eo2EWs4DqcjVi--4iK.Ri-isi--fi-zNi-zXi--4iK.Ri-isi--fi-zNi-zXS0nRehe0ehzpentt; ALF=02_1726323500; WBPSESS=CYIR4M6H9b6mrX29pMW6j_HMjGgb7gJo6bzGIxpUQhfLRlooQAPg4PzfkSrFnsHVA_JUtGmzUnTT3QmEGZRt8EModqXVVa_dysLHo5SwqAdDw73we_kJnvb8ecZmPAWXaEZWiCpafFOPgYVcQ5tjfA==',
    #'referer':'https://weibo.com/newlogin?tabtype=weibo&gid=102803&openLoginLayer=0&url='
#}
#request = urllib.request.Request(url, headers=headers)
#response = urllib.request.urlopen(request)
#content = response.read().decode('gb2312')
#with open('cookie.txt','w',encoding='gb2312') as f:
#    f.write(content)

#第二种方法
url = "https://weibo.com/"
headers = {
    'user-agent':'Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/127.0.0.0 Safari/537.36 Edg/127.0.0.0',
    'cookie':'PC_TOKEN=57cff4c61a; XSRF-TOKEN=rk5VxA-ZFuZvvO8-QqNShNxp; SCF=AoboNi6rD7dstxjnz7VrZ-9eIrxxDM5r21tD3-hXgQYYmf3osFKuj7fQuiUzLHqxKLbkmAJl85JQ--OTNk_EGGs.; SUB=_2A25Lun58DeRhGeFG41IS8y7Oyj6IHXVotv-0rDV8PUNbmtAbLVHEkW9NeNDCD2PLJaiBIH_RSi58tYLgjXo6ZoJV; SUBP=0033WrSXqPxfM725Ws9jqgMF55529P9D9WF.aXPxOedpHjGfE0RMz8ZF5NHD95QN1hn7e0e7eo2EWs4DqcjVi--4iK.Ri-isi--fi-zNi-zXi--4iK.Ri-isi--fi-zNi-zXS0nRehe0ehzpentt; ALF=02_1726323500; WBPSESS=CYIR4M6H9b6mrX29pMW6j_HMjGgb7gJo6bzGIxpUQhfLRlooQAPg4PzfkSrFnsHVA_JUtGmzUnTT3QmEGZRt8EModqXVVa_dysLHo5SwqAdDw73we_kJnvb8ecZmPAWXaEZWiCpafFOPgYVcQ5tjfA==',
    'referer':'https://weibo.com/newlogin?tabtype=weibo&gid=102803&openLoginLayer=0&url='
}
request = urllib.request.Request(url, headers=headers)
response = urllib.request.urlopen(request)
content = response.read().decode('utf-8')
with open('cookie.txt','w',encoding='utf-8') as f:
    f.write(content)
```

### 12.Handler处理器

为什么要学习handler？

urllib.request.urlopen(url) 

不能定制请求头 

urllib.request.Request(url,headers,data) 

可以定制请求头 

Handler 

定制更高级的请求头（随着业务逻辑的复杂 请求对象的定制已经满足不了我们的需求（动态cookie和代理 不能使用请求对象的定制）

代码实现：

```py
# 需求：使用Handler来访问百度  获取网页源码

import urllib.request
url = 'http://www.baidu.com'
headers = {
    'User-Agent': 'Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/127.0.0.0 Safari/537.36 Edg/127.0.0.0'
}
request = urllib.request.Request(url, headers=headers)

# handler build_opener open
# (1)获取handler对象
handler = urllib.request.HTTPHandler()
# (2)获取opener对象
opener = urllib.request.build_opener(handler)
# (3)调用open方法
response = opener.open(request)

content = response.read().decode('utf-8')
print(content)
```

### 13.代理服务器

1.代理的常用功能? 

​	1.突破自身IP访问限制，访问国外站点。 

​	2.访问一些单位或团体内部资源 

​	扩展：某大学FTP(前提是该代理地址在该资源的允许访问范围之内)，使用教育网内地址段免费代理服务 器，就可以用于对教育网开放的各类FTP下载上传，以及各类资料查询共享等服务。 

​	3.提高访问速度 

​	扩展：通常代理服务器都设置一个较大的硬盘缓冲区，当有外界的信息通过时，同时也将其保存到缓冲 区中，当其他用户再访问相同的信息时， 则直接由缓冲区中取出信息，传给用户，以提高访问速度。 

​	4.隐藏真实IP 

​	扩展：上网者也可以通过这种方法隐藏自己的IP，免受攻击。 

2.代码配置代理 

​	创建Reuqest对象 

​	创建ProxyHandler对象 

​	用handler对象创建opener对象 

​	使用opener.open函数发送请求

```py
import urllib.request
url = 'https://www.baidu.com/s?wd=ip'
headers = {
    'User-Agent': 'Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/127.0.0.0 Safari/537.36 Edg/127.0.0.0'
}
# 请求对象的定制
request = urllib.request.Request(url=url,headers=headers)
# 模拟浏览器访问服务器
#response = urllib.request.urlopen(request)
proxies = {
    'http':'121.230.211.142:3256'
}
handler = urllib.request.ProxyHandler(proxies=proxies)
opener = urllib.request.build_opener(handler)
response = opener.open(request)
# 获取响应的信息
content = response.read().decode('utf-8')
# 保存
with open('daili.html','w',encoding='utf-8') as fp:
    fp.write(content)
```

### 14.代理池

```py
import urllib.request
proxies_pool = [
    {'http':'121.230.211.142:3256'},
    {'http':'121.230.211.142:3256'},
]

import random
proxies = random.choice(proxies_pool)
url = 'https://www.baidu.com/s?wd=ip'
headers = {
    'User-Agent': 'Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/127.0.0.0 Safari/537.36 Edg/127.0.0.0'
}
request = urllib.request.Request(url=url,headers=headers)
handler = urllib.request.ProxyHandler(proxies=proxies)
opener = urllib.request.build_opener(handler)
response = opener.open(request)
content = response.read().decode('utf-8')
with open('daili2.html','w',encoding='utf-8') as fp:
    fp.write(content)
```

## 3.解析

### 1.xpath

xpath使用： 

注意：提前安装xpath插件 

（1）打开chrome浏览器 

（2）点击右上角小圆点 

（3）更多工具 

（4）扩展程序 

（5）拖拽xpath插件到扩展程序中 

（6）如果crx文件失效，需要将后缀修改zip 

（7）再次拖拽 

（8）关闭浏览器重新打开 

（9）ctrl + shift + x 

（10）出现小黑框 

1.安装lxml库 pip install lxml ‐i https://pypi.douban.com/simple 

2.导入lxml.etree from lxml import etree

 3.etree.parse() 解析本地文件 

html_tree = etree.parse('XX.html') 

4.etree.HTML() 服务器响应文件 

html_tree = etree.HTML(response.read().decode('utf‐8') 

4.html_tree.xpath(xpath路径)

**xpath基本语法：**

```py
1.路径查询
//：查找所有子孙节点，不考虑层级关系
/ ：找直接子节点
2.谓词查询
//div[@id]
//div[@id="maincontent"]
3.属性查询
//@class
4.模糊查询
//div[contains(@id, "he")]
//div[starts‐with(@id, "he")]
5.内容查询
//div/h1/text()
6.逻辑运算
//div[@id="head" and @class="s_down"]
//title | //price
```

**代码实现：**

```py
from lxml import etree
# xpath解析
# （1）解析本地文件
# （2）解析服务器响应的数据 response.read().decode('utf-8'
# xpath解析本地文件
tree = etree.parse('C:\\Users\\冯煜炜\\PycharmProjects\\python数据分析\\xpath的基本使用.html')
print(tree)

#tree.xpath('xpath路径')

#查找所有有id的属性的li标签
#li_list = tree.xpath('//li[@id]')
#查找id为1的li标签
#li_list = tree.xpath('//li[@id="l1"]/text()')
#查找ul下面的li
#li_list = tree.xpath('//body/ul/li')
#查找到id为l1的li标签的class的属性值
#li_list = tree.xpath('//li[@id="l1"]/@class')
#查询id中包含l的li标签
#li_list = tree.xpath('//li[contains(@id,"l1")]/text()')
#查询id的值以l开头的li标签
#li_list = tree.xpath('//li[starts-with(@id,"c")]/text()')
#查询id为l1和class为c1的
#li_list = tree.xpath('//li[@id="l1" and @class="c1"]/text()')
li_list = tree.xpath('//li[@id="l2"]/text()| //li[@id ="l1"]/text()')
print(li_list)
print(len(li_list))
```

### 2.xpath获取百度的百度一下

代码实现：

```py
#（1）获取网页的源码
#（2）解析
#（3）打印
import urllib.request
url = 'https://www.baidu.com/'
headers = {
'User-Agent': 'Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/127.0.0.0 Safari/537.36 Edg/127.0.0.0'
}
request = urllib.request.Request(url, headers=headers)
response = urllib.request.urlopen(request)
content = response.read().decode('utf-8')
#print(content)
# 解析网页源码
from lxml import etree
tree = etree.HTML(content)
#xpath的返回值是一个列表
result = tree.xpath('//*[@id="su"]/@value')[0]
print(result)
```

### 3.jsonpath

只能解析本地文件

```py
jsonpath的安装及使用方式：
pip安装：
	pip install jsonpath
jsonpath的使用：
	obj = json.load(open('json文件', 'r', 	encoding='utf‐8'))
	ret = jsonpath.jsonpath(obj, 'jsonpath语法')

```

jsonpath的使用：

```py
import json

import jsonpath

obj = json.load(open('package.json', 'r', 	encoding='utf‐8'))
#print(obj)
# 书店所有的作者
#author_list = jsonpath.jsonpath(obj, '$.store.book[*].author')
#print(author_list)
# 所有作者
#author_list = jsonpath.jsonpath(obj, '$..author')
#print(author_list)
# store下面的所有的元素
#a_list = jsonpath.jsonpath(obj,'$.store.*')
#print(a_list)
# store里面所有东西的price
#price_list = jsonpath.jsonpath(obj, '$..price')
#print(price_list)
# 第三本书
#book=jsonpath.jsonpath(obj, '$..book[2]')
#print(book)
# 最后一本书
#book = jsonpath.jsonpath(obj, '$..book[(@.length-1)]')
#print(book)
# 前面的两本书
#book_list = jsonpath.jsonpath(obj, '$..book[0,1]')
#book_list = jsonpath.jsonpath(obj, '$..book[:2]')
#print(book_list)
# 条件过滤
# 过滤所有包含isbn的书
#book_list = jsonpath.jsonpath(obj,'$..book[?(@.isbn)]')
#print(book_list)
# 哪本书超过了10块钱
book_list = jsonpath.jsonpath(obj,'$..book[?(@.price>10)]')
print(book_list)
```

### 4.jsonpath解析淘票票

```py
import urllib.request

url = 'https://www.taopiaopiao.com/cityAction.json?city=&_ksTS=1723889634235_19&jsoncallback=jsonp20&action=cityAction&n_s=new&event_submit_doLocate=true'
headers = {
    'accept':'text/javascript, application/javascript, application/ecmascript, application/x-ecmascript, */*; q=0.01',
    'cookie':'cna=s1tHHy8euAECAW69DZKFP+Ms; xlly_s=1; dnk=; t=5cff2d5edd64b695d058fa54bcbb8a11; lgc=; sn=; _tb_token_=31e6771e8eb5b; cookie2=136c71bf73c0ce686401512cd0737890; _nk_=; isg=BNjYchhLCns59Cb_rwphA04YqQZqwTxLd5Jj7xLLGpPkrXyXutFS279O5OWdmvQj',
    'referer':'https://www.taopiaopiao.com/?tbpm=3',
'sec-ch-ua-mobile':
'?0',
'sec-fetch-dest':
'empty',
'sec-fetch-mode':
'cors',
'sec-fetch-site':
'same-origin',
'user-agent':
'Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/127.0.0.0 Safari/537.36 Edg/127.0.0.0',
'x-requested-with':
'XMLHttpRequest'
}
request = urllib.request.Request(url=url,headers=headers)
response = urllib.request.urlopen(request)
content = response.read().decode('utf-8')
content = content.split('(')[1].split(')')[0]
print(content)
with open('package.json','w',encoding='utf-8') as fp:
    fp.write(content)
import json
import jsonpath
obj = json.load(open('package.json','r',encoding='utf-8'))
city_list = jsonpath.jsonpath(obj,'$..name')
print(city_list)
```

### 5.BeautifulSoup

#### 1.基本简介

```py
1.BeautifulSoup简称：
	bs4
2.什么是BeatifulSoup？
	BeautifulSoup，和lxml一样，是一个html的解析器，主要功能也是解析和提取数据
3.优缺点？
	缺点：效率没有lxml的效率高
	优点：接口设计人性化，使用方便
```

#### 2.安装以及创建

```py
1.安装
	pip install bs4
2.导入
	from bs4 import BeautifulSoup
3.创建对象
	服务器响应的文件生成对象
		soup = BeautifulSoup(response.read().decode(), 'lxml')
	本地文件生成对象
		soup = BeautifulSoup(open('1.html'), 'lxml')
		注意：默认打开文件的编码格式gbk所以需要指定打开编码格式
```

#### 3.节点定位

```py
1.根据标签名查找节点
soup.a 【注】只能找到第一个a
soup.a.name
soup.a.attrs
2.函数
(1).find(返回一个对象)
find('a')：只找到第一个a标签
find('a', title='名字')
find('a', class_='名字')
(2).find_all(返回一个列表)
find_all('a') 查找到所有的a
find_all(['a', 'span']) 返回所有的a和span
find_all('a', limit=2) 只找前两个a
(3).select(根据选择器得到节点对象)【推荐】
1.element
eg:p
2..class
eg:.firstname
3.#id
eg:#firstname
4.属性选择器
[attribute]
eg:li = soup.select('li[class]')
[attribute=value]
eg:li = soup.select('li[class="hengheng1"]')
5.层级选择器
element element
div p
element>element
div>p
element,element
div,p
eg:soup = soup.select('a,span')
```

#### 4.节点信息

```py
(1).获取节点内容：适用于标签中嵌套标签的结构
obj.string
obj.get_text()【推荐】
(2).节点的属性
tag.name 获取标签名
eg:tag = find('li)
print(tag.name)
tag.attrs将属性值作为一个字典返回
(3).获取节点属性
obj.attrs.get('title')【常用】
obj.get('title')
obj['title']
```

代码实现:
```py
from bs4 import BeautifulSoup
# 通过解析本地文件，来将bs4的基础语法进行讲解
# 默认打开的文件编码格式是gbk，所以在打开文件的时候需要指定编码
soup = BeautifulSoup(open("bs4的使用.html",encoding='utf-8'),'lxml')
# 根据标签名查找节点
# 找到的是第一个符合条件的数据
#print(soup.a)
# 获取标签的属性表和属性值
#print(soup.a.attrs)

#bs4的一些函数
#1.find
#找到的是第一个符合条件的数据
#print(soup.find('a'))

#根据title的值来找到对应的标签对象
#print(soup.find('a',title='a2'))

#根据class的值来找到对应的标签对象，注意的是class需要添加下划线
#print(soup.find('a',class_='a1'))

#2.find_all 返回的是一个列表，并且返回了所有的a标签
#print(soup.find_all('a'))
#如果想要获得的是多个标签的数据，那么需要在find_all的参数中添加的是列表的数据
#print(soup.find_all(['a','span']))
#limit的作用是查找前几个数据
#print(soup.find_all('li',limit=2))

#3.select
#select方法返回的是一个列表，并且返回的是多个数据
#print(soup.select('a'))
#可以通过.代表class，我们把这种操作叫做类选择器
#print(soup.select('.a1'))

#print(soup.select('#l1'))

#属性选择器 通过属性寻找对应的标签
#查找到li标签中有id的标签
#print(soup.select('li[id]'))

#查找到li标签中id为l2的标签
#print(soup.select('li[id="l2"]'))

#层级选择器
# 后代选择器
# 找到的是div下面的li
#print(soup.select('div li'))
# 子代选择器
# 某标签的第一级子标签
# 注意：很多计算机编程语言中，如果不加空格不输出内容，但是在bs4中，不会报错，会显示内容
#print(soup.select('div > ul > li'))
# a标签和li标签的所有的对象
#print(soup.select('a,li'))

#节点信息
#获取节点内容
#obj = soup.select('#d1')[0]
#如果标签对象中只有内容，那么string和get_text()都可以使用
#如果标签对象中，除了内容还有标签，那么string就获取不到数据，而get_text()是可以获取数据
#推荐使用get_text()
#print(obj.string)
#print(obj.get_text())

#节点的属性
#obj = soup.select('#p1')[0]
#name是标签的名字
#print(obj.name)
#将属性值作为一个字典返回
#print(obj.attrs)

#获取节点的属性
obj = soup.select('#p1')[0]
#print(obj.attrs.get('class'))
#print(obj.get('class'))
print(obj['class'])
```

### 6.爬取星巴克的数据

代码实现：

```py
import urllib.request
url = 'https://www.starbucks.com.cn/menu/'
response = urllib.request.urlopen(url)
content = response.read().decode('utf-8')
from bs4 import BeautifulSoup
soup = BeautifulSoup(content, 'lxml')
name_list = soup.select('ul[class="grid padded-3 product"]')
for name in name_list:
    print(name.string)
```

## 4.Selenium

### 1.Selenium

```py
1.什么是selenium？
（1）Selenium是一个用于Web应用程序测试的工具。
（2）Selenium 测试直接运行在浏览器中，就像真正的用户在操作一样。
（3）支持通过各种driver（FirfoxDriver，IternetExplorerDriver，OperaDriver，ChromeDriver）驱动
真实浏览器完成测试。
（4）selenium也是支持无界面浏览器操作的。
```

```py
2.为什么使用selenium？
模拟浏览器功能，自动执行网页中的js代码，实现动态加载
```

```py
3.如何安装selenium？
（1）操作谷歌浏览器驱动下载地址
http://chromedriver.storage.googleapis.com/index.html
（2）谷歌驱动和谷歌浏览器版本之间的映射表
http://blog.csdn.net/huilan_same/article/details/51896672
（3）查看谷歌浏览器版本
谷歌浏览器右上角‐‐>帮助‐‐>关于
（4）pip install selenium
```

```py
4.selenium的使用步骤？
（1）导入：from selenium import webdriver
（2）创建谷歌浏览器操作对象：
path = 谷歌浏览器驱动文件路径
browser = webdriver.Chrome(path)
（3）访问网址
url = 要访问的网址
browser.get(url)
```

```py
4‐1：selenium的元素定位？
元素定位：自动化要做的就是模拟鼠标和键盘来操作来操作这些元素，点击、输入等等。操作这些元素前首先
要找到它们，WebDriver提供很多定位元素的方法
方法：
1.find_element_by_id
eg:button = browser.find_element_by_id('su')
2.find_elements_by_name
eg:name = browser.find_element_by_name('wd')
3.find_elements_by_xpath
eg:xpath1 = browser.find_elements_by_xpath('//input[@id="su"]')
4.find_elements_by_tag_name
eg:names = browser.find_elements_by_tag_name('input')
5.find_elements_by_css_selector
eg:my_input = browser.find_elements_by_css_selector('#kw')[0]
6.find_elements_by_link_text
eg:browser.find_element_by_link_text("新闻")
```

```py
4‐2:访问元素信息
获取元素属性
.get_attribute('class')
获取元素文本
.text
获取标签名
.tag_name
```

```py
4‐3:交互
点击:click()
输入:send_keys()
后退操作:browser.back()
前进操作:browser.forword()
模拟JS滚动:
js='document.documentElement.scrollTop=100000'
browser.execute_script(js) 执行js代码
获取网页代码：page_source
退出：browser.quit()
```

### 2.Selenium的基本使用

```py
# 导入selenium
from selenium import webdriver
# 创建浏览器操作对象
path = 'chromedriver.exe'
browser = webdriver.Chrome(path)
# 访问网站
#url = 'https://www.baidu.com'
# 访问京东的网址
url = 'https://www.jd.com'
browser.get(url)
content = browser.page_source
print(content)
```

### 3.Selenium的元素

#### 3.1 元素定位

```py
from selenium import webdriver
path = "chromedriver.exe"
browser = webdriver.Chrome(path)
url = "https://www.baidu.com"
browser.get(url)
# 元素定位
#button = browser.find_element_by_id("su")
# 根据id来找到对象
#print(button)
# 根据标签属性的属性值来获取对象
#button = browser.find_element_by_name("wd")
#print(button)
# 根据xpath语句来获取对象
#button = browser.find_elements_by_xpath('//input[@id="su"]')
#print(button)
# 根据标签的名字来获取对象
#button = browser.find_elements_by_tag_name("input")
#print(button)
# 使用bs4的语法来获取对象
#button = browser.find_elements_by_css_selector("#su")
#print(button)
#
button = browser.find_elements_by_link_text('直播')
print(button)
```

#### 3.2 元素信息及交互

```py
from selenium import webdriver
path = "chromedriver.exe"
browser = webdriver.Chrome(path)
url = "http://www.baidu.com"
browser.get(url)

#input = browser.find_element_by_id('su')
# 获取标签的属性
#print(input.get_attribute('class'))
# 获取标签的名字
#print(input.tag_name)
#获取标签的文本
#a = browser.find_element_by_link_text("新闻")
#print(a.text)
#print(input.text)

#交互
import time
time.sleep(2)

#获取文本框的对象
input = browser.find_element_by_id("kw")
#在文本框中输入周杰伦
input.send_keys("周杰伦")
time.sleep(2)
#获取百度一下的按钮
button = browser.find_element_by_id("su")
#点击按钮
button.click()
time.sleep(2)
#滑到底部
js_botton = 'document.documentElement.scrollTop=100000'
browser.execute_script(js_botton)
time.sleep(2)
#获取下一页的按钮
next = browser.find_element_by_xpath('//a[@class="n"]')
#点击下一页
next.click()
time.sleep(2)
#回到上一页
browser.back()
time.sleep(2)
#回去
browser.back()
time.sleep(2)
#退出
browser.quit()
```

### 4.Phantomjs

```py
1.什么是Phantomjs？
（1）是一个无界面的浏览器
（2）支持页面元素查找，js的执行等
（3）由于不进行css和gui渲染，运行效率要比真实的浏览器要快很多
```

```py
2.如何使用Phantomjs？
（1）获取PhantomJS.exe文件路径path
（2）browser = webdriver.PhantomJS(path)
（3）browser.get(url)
扩展：保存屏幕快照:browser.save_screenshot('baidu.png')
```

代码实现：

```py
from selenium import webdriver
path = 'phantomjs.exe'
browser = webdriver.PhantomJS(path)
url = 'https://www.baidu.com'
browser.get(url)
browser.save_screenshot('baidu.png')
import time
time.sleep(2)

input = browser.find_element_by_id('kw')
input.send_keys('昆凌')
time.sleep(3)

browser.save_screenshot('kunling.png')
```



### 5.Chrome handless

Chrome-headless 模式， Google 针对 Chrome 浏览器 59版 新增加的一种模式，可以让你不打开UI界面的情况下 使用 Chrome 浏览器，所以运行效果与 Chrome 保持完美一致。

```py
1.系统要求：
Chrome
Unix\Linux 系统需要 chrome >= 59
Windows 系统需要 chrome >= 60
Python3.6
Selenium==3.4.*
ChromeDriver==2.31
```

```py
2.配置：
from selenium import webdriver
from selenium.webdriver.chrome.options import Options
chrome_options = Options()
chrome_options.add_argument('‐‐headless')
chrome_options.add_argument('‐‐disable‐gpu')
path = r'C:\Program Files (x86)\Google\Chrome\Application\chrome.exe'
chrome_options.binary_location = path
browser = webdriver.Chrome(chrome_options=chrome_options)
browser.get('http://www.baidu.com/')
```

```py
3.配置封装：
from selenium import webdriver
#这个是浏览器自带的 不需要我们再做额外的操作
from selenium.webdriver.chrome.options import Options
def share_browser():
	#初始化
	chrome_options = Options()
	chrome_options.add_argument('‐‐headless')
	chrome_options.add_argument('‐‐disable‐gpu')
	#浏览器的安装路径 打开文件位置
	#这个路径是你谷歌浏览器的路径
	path = r'C:\Program Files (x86)\Google\Chrome\Application\chrome.exe'
	chrome_options.binary_location = path
	browser = 	webdriver.Chrome(chrome_options=chrome_options)
	return browser
封装调用：
from handless import share_browser
browser = share_browser()
browser.get('http://www.baidu.com/')
browser.save_screenshot('handless1.png')
```

代码：

```py
from selenium import webdriver
from selenium.webdriver.chrome.options import Options
#封装的handless
def share_browser():
    chrome_options = Options()
    chrome_options.add_argument('‐‐headless')
    chrome_options.add_argument('‐‐disable‐gpu')
    # path是你自己的chrome浏览器的文件路径
    path = r'C:\Program Files\Google\Chrome\Application\chrome.exe'
    chrome_options.binary_location = path
    browser = webdriver.Chrome(chrome_options=chrome_options)
    return browser
browser = share_browser()
url = 'https://www.baidu.com'
browser.get(url)
browser.save_screenshot('baidu.png')
```

## 5.requests

### 1.基本使用

```py
1.文档：
官方文档
http://cn.python‐requests.org/zh_CN/latest/
快速上手
http://cn.python‐requests.org/zh_CN/latest/user/quickstart.html
```

```py
2.安装
pip install requests
```

```py
3.response的属性以及类型
	   类型       :	models.Response
	r.text       : 	 获取网站源码
	r.encoding   :	 访问或定制编码方式
	r.url 	     :	 获取请求的url
	r.content    :	 响应的字节类型
	r.status_code:	 响应的状态码
	r.headers    :	 响应的头信息
```

代码实现：

```py
import requests
url = 'https://www.baidu.com'
response = requests.get(url=url)
# 一个类型和六个属性
# Response类型
#print(type(response))
# 设置响应的编码形式
#response.encoding = 'utf-8'
# 已字符串的形式来返回网页的源码
#print(response.text)
# 返回url地址
#print(response.url)
# 返回的是二进制的数据
#print(response.content)
# 返回响应的状态码
#print(response.status_code)
# 返回的是响应头
print(response.headers)
```

### 2.get请求

```py
requests.get()
eg:
	import requests
	url = 'http://www.baidu.com/s?'
	headers = {
'User‐Agent': 'Mozilla/5.0 (Windows NT 10.0; WOW64) AppleWebKit/537.36 (KHTML,
like Gecko) Chrome/65.0.3325.181 Safari/537.36'
	}
	data = {
		'wd':'北京'
	}
	response = 			requests.get(url,params=data,headers=headers)
定制参数
	参数使用params传递
	参数无需urlencode编码
	不需要请求对象的定制
	请求资源路径中？可加可不加
```

代码实现：

```py
# urllib
# (1)一个类型和六个方法
# (2)get请求
# (3)post请求
# (4)ajax的get请求
# (5)ajax的post请求
# (6)cookie登录
# (7)代理

#requests
# (1)一个类型以及六个属性
# (2)get请求
# (3)post请求
# (4)代理
# (5)cookie 验证码

#get请求
import requests
from lxml import etree
url = 'https://www.baidu.com/s?'
headers = {
     'User-Agent':'Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/127.0.0.0 Safari/537.36 Edg/127.0.0.0'
}
data = {
    'wd':'北京'
}
# url 请求资源路径
# params 参数
# kwargs 字典
response = requests.get(url=url, data=data,headers=headers)
content = response.text
print(content)

# 参数使用params
# 参数无需urlencode编码
# 不需要请求对象的定制
```

### 3.post请求

```py
requests.post()
百度翻译:
eg:
import requests
post_url = 'http://fanyi.baidu.com/sug'
headers={
'User‐Agent': 'Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36
(KHTML, like Gecko) Chrome/68.0.3440.106 Safari/537.36'
}
data = {
'kw': 'eye'
}
r = requests.post(url = post_url,headers=headers,data=data)
```

```py
6：get和post区别？
1： get请求的参数名字是params post请求的参数的名字是data
2： 请求资源路径后面可以不加?
3： 不需要手动编解码
4： 不需要做请求对象的定制
```

代码实现：

```py
import requests
url = 'https://www.baidu.com/sug'
headers = {
     'User-Agent':'Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/127.0.0.0 Safari/537.36 Edg/127.0.0.0'
}
data = {
    'kw':'eye'
}
# url 请求地址
# data 请求参数
# kwargs 字典
response = requests.post(url, headers=headers, data=data)
content = response.text
import json
obj = json.loads(content,encoding='utf-8')
print(obj)
```

### 4.代理

```py
7：proxy定制
在请求中设置proxies参数
参数类型是一个字典类型
eg:
import requests
url = 'http://www.baidu.com/s?'
headers = {
'user‐agent': 'Mozilla/5.0 (Windows NT 10.0; WOW64) AppleWebKit/537.36 (KHTML,
like Gecko) Chrome/65.0.3325.181 Safari/537.36'
}
data = {
'wd':'ip'
}
proxy = {
'http':'219.149.59.250:9797'
}
r = requests.get(url=url,params=data,headers=headers,proxies=proxy)
with open('proxy.html','w',encoding='utf‐8') as fp:
fp.write(r.text)
```

代码实现：

```py
import requests
url = 'http://www.baidu.com/s?'
headers = {
     'User-Agent':'Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/127.0.0.0 Safari/537.36 Edg/127.0.0.0'
}
data = {
    'wd':'ip'
}
proxy = {
    'http':'212.129.251.55:16816'
}
response = requests.get(url=url,params=data,headers=headers,proxies=proxy)
content = response.text
with open('proxy.html','w',encoding='utf‐8') as fp:
    fp.write(content)
```

### 5.cookie定制

```py
8:cookie定制
应用案例：
（1）古诗文网（需要验证）
（2）云打码平台
用户登陆 actionuser action
开发者登陆 actioncode action
```

代码实现登录古诗文网站:

```py
import requests
# 通过登录，然后进入到主页面
# 通过找登录接口，我们发现登录的时候需要的参数很多
# 我们观察到code是一个可以变化的量
# 难点：(1)__VIEWSTATE __VIEWSTATEGENERATOR 一般情况看不到的数据 都是在页面的源码中
#      我们观察到这两个数据在页面的源码中 所以我们需要获取页面的源码 然后进行解析就可以获取了
#      (2)验证码
url = 'https://www.gushiwen.cn/user/login.aspx?from=http://www.gushiwen.cn/user/collect.aspx'
headers = {
    'user-agent':'Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/127.0.0.0 Safari/537.36 Edg/127.0.0.0'
}
# 获取页面的源码
response = requests.get(url=url, headers=headers)
content = response.text
# 解析页面源码 然后获取__VIEWSTATE __VIEWSTATEGENERATOR
from bs4 import BeautifulSoup
soup = BeautifulSoup(content, 'lxml')
# 获取__VIEWSTATE
viewstate = soup.select('#__VIEWSTATE')[0].attrs.get('value')
# 获取__VIEWSTATEGENERATOR
viewstategenerator = soup.select('#__VIEWSTATEGENERATOR')[0].attrs.get('value')
# 获取验证码图片
code = soup.select('#imgCode')[0].attrs.get('src')
code_url = 'https://so.gushiwen.cn'+code
#有坑
#import urllib.request
#urllib.request.urlretrieve(url=code_url, filename='code.jpg')
#requests里面有一个方法 session() 通过session的返回值 就能使用请求变成一个对象
session = requests.session()
# 验证码的url的内容
response_code = session.get(code_url)
content_code = response_code.content
with open('code.jpg','wb')as fp:
    fp.write(content_code)
# 获取了验证码的图片之后 下载到本地 然后观察验证码 观察之后 然后在控制台输入这个验证码 就可以将这个值给code参数 就可以登录
code_name = input('请输入你的验证码')
# 点击登录
url_post = 'https://www.gushiwen.cn/user/login.aspx?from=http://www.gushiwen.cn/user/collect.aspx'
data_post = {
    '__VIEWSTATE': viewstate,
    '__VIEWSTATEGENERATOR': viewstategenerator,
    'from':'http://so.gushiwen.cn/user/collect.aspx',
    'email':'595165358@qq.com',
    'pwd':'action',
    'code':code_name,
    'denglu':'登录'
}
response_text = session.post(url=url_post,headers=headers,data=data_post)
content = response_text.text
with open('gushiwen.html','w',encoding='utf-8') as fp:
    fp.write(content)
```

## 6.scrapy

### 1.scrapy

```py
（1）scrapy是什么？
	Scrapy是一个为了爬取网站数据，提取结构性数据而编写的应用框架。 可以应用在包括数据挖掘，信息处理
或存储历史数据等一系列的程序中。
```

```py
（2）安装scrapy：
	pip install scrapy
安装过程中出错：
	如果安装有错误！！！！
	pip install Scrapy
	building 'twisted.test.raiser' extension
	error: Microsoft Visual C++ 14.0 is required. Get it with "Microsoft Visual C++
	Build Tools":http://landinghub.visualstudio.com/visual‐cpp‐build‐tools
解决方案：
http://www.lfd.uci.edu/~gohlke/pythonlibs/#twisted
下载twisted对应版本的whl文件（如我的Twisted‐17.5.0‐cp36‐cp36m‐win_amd64.whl），cp后面是
python版本，amd64代表64位，运行命令：
pip install C:\Users\...\Twisted‐17.5.0‐cp36‐cp36m‐win_amd64.whl
pip install Scrapy
如果再报错
	python ‐m pip install ‐‐upgrade pip
如果再报错 win32
解决方法：
	pip install pypiwin32
再报错：使用anaconda
使用步骤：
	打开anaconda
	点击environments
	点击not installed
	输入scrapy
	apply
	在pycharm中选择anaconda的环境
```

#### 1.scrapy项目的创建以及运行

```py
1.创建scrapy项目：
	终端输入 scrapy startproject 项目名称
```

```py
2.项目组成：
	spiders
	__init__.py
	自定义的爬虫文件.py ‐‐‐》由我们自己创建，是实现爬虫核心功能的文件
	__init__.py
	items.py ‐‐‐》定义数据结构的地方，是一个继承自scrapy.Item的类
	middlewares.py ‐‐‐》中间件 代理
	pipelines.py ‐‐‐》管道文件，里面只有一个类，用于处理下载数据的后续处理
默认是300优先级，值越小优先级越高（1‐1000）
	settings.py ‐‐‐》配置文件 比如：是否遵守robots协议，User‐Agent定义等
```

```py
3.创建爬虫文件：
（1）跳转到spiders文件夹 cd 目录名字/目录名字/spiders
（2）scrapy genspider 爬虫名字 网页的域名
爬虫文件的基本组成：
	继承scrapy.Spider类
	name = 'baidu' ‐‐‐》 运行爬虫文件时使用的名字
	allowed_domains ‐‐‐》 爬虫允许的域名，在爬取的时候，如果不是此域名之下的url，会被过滤掉
	start_urls ‐‐‐》 声明了爬虫的起始地址，可以写多个url，一般是一个
	parse(self, response) ‐‐‐》解析数据的回调函数
	response.text ‐‐‐》响应的是字符串
	response.body ‐‐‐》响应的是二进制文件
	response.xpath()‐》xpath方法的返回值类型是selector列表
	extract() ‐‐‐》提取的是selector对象的是data
	extract_first() ‐‐‐》提取的是selector列表中的第一个数据
```

```py
4.运行爬虫文件：
	scrapy crawl 爬虫名称
	注意：应在spiders文件夹内执行
```

#### 2.scrapy架构组成

```py
（1）引擎 ‐‐‐》自动运行，无需关注，会自动组织所有的请求对象，分发给下载器
（2）下载器 ‐‐‐》从引擎处获取到请求对象后，请求数据
（3）spiders ‐‐‐》Spider类定义了如何爬取某个(或某些)网站。包括了爬取的动作(例
如:是否跟进链接)以及如何从网页的内容中提取结构化数据(爬取item)。 换句话说，Spider就是您定义爬取的动作及
分析某个网页(或者是有些网页)的地方。
（4）调度器 ‐‐‐》有自己的调度规则，无需关注
（5）管道（Item pipeline） ‐‐‐》最终处理数据的管道，会预留接口供我们处理数据
当Item在Spider中被收集之后，它将会被传递到Item Pipeline，一些组件会按照一定的顺序执行对Item的处理。
每个item pipeline组件(有时称之为“Item Pipeline”)是实现了简单方法的Python类。他们接收到Item并通过它执行
一些行为，同时也决定此Item是否继续通过pipeline，或是被丢弃而不再进行处理。
以下是item pipeline的一些典型应用：
1. 清理HTML数据
2. 验证爬取的数据(检查item包含某些字段)
3. 查重(并丢弃)
4. 将爬取结果保存到数据库中
```

#### 3.scrapy工作原理

![image-20240822162232710](../../../AppData/Roaming/Typora/typora-user-images/image-20240822162232710.png)

代码实现：

```py
import scrapy


class ExampleSpider(scrapy.Spider):
    name = 'car'
    allowed_domains = ['autohome.com.cn']
    start_urls = ['https://www.autohome.com.cn/price/brandid_15']

    def parse(self, response):
        name_list = response.xpath('//div[@class="main-title"]/a/text()')
        for name in name_list:
            print(name)
```

### 2.scrapy shell

```py
1.什么是scrapy shell？
Scrapy终端，是一个交互终端，供您在未启动spider的情况下尝试及调试您的爬取代码。 其本意是用来测试提取
数据的代码，不过您可以将其作为正常的Python终端，在上面测试任何的Python代码。
该终端是用来测试XPath或CSS表达式，查看他们的工作方式及从爬取的网页中提取的数据。 在编写您的spider时，该
终端提供了交互性测试您的表达式代码的功能，免去了每次修改后运行spider的麻烦。
一旦熟悉了Scrapy终端后，您会发现其在开发和调试spider时发挥的巨大作用。
```

```py
2.安装ipython
安装：pip install ipython
简介：如果您安装了 IPython ，Scrapy终端将使用 IPython (替代标准Python终端)。 IPython 终端与其他相
比更为强大，提供智能的自动补全，高亮输出，及其他特性。
```

```py
3.应用：（1）scrapy shell www.baidu.com
（2）scrapy shell http://www.baidu.com
(3) scrapy shell "http://www.baidu.com"
(4) scrapy shell "www.baidu.com"
语法：
（1）response对象：
response.body
response.text
response.url
response.status
（2）response的解析：
response.xpath() （常用）
使用xpath路径查询特定元素，返回一个selector列表对象
response.css()
使用css_selector查询元素，返回一个selector列表对象
获取内容 ：response.css('#su::text').extract_first()
获取属性 ：response.css('#su::attr(“value”)').extract_first()
（3）selector对象（通过xpath方法调用返回的是seletor列表）
extract()
提取selector对象的值
如果提取不到值 那么会报错
使用xpath请求到的对象是一个selector对象，需要进一步使用extract()方法拆
包，转换为unicode字符串
extract_first()
提取seletor列表中的第一个值
如果提取不到值 会返回一个空值
返回第一个解析到的值，如果列表为空，此种方法也不会报错，会返回一个空值
xpath()
css()
注意：每一个selector对象可以再次的去使用xpath或者css方法
```

### 3.yield

1. 带有 yield 的函数不再是一个普通函数，而是一个生成器generator，可用于迭代 
2. yield 是一个类似 return 的关键字，迭代一次遇到yield时就返回yield后面(右边)的值。重点是：下一次迭代 时，从上一次迭代遇到的yield后面的代码(下一行)开始执行
3. 简要理解：yield就是 return 返回一个值，并且记住这个返回的位置，下次迭代就从这个位置后(下一行)开始

代码实现：

```py
import scrapy


class DangSpider(scrapy.Spider):
    name = 'dang'
    allowed_domains = ['category.dangdang.com']
    start_urls = ['http://category.dangdang.com/']

    def parse(self, response):
        #piplines 下载数据
        #items 定义数据结构的
        #通俗的说就是你要下载的数据都有什么
        #src = //ul[@id="component_59"]/li//img/@src
        #alt = //ul[@id="component_59"]/li//img/@alt
        #price = //ul[@id="component_59"]/li//p[@class="price"]/span[1]/text()
        li_list = response.xpath('//ul[@id="component_59"]/li')
        for li in li_list:
            src = li.xpath('.//img/@data-original').extract_first()
            # 第一张图片跟后面的图片是不一样的
            if src:
                src = src
            else:
                src = li.xpath('.//img/@src').extract_first()
            name = li.xpath('.//img/@alt')
            price = li.xpath('//p[@class="price"]/span[1]/text()')
            print(src,name,price)
```

#### 1.管道封装

##### 1.dang.py

```py
import scrapy
from scrapy_dangdang.items import ScrapyDangdangItem

class DangSpider(scrapy.Spider):
    name = 'dang'
    allowed_domains = ['category.dangdang.com']
    start_urls = ['http://category.dangdang.com/']

    def parse(self, response):
        #piplines 下载数据
        #items 定义数据结构的
        #通俗的说就是你要下载的数据都有什么
        #src = //ul[@id="component_59"]/li//img/@src
        #alt = //ul[@id="component_59"]/li//img/@alt
        #price = //ul[@id="component_59"]/li//p[@class="price"]/span[1]/text()
        li_list = response.xpath('//ul[@id="component_59"]/li')
        for li in li_list:
            src = li.xpath('.//img/@data-original').extract_first()
            # 第一张图片跟后面的图片是不一样的
            if src:
                src = src
            else:
                src = li.xpath('.//img/@src').extract_first()
            name = li.xpath('.//img/@alt')
            price = li.xpath('//p[@class="price"]/span[1]/text()')
            book = ScrapyDangdangItem(src=src,name=name,price=price)
            #获取一个book就将book交给piplines
            yield book
```

##### 2.pipelines.py

```py
# Define your item pipelines here
#
# Don't forget to add your pipeline to the ITEM_PIPELINES setting
# See: https://docs.scrapy.org/en/latest/topics/item-pipeline.html


# useful for handling different item types with a single interface
from itemadapter import ItemAdapter

# 如果相使用管道的话，那么就必须在settings中开启管道
class ScrapyDangdangPipeline:
    def open_spider(self,spider):
        self.fp = open('book.json','w',encoding='utf-8')
    def process_item(self, item, spider):
        # 1.write方法必须是一个字符串 而不是其他对象
        # 2.w模式会每一个对象都打开一次文件，覆盖之前的内容
        #with open('book.json','a',encoding='utf-8') as fp:
            #fp.write(item)
        self.fp.write(str(item))
        return item
    def close_spider(self,spider):
        self.fp.close()
```

##### 3.item.py

```py
# Define here the models for your scraped items
#
# See documentation in:
# https://docs.scrapy.org/en/latest/topics/items.html

import scrapy


class ScrapyDangdangItem(scrapy.Item):
    # define the fields for your item here like:
    # name = scrapy.Field()
    src = scrapy.Field()
    name = scrapy.Field()
    price = scrapy.Field()
```

#### 2.多条管道开启

在piplines.py上加上

```py
import urllib.request
#多条管道开启
#  1.定义管道类
#  2.在setting中开启管道
# 'scrapy_dangdang.pipelines.DangDangDownLoadPipeline': 301
class DangDangDownLoadPipline:
    def process_item(self, item, spider):
        url = item.get('src')
        filename = './books'+item.get('name')+'.jpg'
        #urllib.request.urlretrieve(url=url,filename=filename)

        return item
```

#### 3.多页数据的下载

在 dang.py上

```py
import scrapy
from scrapy_dangdang.items import ScrapyDangdangItem

class DangSpider(scrapy.Spider):
    name = 'dang'
    allowed_domains = ['category.dangdang.com']
    start_urls = ['http://category.dangdang.com/']
    base_url = 'http://category.dangdang.com/pg'
    page = 1
    def parse(self, response):
        #piplines 下载数据
        #items 定义数据结构的
        #通俗的说就是你要下载的数据都有什么
        #src = //ul[@id="component_59"]/li//img/@src
        #alt = //ul[@id="component_59"]/li//img/@alt
        #price = //ul[@id="component_59"]/li//p[@class="price"]/span[1]/text()
        li_list = response.xpath('//ul[@id="component_59"]/li')
        for li in li_list:
            src = li.xpath('.//img/@data-original').extract_first()
            # 第一张图片跟后面的图片是不一样的
            if src:
                src = src
            else:
                src = li.xpath('.//img/@src').extract_first()
            name = li.xpath('.//img/@alt')
            price = li.xpath('//p[@class="price"]/span[1]/text()')
            book = ScrapyDangdangItem(src=src,name=name,price=price)
            #获取一个book就将book交给piplines
            yield book
            #每一页的爬取的业务逻辑全都是一样的，所有我们只需要将执行的那个页的请求再次调用parse方法就可以了
            if self.page < 100:
                self.page += 1
                url = self.base_url + str(self.page) + '-cp01.01.02.00.00.00.html'
                # 怎么去调用parse方法
                # url就是请求地址
                # callback是你要执行的那个函数，注意不要加()
                yield scrapy.Request(url=url,callback=self.parse)
```

### 4.Mysql

（1）下载（https://dev.mysql.com/downloads/windows/installer/5.7.html） 

（2）安装（https://jingyan.baidu.com/album/d7130635f1c77d13fdf475df.html）

### 5.pymysql的使用步骤

```py
1.pip install pymysql
2.pymysql.connect(host,port,user,password,db,charset)
3.conn.cursor()
4.cursor.execute()
```

### 6.CrawlSpider

```py
1.继承自scrapy.Spider
2.独门秘笈
CrawlSpider可以定义规则，再解析html内容的时候，可以根据链接规则提取出指定的链接，然后再向这些链接发
送请求
所以，如果有需要跟进链接的需求，意思就是爬取了网页之后，需要提取链接再次爬取，使用CrawlSpider是非常
合适的
```

```py
3.提取链接
链接提取器，在这里就可以写规则提取指定链接
scrapy.linkextractors.LinkExtractor(
allow = (), # 正则表达式 提取符合正则的链接
deny = (), # (不用)正则表达式 不提取符合正则的链接
allow_domains = (), # （不用）允许的域名
deny_domains = (), # （不用）不允许的域名
restrict_xpaths = (), # xpath，提取符合xpath规则的链接
restrict_css = () # 提取符合选择器规则的链接)
4.模拟使用
正则用法：links1 = LinkExtractor(allow=r'list_23_\d+\.html')
xpath用法：links2 = LinkExtractor(restrict_xpaths=r'//div[@class="x"]')
css用法：links3 = LinkExtractor(restrict_css='.x')
5.提取连接
link.extract_links(response)
```

```py
6.注意事项
【注1】callback只能写函数名字符串, callback='parse_item'
【注2】在基本的spider中，如果重新发送请求，那里的callback写的是 callback=self.parse_item 【注‐
‐稍后看】follow=true 是否跟进 就是按照提取连接规则进行提取
```

### 7.scrapy的post请求

```py
（1）重写start_requests方法：
def start_requests(self)
(2) start_requests的返回值：
scrapy.FormRequest(url=url, headers=headers, callback=self.parse_item, formdata=data)
url: 要发送的post地址
headers：可以定制头信息
callback: 回调函数
formdata: post所携带的数据，这是一个字典
```

### 8.代理

```py
（1）到settings.py中，打开一个选项
DOWNLOADER_MIDDLEWARES = {
'postproject.middlewares.Proxy': 543,
}
（2）到middlewares.py中写代码
def process_request(self, request, spider):
request.meta['proxy'] = 'https://113.68.202.10:9999'
return None
```

