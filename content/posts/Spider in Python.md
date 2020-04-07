---
title: 'Spider in Python'
date: 2019-11-21 06:00:00
tags: ["Spider"]
categories: ["Python"]
toc: true
published: true
hideInList: false
feature: 
isTop: false
---
There are some ways to use spider, for example, request, bs4...
<!--more-->
# Request
## 7 Main functions in requests
- `requests.request()` generate a request, basic function
- `requests.get()` Get the html
- `requests.head()` Get the head of html
- `requests.post()` Post a request to website
- `requests.put()` Put a requests
- `requests.patch()` Modify the website
- `requests.delete()` delete the website
## requests.request(method, url, **kwargs)
- method means get, head, post....
- kwargs: 控制访问的参数，均为可选项
1. params: 字典或字符序列，增加的url
```
kv = {'key1': 'value1', 'key2':'value2'}
r = requests.request('GET', 'http://python123.io/ws', params=kv)
print(r.url)
```
The result is `https://python123.io/ws?key1=value1&key2=value2`
2. data:字典或字符序列或文件对象， 作为Request的内容
```
kv = {'key1': 'value1', 'key2':'value2'}
r = requests.request('GET', 'http://python123.io/ws', data=kv)
print(r.url)
```
3. JSON: JSON 格式的数据， 作为request的内容
4. heasers: 字典， http定制头
```
hd = {'user-agent':'Chrome/10'}
r = requests.request('POST','http://python123.io/ws', headers = hd)
```
5. files: dict, transfer file
```
fs = {'file':open('data.xls','rb')}
r = requests.request('POST', 'http://python123.io/ws', files = fs)
```
6. timeout: set time when get a website, if it doesnot response in set time, it will have a exception
7. proxies: dict, set proxy vps
8. allow_redirects: True/False, 重定向
9. stream: true/false, 获取内容立即下载
# Practice
## JD get
```
url = 'https://item.jd.com/43223278294.html'
try:
    r = requests.get(url)
    r.raise_for_status()  //if code = 200,its ok. Otherwise, exception
    r.encoding = r.apparent_encoding
    print(r.text[:1000])
except:
    print(Exception!)
```
## Baidu post
```
url = "http://www.baidu.com"
kv = {'wd':'蔡徐坤'}
try:
    r = request.post(url,params = kv)
    r.raise_for_status
    r.encoding = r.apparent_encoding
    print(r.text[:1000])
except:
    print("Exception")
```
# Beautisul soup
## basic code
```
from bs4 import BeautifulSoup
soup = BeautiuflSoup("<html>data<html>", "html.parser")
```
## Beautiful Soup 库解析器
- bs4 Html: BeautifulSoup(data,html.parser)
- lxml Html: BeautifulSoup(data,"lxml") `pip3 install lxml`
- lxml Xml: BeautifulSoup(data,"xml")  `pip3 install lxml`
- html5lib: BeautifulSoup(data,"html5lib") `pip3 install html5lib`
## 基本元素
- Tag: <>xxx</>
- Name: the name of tag, the name of <p>,,,</p> is 'p', format: <tag>.name
- Attributes: <tag>.attrs
- NavigableString: 非属性string, format: <tag>.string
- Comment: special comment
## 遍历
- 下行遍历
1. `.content` : 子节点列表， 将<tag>所有儿子节点存入列表 eg.`soup.body.content`
2. `.children`: 子节点的迭代类型，与content类似， 用于循环遍历儿子节点
3. `descendants`: 遍历所有子孙节点
- 上行遍历
1. `.parent`: 节点的父亲标签
2. `.parents`: 循环遍历先辈节点
- 平行遍历
1.  `.next_sibing`: 返回下一个平行节点标签
2. `.previous_sibing`: 返回上一个平行节点标签
3. `.next_sibings`: 遍历后续所有平行标签
4. `.previous_sibings`: 遍历所有前边平行节点
##  Find information
`<>.find_all(name,attrs,recursive,string,**kwargs)`==`<>()`
返回一个列表类型，存储查找的结果
1. name: 对a标签查找，查找所有： soup.find_all['a','b']
2. attrs:对属性查找
3. recursive: 是否对子孙节点搜索
4. string: search string
## 爬取大学排名
```
import requests
from bs4 import BeautifulSoup
import bs4

def getHtml(url):
    r = requests.get(url,timeout = 30)
    r.raise_for_status()
    r.encoding = r.apparent_encoding
    return r.text

def fillList(list, html):
    soup = BeautifulSoup(html, "html.parser")
    for tr in soup.find('tbody').children:
        if isinstance(tr, bs4.element.Tag):
            tds = tr('td')
            list.append([tds[0].string, tds[1].string, tds[4].string])

def printList(list,num):
    print("{:^10}\t{:^6}\t{:^10}".format("排名","学校","分数"))
    for i in range(num):
        u = list[i]
        print("{:^10}\t{:<6}\t{:>10}".format(u[0],u[1],u[2]))

def main():
    list = []
    url = "http://www.zuihaodaxue.com/ARWU2019.html"
    html = getHtml(url)
    fillList(list,html)
    printList(list,100)

main()
```
# Re库基本使用
-  `re.search()`在一个字符串中搜素匹配正则表达式的第一个位置，返回match对象
    re.search(pattern,string,flags = 0)
    1. pattern: 正则表达式的字符串或原生字符串表示 
    2. string:待匹配字符串
    3. flags: 正则表达式使用时的控制标记
    `re.I`:忽略正则表达式大小写
    `re.M`正则表达式中的^能够将给定的字符串的每行当作匹配开始
    `re.S`正则表达式中的.匹配除换行外的所有字符
