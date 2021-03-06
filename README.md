page-navigator
==============

#### 查看例子
[在线 Demo](http://meowtec.github.io/demo/page-navigator/example.html)

```
git clone git@github.com:meowtec/page-navigator.git
cd page-navigator
```
`PageNavigator`有`js/php/python`三种版本，有三个例子文件 (example.) html/php/py 分别与之对应。
你可以通过直接在浏览器中打开`example.html`，或者在项目目录下运行`example.py`后打开生成文件，或者把`pagenavigator.php`和`example.php`放在`php`的服务器目录下并访问`example.php`来运行这三个样例。

`pagenavigator.js`可以直接通过`<script>`标签在浏览器中引入，也可以使用`require.js/sea.js`等工具加载，也可以在`nodejs`中使用。

NPM 安装 & nodejs 调用
```
npm install page-navigator
```
```
var PageNavigator = require('page-navigator')
```

#### 使用
##### 初始化
```
var nav = new PageNavigator()

```
##### 生成导航
```
var html = nav.create(currentPage, maxPage) // html 字符串
```
 - currentPage: 当前页, number
 - maxPage: 总页数, number

返回值`html`为生成的导航 html 源码，格式类似于：
```
<a>上一页</a><a>1</a><a>2</a><a>下一页</a>
```
如果你喜欢用`<li>`做导航，你也可以自定义`helper`来使用`<li>`取代`<a>`。

#### 设置
`PageNavigator(setting)`在初始化时可以传入一个设置参数`setting`，类型为`Object`:
```
var nav2 = new PageNavigator({
  linkHelper: 'list.html?page={{page}}&from={{current}}&max={{max}}',
  prevText: '←',
  nextText: '→',
  moreText: '……',
  size: 9,
})
```

#### 自定义 helper
默认的导航以`<span>`和`<a>`标签组成，假设我们要将显示数字的节点换成`<button>`标签，在 setting 中添加`numberHelper`和`currentHelper`:
```
var nav3 = new PageNavigator({
  numberHelper: '<button href="{{link}}" class="item number" data-page="{{page}}">{{page}}</button>',
  currentHelper: '<button class="item number current" data-page="{{page}}" disabled="disabled">{{page}}</button>'
})
```

###### 可定义的 helper 列表请查看源代码。
