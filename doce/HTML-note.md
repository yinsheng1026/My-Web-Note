# 我的第一个 HTML 代码

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>这是我的第一个网站</title>
  </head>
  <body>
    <h1>Hello,world</h1>
    <p>My is CJH, and this is my very first webpage :D</p>
  </body>
</html>
```

## HTML 基础概念

### HTML 元素结构

一个 HTML 元素通常由三个部分组成：开始标签 - 内容 - 结束标签  
例如：`<h1>Hello, world</h1>`

### HTML 基本结构

```html
<!DOCTYPE html>
<!-- 声明文档类型为HTML -->
<html>
  <!-- 文档根元素 -->
  <head>
    <!-- 头部信息开始 -->
    <title>页面标题</title>
    <!-- 设置浏览器标签页标题 -->
  </head>
  <!-- 头部信息结束 -->
  <body>
    <!-- 页面内容开始 -->
    <h1>这是我的第一个标题</h1>
    <!-- 一级标题 -->
  </body>
  <!-- 页面内容结束 -->
</html>
<!-- 文档根元素结束 -->
```

## HTML 常用元素

### 标题层次结构

HTML 提供了 6 级标题：`<h1>`到`<h6>`  
可以在标题下方使用`<p>`标签创建段落

### 文本格式化

- ​**注释**​：`<!-- 注释内容 -->`
- ​**加粗**​：

  ```html
  <strong>我是加粗的内容</strong>
  ```

- ​**斜体**​：

  ```html
  <em>我是斜体显示的内容</em>
  ```

### 列表

- ​**有序列表**​：

  ```html
  <ol>
    <!-- 有序列表会自动编号 -->
    <li>这是有序列表的第一项</li>
    <li>这是有序列表的第二项</li>
    <li>这是有序列表的第三项</li>
  </ol>
  ```

- ​**无序列表**​：

  ```html
  <ul>
    <!-- 无序列表使用圆点标记 -->
    <li>这是无序列表的第一项</li>
    <li>这是无序列表的第二项</li>
    <li>这是无序列表的第三项</li>
  </ul>
  ```

### 图片

```html
<img src="post-img.jpg" <!-- 图片文件路径 -- /> alt="图片加载失败时的替代文本"
<!-- 无障碍访问和SEO优化 -->
width="500"
<!-- 图片宽度 -->
height="200"/>
<!-- 图片高度 -->
```

### 链接

`<a>`标签用于创建链接，`href`属性指定目标地址：

```html
<p>
  这是我的链接（默认显示为蓝色）：
  <a href="https://www.bilibili.com/" target="_blank">点击访问B站</a>
</p>
```

- `target="_blank"`表示在新标签页打开链接
- 可以使用`<a href="#">空链接</a>`创建返回顶部的链接

### 内部页面跳转

创建另一个 HTML 文件（如 blog.html）：

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>跳转页面</title>
  </head>
  <body>
    <h2>欢迎来到我的博客！</h2>
  </body>
</html>
```

然后通过链接跳转：

```html
<a href="blog.html" target="_blank">访问我的博客</a>
```

## HTML 结构元素

### 导航容器

```html
<nav>
  <a href="blog.html" target="_blank">博客</a>
  <a href="#">空链接1</a>
  <a href="#">空链接2</a>
  <a href="#">空链接3</a>
</nav>
```

### 页眉

```html
<header>
  <h1>📘 代码杂志</h1>
  <nav>
    <a href="blog.html" target="_blank">博客</a>
    <a href="#">空链接1</a>
    <a href="#">空链接2</a>
    <a href="#">空链接3</a>
  </nav>
</header>
```

### 文章区域

```html
<article>
  <!-- 文章内容 -->
</article>
```

### 侧边栏

```html
<aside>
  <!-- 次要内容或相关信息 -->
</aside>
```

### 页脚

```html
<footer>
  <!-- 版权信息、联系方式等 -->
</footer>
```

## 特殊符号

HTML 使用实体符号表示特殊字符，格式为`&实体名;`  
例如：`&copy;`（©）、`&rarr;`（→）

## 按钮

```html
<button>点击我</button>
```