-  `re.match()`从一个字符串的开始位置起匹配正则表达式，返回match对象
    属性
    1. `.string`:待匹配的文本
    2. `.re`匹配时使用的pattern对象
    3. `pos`正则表达式搜索文本的开始位置
    4. `endpos`正则表达式搜索文本的结束位置
    方法
    1. `.group(0)`:获取匹配后的字符串
    2. `.start()`:匹配字符串在原始字符串的开始位置
    3. `.end()`：匹配字符串在原始字符串的结束位置
    4. `.span()`：返回(.start().end())
-  `re.findall()`搜索字符串中以列表类型返回全部能匹配的字串
-  `re.split()`将一个字符串按照正则表达式匹配结果进行分割，返回列表类型
-  `re.finditer`搜索字符串，返回一个匹配结果的迭代类型，每个迭代元素是match对象
-  `re.sub()`在一个字符串中替换所有匹配正则表达式的字串，返回替换后的字符串
- 贪婪匹配
例子：
```
match = re.search(r'PY.*N', 'PYANBNCNDN')
match.group(0)
```
result is `PYANBNCNDN`
最小匹配： 加？`r'PY.*?N'`
# Scrapy
Scrapy 常用命令
- `startproject<name>[dir]`创建一个新工程
- `genspider[options]<name><domin>` 创建一个新爬虫
- `settings[options]`获取爬虫配置信息
- `crawel <spider>` run a spider
- `list` list all spider in this project
- `shell`启用url调试命令行
yield：冻结，执行
```
def gen(num):
    for i in range(num):
        yield i**2
for i in gen(6):
    print(i,"",end="")
```
结果0 1 4 9 16 25 
# xpath
xpath 是一种在xml文档查找信息的语言
## 概念
### 节点（node）
元素，属性，文本，命名空间，文档（根）节点
### 节点关系
父(parent)
children
sibling
ancestor
descentant
## 语法
| 表达式 |    描述 |
nodename	选取此节点的所有子节点。
/	        从根节点选取。
//	        从匹配选择的当前节点选择文档中的节点，而不考虑它们的位置。
.	        选取当前节点。
..	        选取当前节点的父节点。
@	        选取属性。
comment = result.xpath('//span[@class = "short"]/text()') . 读取内容

