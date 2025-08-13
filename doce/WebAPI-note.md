新篇章：Web API

1. ​**DOM 是特殊的 Web API**​：虽然 DOM 技术上属于 Web APIs 的一部分，但由于其核心地位常被单独讨论

2. ​**JavaScript ≠ DOM**​：

- JavaScript 是语言
- DOM 是浏览器提供的接口
- 没有 DOM 的 JavaScript 环境（如 Node.js）仍然可以运行

3. ​**浏览器扩展了 JavaScript**​：通过 Web APIs，浏览器为 JavaScript 提供了远超语言本身的能力

# DOM（文档对象模型）详解

DOM（Document Object Model，文档对象模型）是 Web 开发中的核心概念，它是 HTML 和 XML 文档的编程接口。

- 将 HTML/XML 文档表示为树形结构的对象模型
- 提供用 JavaScript 操作文档结构的接口
- 是 Web API 的一部分，但因其重要性常被单独讨论
- 由浏览器根据 HTML 文档创建
- 独立于 JavaScript 语言本身（其他语言也可以实现 DOM）
- 通过  `document`  对象暴露给 JavaScript
- DOM 是特殊的 Web API：虽然 DOM 技术上属于 Web APIs 的一部分，但由于其核心地位常被单独讨论

## 什么是 DOM

DOM 是：

- 一个跨平台、语言独立的**接口**，用于表示和操作 HTML/XML 文档
- 将文档结构化为**节点树**，每个节点都是一个对象，包含属性和方法。每个 HTML 的对象都有对应
- 浏览器根据 HTML 文档创建的**内存中的树形结构**，JavaScript 可以通过它来动态改变文档内容、结构和样式

## document.querySelector()

`document.querySelector()`  是 JavaScript 中用于选择 DOM 元素的重要方法，它返回文档中与指定选择器组匹配的第一个元素。将它显示在网页的控制台上面。

## 选择器示例（要注意格式）

1. ​**通过标签名选择**:

```javascript
const firstDiv = document.querySelector("div");
```

1. ​**通过类名选择**:

```javascript
const firstItem = document.querySelector(".item");
```

3. ​**通过 ID 选择**:

```javascript
const header = document.querySelector("#header");
```

4. ​**通过属性选择**:

```javascript
const link = document.querySelector('[href="https://example.com"]');
```

5. ​**组合选择器**:

```javascript
const specialItem = document.querySelector("div.special.item");
```

6. ​**后代选择器**:

```javascript
const nestedSpan = document.querySelector("div p span");
```

7. ​**子元素选择器**:

```javascript
const directChild = document.querySelector("ul > li");
```

8. ​**伪类选择器**:

```javascript
const firstListItem = document.querySelector("li:first-child");
```

## 当想获取其中的文本信息的时候，在后面加一个 .textContent

如：

```javascript
console.log(document.querySelector(".message").textContent);
```

# 可以通过利用 JS 和 DOM 来实现网页信息的变化

`document.querySelector()`  是 JavaScript 中用于选择 DOM 元素的重要方法

例如：

```javascript
document.querySelector(".message").textContent = "wowowowow";
```

意思就是调用 HTML 中的 message 类，将其中的内容变化为引号中的内容

# 设置监听器

# 如何设置 HTML 元素的监听器（事件监听）

在 JavaScript 中，你可以通过事件监听器来响应用户与网页的交互。以下是设置监听器的几种主要方法：

## 使用  `addEventListener()`  方法（推荐）

这是最常用和推荐的方式，允许为同一事件添加多个监听器。

```javascript
element.addEventListener(eventType, eventHandler, [options]);
```

### 示例：

```javascript
const button = document.getElementById("myButton");
// 添加点击事件监听
button.addEventListener("click", function (event) {
  console.log("按钮被点击了!", event);
});

// 可以添加多个同类型监听器
button.addEventListener("click", function () {
  alert("另一个点击处理函数");
});
```

## 具体用法：

### 基本语法

```javascript
target.addEventListener(type, listener, options);
// 或
target.addEventListener(type, listener, useCapture);
```

### 参数说明

| 参数       | 类型              | 描述                                           |
| ---------- | ----------------- | ---------------------------------------------- |
| `type`     | String            | 事件类型（如 "click", "mouseover" 等）         |
| `listener` | Function          | 事件触发时执行的回调函数（被触发成功后的动作） |
| `options`  | Object 或 Boolean | 可选，配置对象或是否使用捕获                   |

例如：HTML 中有一个 input 类名为 guess，想有一个按钮点击后的动作为在控制台打印其中的值，按钮的类名为 check

```javascript
document.querySelector(".check").addEventListener("click", function () {
  console.log(document.querySelector(".guess").value);
});
```

## addEventListener 中的函数可以有许多用途

！！！我们可以在外面就定义好一个函数，这样在 addEventListener 里面就可以直接调用，不需要再创建一个匿名函数了。

如：创建匿名函数：

```javascript
document.querySelector(".check").addEventListener(
  "click",
  function () {
    console.log(document.querySelector(".guess").value);
  } // 这个是匿名函数，没有名字
);
```

在外部定义：

```javascript
const x = function () {
  console.log(document.querySelector(".guess").value);
};
document.querySelector(".check").addEventListener("click", x);
```

# 操控 CSS

# 使用  `document.querySelector`  操控 CSS 样式

`document.querySelector`  是 JavaScript 中非常强大的 DOM 选择方法，结合它我们可以精确地选择和操控页面元素的样式。以下是详细的使用方法：

## 基础选择与样式修改

### 1. 选择元素并修改样式

```javascript
// 选择单个元素
const element = document.querySelector(".my-class"); // 类选择器
const element = document.querySelector("#my-id"); // ID 选择器
const element = document.querySelector("div"); // 标签选择器
const element = document.querySelector("[data-attr]"); // 属性选择器
// 修改样式
element.style.color = "red";
element.style.fontSize = "20px";
element.style.backgroundColor = "#f0f0f0";
```

### 2. 多属性同时修改

```javascript
const btn = document.querySelector("button");
// 方法1：逐个设置
btn.style.margin = "10px";
btn.style.padding = "8px 16px";

// 方法2：使用 cssText 批量设置（会覆盖原有行内样式）
btn.style.cssText = "margin: 10px; padding: 8px 16px; color: white;";

// 方法3：使用 Object.assign
Object.assign(btn.style, {
  margin: "10px",
  padding: "8px 16px",
  color: "white",
});
```

| 方法               | 返回值        | 是否动态更新 | 适用场景         |
| ------------------ | ------------- | ------------ | ---------------- |
| `querySelector`    | 单个元素/null | -            | 操作单个元素     |
| `querySelectorAll` | NodeList      | 静态         | 批量操作多个元素 |

`使用 document.querySelectorAll('') 后会根据匹配元素数量多少生成对应大小的数组`
