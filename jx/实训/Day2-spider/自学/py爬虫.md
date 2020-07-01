# py爬虫

- [py爬虫](#py爬虫)
- [requests](#requests)
  - [发送请求](#发送请求)
    - [传递url参数](#传递url参数)
    - [响应内容](#响应内容)
    - [自定义请求头](#自定义请求头)
    - [更加复杂的 POST 请求](#更加复杂的-post-请求)
    - [状态码](#状态码)
  - [Cookie](#cookie)
  - [timeout](#timeout)
  - [重定向](#重定向)
- [bs4](#bs4)
  - [对象](#对象)
    - [Tag](#tag)
    - [Name](#name)
    - [Attr](#attr)
  - [查找节点](#查找节点)
    - [.contents 和 .children](#contents-和-children)
    - [父节点](#父节点)
    - [兄弟节点](#兄弟节点)
  - [正则表达式查找节点](#正则表达式查找节点)
  - [通过函数查找节点](#通过函数查找节点)
  - [find_all()](#find_all)
    - [按css搜索](#按css搜索)
  - [其他的查找函数](#其他的查找函数)
  - [css选择器](#css选择器)

# requests

## 发送请求
```python
import request
req = request.get("http://www.baidu.com")
```

### 传递url参数
```python
payload = {'key1': 'value1', 'key2': 'value2'}
r = requests.get("http://httpbin.org/get", params=payload)
print(r.url)
# http://httpbin.org/get?key2=value2&key1=value1
```
**注意字典里值为 None 的键都不会被添加到 URL 的查询字符串里。**
```python
payload = {'key1': 'value1', 'key2': ['value2', 'value3']}
r = requests.get('http://httpbin.org/get', params=payload)
print(r.url)
# http://httpbin.org/get?key1=value1&key2=value2&key2=value3
```
也可以传入一个列表

### 响应内容
```python
import requests
r = requests.get('https://api.github.com/events')
r.text      # 响应数据
r.content   # 二进制响应数据
r.encoding  # 编码方式
r.json()    # json格式的响应数据
r.raw       # 原生响应方式
```

### 自定义请求头
```python
url = 'https://api.github.com/some/endpoint'
headers = {'user-agent': 'my-app/0.0.1'}

r = requests.get(url, headers=headers)
```

### 更加复杂的 POST 请求
```python
>>> payload = {'key1': 'value1', 'key2': 'value2'}
>>> r = requests.post("http://httpbin.org/post", data=payload)
>>> print(r.text)
{
  ...
  "form": {
    "key2": "value2",
    "key1": "value1"
  },
  ...
}
```
多个元素使用统一key
```python
>>> payload = (('key1', 'value1'), ('key1', 'value2'))
>>> r = requests.post('http://httpbin.org/post', data=payload)
>>> print(r.text)
{
  ...
  "form": {
    "key1": [
      "value1",
      "value2"
    ]
  },
  ...
}
```
自动编码为json
```python
>>> url = 'https://api.github.com/some/endpoint'
>>> payload = {'some': 'data'}
>>> r = requests.post(url, json=payload)
```

### 状态码
```python
>>> r = requests.get('http://httpbin.org/get')
>>> r.status_code
200
```
内置的状态码查询对象：`requests.code.ok  # 200`

提交异常
```python
r.raise_for_status() # status_code 为200时为None
```

## Cookie
使用 cookies 参数提交cookie
```python
>>> url = 'http://httpbin.org/cookies'
>>> cookies = dict(cookies_are='working')

>>> r = requests.get(url, cookies=cookies)
>>> r.text
'{"cookies": {"cookies_are": "working"}}'
```

## timeout
```python
>>> requests.get('http://github.com', timeout=0.001)
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
requests.exceptions.Timeout: HTTPConnectionPool(host='github.com', port=80): Request timed out. (timeout=0.001)
```

## 重定向
默认允许重定向
```python
>>> r = requests.get('http://github.com')

>>> r.url
'https://github.com/'

>>> r.status_code
200

>>> r.history
[<Response [301]>]
```
禁止重定向
```python
>>> r = requests.get('http://github.com', allow_redirects=False)
>>> r.status_code
301
>>> r.history
[]
```

# bs4

## 对象

### Tag
```python
soup = BeautifulSoup('<b class="boldest">Extremely bold</b>')
tag = soup.b
type(tag)
# <class 'bs4.element.Tag'>
```

### Name
```python
tag.name
# u'b'
```

### Attr
一个tag可能有很多个属性. tag <b class="boldest"> 有一个 “class” 的属性,值为 “boldest” . tag的属性的操作方法与字典相同:
```python
tag['class']
# u'boldest'
```
获取属性的字典
```python
tag.attrs
# {u'class': u'boldest'}
```
**tag的属性的操作方法与字典相同!!!**

## 查找节点
```python
import requests
from bs4 import BeautifulSoup
req = requests("https://www.baidu.com")
soup = BeautifulSoup(req.text)
soup.a # 第一个a标签
soup.div # 第一个div标签
soup.find_all('a') # 查找所有的a标签
```

### .contents 和 .children
tag的 .contents 属性可以将tag的子节点以列表的方式输出:
```python
head_tag = soup.head
head_tag
# <head><title>The Dormouse's story</title></head>

head_tag.contents
[<title>The Dormouse's story</title>]

title_tag = head_tag.contents[0]
title_tag
# <title>The Dormouse's story</title>
title_tag.contents
# [u'The Dormouse's story']
```
通过tag的 .children 生成器,可以对tag的子节点进行循环:
```python
for child in title_tag.children:
    print(child)
    # The Dormouse's story
```

### 父节点
- .parent
    > 当前的一个父节点
    ```python
    title_tag = soup.title
    title_tag
    # <title>The Dormouse's story</title>
    title_tag.parent
    # <head><title>The Dormouse's story</title></head>
    ```
- .parents
    > 所有父节点（一直到跟节点）（生成器）
    ```python
    link = soup.a
    link
    # <a class="sister" href="http://example.com/elsie" id="link1">Elsie</a>
    for parent in link.parents:
        if parent is None:
            print(parent)
        else:
            print(parent.name)
    # p
    # body
    # html
    # [document]
    # None
    ```

### 兄弟节点
- .next_sibling 和 .previous_sibling
    ```python
    for sibling in soup.a.next_siblings:
        print(repr(sibling))
        # u',\n'
        # <a class="sister" href="http://example.com/lacie" id="link2">Lacie</a>
        # u' and\n'
        # <a class="sister" href="http://example.com/tillie" id="link3">Tillie</a>
        # u'; and they lived at the bottom of a well.'
        # None

    for sibling in soup.find(id="link3").previous_siblings:
        print(repr(sibling))
        # ' and\n'
        # <a class="sister" href="http://example.com/lacie" id="link2">Lacie</a>
        # u',\n'
        # <a class="sister" href="http://example.com/elsie" id="link1">Elsie</a>
        # u'Once upon a time there were three little sisters; and their names were\n'
        # None
    ```

## 正则表达式查找节点
```python
import re
for tag in soup.find_all(re.compile("^b")):
    print(tag.name)
# body
# b
```

## 通过函数查找节点
```python
def has_class_but_no_id(tag):
    return tag.has_attr('class') and not tag.has_attr('id')

soup.find_all(has_class_but_no_id)
# [<p class="title"><b>The Dormouse's story</b></p>,
#  <p class="story">Once upon a time there were...</p>,
#  <p class="story">...</p>]
```

## find_all()
```python
find_all( name , attrs , recursive , string , **kwargs )
```
### 按css搜索
```python
soup.find_all("a", class_="sister")
# [<a class="sister" href="http://example.com/elsie" id="link1">Elsie</a>,
#  <a class="sister" href="http://example.com/lacie" id="link2">Lacie</a>,
#  <a class="sister" href="http://example.com/tillie" id="link3">Tillie</a>]
```

## 其他的查找函数
- `find()`
- `find_parents()` & `find_parent()`
- `find_next_siblings()` & `find_next_sibling()`
- `find_previous_siblings()` & `find_previous_sibling()`
- `find_all_next()` & `find_next()`
- `find_all_previous()` & `find_previous()`

## css选择器
```python
soup.select()
```