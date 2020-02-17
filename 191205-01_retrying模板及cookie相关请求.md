### 使用超时参数
- requests.get(url,headers=headers,timeout=3) #3秒之内必须返回响应，否则会报错


### retrying模块的学习
- pip install retrying
```python
from retrying import retry
@retry(stop_max_attempt_number=3)   #反复执行3次
def fun1():
  print("this is fun1")
  raise ValueError("this is test error")

- 例子：
```python
from retrying import retry
import requests
url = "..."
headers = {....}
@retry(stop_max_attempt_number=3)  #让被装饰的函数反复执行三次，三次全部报错才会报错，中间有一次成功则继续往下走
def _parse_url(url):
  response = requests.get(url,headers=headers)
  retrun response.content.decode()
def parse_url(url):
    try:
      html_str = _parse_url(url)
    except:
      html_str = None
    return html_str

### 处理cookie相关的请求

- 人人网{"email":"mr_mao_hacker@163.com",
  "password":"alarmchime"}

- 直接携带cookie请求url地址
 - 1.cookie放在headers中
 - 模拟登录人人网
```python
url = "https://http://www.renren.com/973018917/newsfeed/photo"
headers = {"user_agent":"...",
            "cookie":"..."}
response = requests.get(url,headers=headers)
with open("rencent.html","w",encoding="utf-8") as f:
  f.write(response.content.decode())

  - 2.cookie字典(将cookie写成字典的形式)
  -例：
 cookie_dict = {iguan.split("=")[0]:i.split("=")[-1] for i in cookie.split(";")}

- 先发送post请求，获取cookie，带上cookie请求登录后的页面
 - 1.session = requests.session() #session具有的方法和requests一样
 - 2.session.post(url,data,headers) #服务器设置在本地的cookie会被保存在session
 - 3.session.get(url) #会带上之前保存在session中的cookie，则能够请求成功
```python
#实例化session
session = requests.session()
#使用session发送post请求，获取对方的cookie
post_url = ""
headers = {}
post_data = {}
session.post(post_url,headers=headers,data=post_data)
#再使用session请求登录后的页面
url = ""
response = session.get(url,headers=headers)
with open("12.html","w") as f:
  f.write(response.content.decode())
