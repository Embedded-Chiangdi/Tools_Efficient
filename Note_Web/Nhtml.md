# Html Note for review
# Basic 
## Struce of HTML
```html
<!DOCTYPE html>
<html>
  <head>
    <meta charset="utf-8">
    <title>我的测试站点</title>
  </head>
  <body>
    <p>这是我的页面</p>
  </body>
</html>
```
***
分析如下：
1. `<!DOCTYPE html>`    声明文档类型
2. `<html> </html> `    用来包裹整个完整的页面
3. `<head> </head>`     类似于头文件。包括搜索结果中出现的关键字和页面描述，CSS样式，字符集声明等。
4. `<meta>`             字符集声明等
5. `<title> </title>`   页面标题 出现在浏览器的标签上
6. `<body> </body>`             页面主内容

### HTML 头部细节分析
```html
<!DOCTYPE html>
<html lang="en-US">
  <head>
    <meta charset="utf-8">
    <title>Meta examples</title>
    <link rel="stylesheet" href="style.css">
  </head>
</html>
```
***
#### 头部可用于引用CSS和 实现Javascript
```html
<link rel="stylesheet" href="my-css-file.css">
<script src="my-js-file.js"></script>
```
***
* `<link>` 通常位于文档头部，rel用来指明文档类型，href知名路径
* `<script>` 上例中指向外部脚本

### HTML 超链接

## Table of HTML

## Forms of HTML
HTML表单：web站点和服务器交互的数据
### Element of Forms
***
**`form`元素**
```html
<form action="/my-handling-form-page" method="post">

</form>
```
***
所有HTML表单都以一个form元素开始。然后将所有需要提交的表单内容放置在form中。
* `action`  定义在提交表单时，应该将所手机的数据给某个模块或者URL去处理。
* `method` 定义了发送数据的HTTP方法

**`label`,`input`,`textarea`**
```html
<form action="/my-handling-form-page" method="post">
  <div>
    <label for="name">Name:</label>
    <input type="text" id="name">
  </div>
  <div>
    <label for="mail">E-mail:</label>
    <input type="email" id="mail">
  </div>
  <div>
    <label for="msg">Message:</label>
    <textarea id="msg"></textarea>
  </div>
</form>
```
***
* `<input>`
* `<label>`     通常于`input`标签相匹配。
* `<textarea>`

**`button`**
```html
<div class="button">
  <button type="submit">Send your message</button>
</div>
```
***
`button`的type属性可配置为`submit` `reset` `button`
* `submit` 发送表单数据到`<form>`中`action`指定目标去
* `reset` 回复默认值
* `button` 

**输入标签的通用属性/表单部件**
```html
<input type="text" id="comment" name="comment" value="I'm a text field">
```
* autofocus 默认关闭
* disabled 默认关闭
* name  元素的名称 和表单数据一起提交的
* value 元素的初始值
* type 指定输入类型