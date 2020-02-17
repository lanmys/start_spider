# BeautifulSoup
- BeautifulSoup库：（bs4）
- from bs4 import BeautifulSoup(引入)
  基本元素：
  Tag：标签，<tag>
  Name：标签名字,<tag>.name
  Attributes：标签属性,<tag>.attrs
  NavigableString：标签内非属性字符串,<tag>.string
  Comment：标签内字符串的注释部分

- 例子：
```python
  r = requests.get(url）
  demo = r.text
  soup = BeautifulSoup(demo,'html.parser')
  soup.prettify()  #美化HTML
  soup.a   #显示<a>..</a>
  soup.a.attrs  #显示a标签的属性
```
<tag>(...)等价于<tag>.find_all(...)
soup(...)等价于soup.find_all(...)

## 方法
- <>.find_all(name,attrs,recursive,string,**kwargs):返回一个列表类型，存储查找的结果
- name:对标签名称的检索字符串；
- attrs:对标签属性值的检索字符串，可标注属性检索；，传入的是字典；
- recursive：是否对子孙全部检索，默认True
- string：对标签中字符串区域的检索字符串


## 同<>.find_all()的扩展方法：
- <>.find():搜索且只返回一个结果字符串类型
- <>.find_parents():在先辈节点中搜索，列表
- <>.find_parent():在先辈节点中返回一个结果，字符串
- <>.find_next_siblings():在后续平行节点 中搜索，返回列表类型
- <>.find_next_sibling():在后续平行节点中返回字符串
- <>.find_previous_siblings():在前序平行节点中搜索，反回列表
- <>.find_previous_sibling():在前序平行节点中返回结果，字符串类型

#### 标签树的下行遍历：
 - .contents:子节点的列表，将<tag>所有儿子节点存入列表
 - .children:子节点的迭代类型，与.contents类，用于循环遍历儿子节点
 - .descendants:子孙节点的迭代类型，包含所有子孙节点，用于循环遍历子孙节点

#### 标签树的上行遍历：
 - .parent:节点的父亲标签
 - .parents:节点先辈标签的迭代类型，用于循环遍历先辈节点

#### 标签树的平行遍历：
 - .next_sibling:返回按照HTML文本顺序的下一个平行节点标签
 - .previous_sibling:返回按照HTML文本顺序的上一个平行节点标签
 - .next_siblings:迭代类型，返回按照HTML文本顺序的后续所有平行节点标签
 - .previous_siblings:迭代类型，返回按照HTML文本顺序的谦续所有平行节点的标签
