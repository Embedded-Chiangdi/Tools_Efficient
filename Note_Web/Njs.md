 # Javascript
 ## 变量
 ### 数据运算
 ### 字符串的处理
 ### 数组
 ### 对象
 ### 例程
 ```html
<!DOCTYPE html>
<html>
  <head>
    <meta charset="utf-8">
    <title>我的测试站点</title>

  </head>
  <body>
    <button>Press me</button>
    <script>
    const button = document.querySelector('button');
    button.onclick = function() 
    {
        let name = prompt('What is your name?');
        alert('Hello ' + name + ', nice to see you!');
    }
    </script>
  </body>
</html>
 ```

```html
<!DOCTYPE html>
<html>
  <head>
    <meta charset="utf-8">
    <title>我的测试站点</title>

  </head>
  <body>
    <button>Start machine</button>
    <p>The machine is stopped.</p>
    <script>const btn = document.querySelector('button');
    const txt = document.querySelector('p');

    btn.addEventListener('click', updateBtn);

    function updateBtn() {
  if (btn.textContent === 'Start machine') {
    btn.textContent = 'Stop machine';
    txt.textContent = 'The machine has started!';
  } else {
    btn.textContent = 'Start machine';
    txt.textContent = 'The machine is stopped.';
  }
}
    </script>
  </body>
</html>
 ```

## 条件、循环、函数及函数返回值

## 事件
### 事件处理器的属性
```js
var btn = document.querySelector('button');

btn.onclick = function() {
  var rndCol = 'rgb(' + random(255) + ',' + random(255) + ',' + random(255) + ')';
  document.body.style.backgroundColor = rndCol;
}
```
### 行内时间处理器
```js
<button onclick="bgChange()">Press me</button>
function bgChange() {
  var rndCol = 'rgb(' + random(255) + ',' + random(255) + ',' + random(255) + ')';
  document.body.style.backgroundColor = rndCol;
}
```
### addEventListener()和removeEventListener()
```js
var btn = document.querySelector('button');

function bgChange() {
  var rndCol = 'rgb(' + random(255) + ',' + random(255) + ',' + random(255) + ')';
  document.body.style.backgroundColor = rndCol;
}   

btn.addEventListener('click', bgChange);
```