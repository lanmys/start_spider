# 认识http，https
- http:超文本传输协议
 - 以明文的形式传输
 - 效率更高，但是不安全

- https：http + ssl（安全套接字层）
 - 传输数据之前先加密，后解密获取内容
 - 效率较低，但是安全

- get请求和post请求的区别
 - get请求没有请求体，post有。则get请求把数据放在url地址中
 - post请求常用于登陆注册
 - post请求携带的数据量比get请求大，多，常用于传输大文本的时候

- http协议之请求
  - 1.请求行
  - 2.请求头
   - User-Agent：用户代理：对方服务器能够通过知道当前请求对方按的是神，额浏览器
   - 如果我们需要模拟手机版的模拟器发送请求，那么我们需要将user_agent改成手机版
   - Upgrade-Insecure-Request:1 --表示将http协议改成https协议
   - accept:表示客户端接收什么样的数据
   - accept-Encoding:表示接收什么样的编码数据
   - accept-Language:表示接收什么样的语言
   + 例：accept:text/html,application/xhtml+xml,application/xml;q=0.9,image/webp,image/apng,*/*;q=0.8,表示服务器更加愿意接收text/html的数据，其次是image...
   - (Cookie):就是缓存，用来存储用户信息的，每次请求会被携带上发送给对方的浏览器
    - 要请求需要登录的网站，这时需要处理cookie；
    - 登录的服务器也会根据cookie来判断我们是否是一个爬虫
  -3.请求体：携带数据
   - get请求没有请求体，则get请求把数据放在url地址中
   - post请求有请求体，post请求常用于登陆注册，传输大文本的时候，因为post请求携带的数据量比get请求大，多；

- http协议之响应
 - 1.响应头
  - Set-Cookie： 对方服务器通过该字段设置cookie到本地
 - 2.响应体
  - url地址对应的响应
  - cookie：主要关注name和value
- 抓包就是用于查看服务器使用的是哪个请求

## requests模块的学习

### 使用前安装
   - pip install requests

###  发送get，post请求，获取响应
   - response = requests.get(url) #发送get请求，请求url地址对应的响应
   - 例：
      url = "http://www.baidu.com"
      response = requests.get(url)
      print(response)
      -->> <response[200]>(注意：python中用<>括起来的一般表示的是class)
   - response = requests.post(url,data={请求体的字典}) #发送post请求
   - 例:
     url = "http://fanyi.baidu.com/basetrans"
     query_string = {"query":"人生苦短，我用python",
              "from":"zh",
              "to":"en"}

     response = requests.post(url,data=query_string)
     #print(response)
     response.Encoding = 'utf-8'
     print(response.text)

### response的方法
- response.text : 是requests模块根据响应头部做出的推测解码
  - 该方法往往会出现乱码，出现乱码使用response.encoding="utf-8"
 - reponse.content.decode()
  - 把响应的二进制字节流转化为str类型，获取网页的html字符串

 - response.request.url  #发送请求的url地址
 - response.url  #response响应的url地址
 - response.request.headers  #请求头
 - response.headers  #响应头

### 获取网页源码的正确打开方式
 - 1.respons.content.decode()  #首先使用这个
 - 2.response.content.decode("gdk") #其次使用这个
 - 3.response.text #最后使用这个（前面使用response.encoding = "utf-8"）




### 发送带header的请求(当发现前面添加的信息不足时，需要多的添加headers)
 - 为了模拟浏览器，获取和浏览器一模一样的内容
 - headers = {"User-Agent":"...."，
               "...":"..."}
 - response = resquests.post(url,data=query_string,headers=headers)
