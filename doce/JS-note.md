## JavaScript 基础

```javascript
alert("Hello World"); // 修正引号为英文格式
```

创建一个  `.js`  文件来分离代码，方便维护。

HTML 链接方式：

```html
<script src="script.js"></script>
```

---

## JavaScript 变量命名规则

### 基本规则

1. ​**必须以字母、下划线 (`_`) 或美元符号 (`$`) 开头**，不能以数字开头

- 合法：`name`, `_name`, `$name`
- 非法：`1name`

2. ​**后续字符可以是字母、数字、下划线或美元符号**​

- 合法：`name1`, `user_name`, `user$`
- 非法：`user-name`（连字符不允许）

3. ​**区分大小写**​

- `myVar`  和  `myvar`  是两个不同的变量

4. ​**不能使用保留关键字**​

- 非法：`var`, `function`, `if`, `else`  等

### 命名约定

| 风格       | 用途          | 示例                          |
| ---------- | ------------- | ----------------------------- |
| camelCase  | 变量/函数名   | `firstName`, `calculateTotal` |
| PascalCase | 构造函数/类名 | `Person`, `UserAccount`       |
| UPPER_CASE | 常量          | `MAX_SIZE`, `API_KEY`         |

### 最佳实践

- 使用有意义的名称（避免  `a`, `x`  等）
- 布尔变量以  `is`/`has`/`can`  开头：`isActive`, `hasPermission`
- 保持项目风格一致

---

## JavaScript 数据类型（7 种）

### 1. Number

```javascript
let age = 25;
let price = 99.99;
let infinity = Infinity;
```

### 2. String

```javascript
let name = "Alice";
let message = `Hello, ${name}`; // 模板字符串
```

### 3. Boolean

```javascript
let isActive = true;
```

### 4. Null

```javascript
let user = null; // 表示空值
```

### 5. Undefined

```javascript
let x;
console.log(x); // undefined
```

### 6. Symbol（ES6）

```javascript
let id = Symbol("id");
```

### 7. BigInt（ES2020）

```javascript
const bigNum = 12345678901234567890n;
```

### 类型检查

```javascript
typeof 42; // "number"
typeof "hello"; // "string"
typeof null; // "object"（历史遗留问题）
```

---

## 类型转换

### 显式转换

```javascript
let input = "1990";
console.log(Number(input) + 4); // 1994
```

### 隐式转换

```javascript
console.log("10" - 5); // 5（数字运算）
console.log("10" + 5); // "105"（字符串拼接）
```

### 布尔转换规则

| 值                                    | 转换结果 |
| ------------------------------------- | -------- |
| `0`, `""`, `null`, `undefined`, `NaN` | `false`  |
| 其他值                                | `true`   |

---

## 比较运算符

| 运算符 | 描述                   |
| ------ | ---------------------- |
| `===`  | 严格相等（推荐）       |
| `==`   | 宽松相等（会类型转换） |
| `!==`  | 严格不等               |
| `!=`   | 宽松不等               |

---

## 交互函数

### `prompt`

```javascript
let name = prompt("请输入名字", "默认值");
if (name !== null) {
  console.log(`你好, ${name}`);
}
```

### `switch`

```javascript
switch (prompt("输入1-3")) {
  case "1":
    console.log("选择了1");
    break;
  default:
    console.log("其他输入");
}
```

---

## 三元运算符

```javascript
let age = 20;
let status = age >= 18 ? "成人" : "未成年";
```

---

## 严格模式

```javascript
"use strict";
// 整个脚本将启用严格语法检查
```

---

## 函数定义

### 1. 函数声明

```javascript
function calcAge1(birthYear) {
  return 2025 - birthYear;
}
```

### 2. 函数表达式

```javascript
const calcAge2 = function (birthYear) {
  return 2025 - birthYear;
};
```

### 3. 箭头函数

```javascript
const calcAge3 = (birthYear) => 2025 - birthYear;
```

## JavaScript 数组（Array）详解

### 1. 创建数组

#### 字面量方式（推荐）

```javascript
const fruits = ["apple", "banana", "orange"];
const mixed = [1, "hello", true, { name: "Alice" }];
```

#### 构造函数方式

```javascript
const numbers = new Array(1, 2, 3); // [1, 2, 3]
const empty = new Array(5); // 创建长度为5的空数组（非5个undefined）
```

---

### 2. 基本操作

#### 访问与修改

```javascript
fruits[0]; // 'apple'（索引从0开始）
fruits[fruits.length - 1]; // 获取最后一个元素
fruits[1] = "pear"; // 修改元素 → ['apple', 'pear', 'orange']
```

#### 长度属性

```javascript
fruits.length; // 3
```

---

### 3. 常用方法

#### 增删元素

| 方法              | 作用     | 示例                        |
| ----------------- | -------- | --------------------------- |
| `push('mango')`   | 末尾添加 | `fruits` → `[..., 'mango']` |
| `pop()`           | 删除末尾 | 返回被删除的元素            |
| `unshift('kiwi')` | 开头添加 | `fruits` → `['kiwi', ...]`  |
| `shift()`         | 删除开头 | 返回被删除的元素            |

#### 其他关键方法

```javascript
// 增删改任意位置
fruits.splice(1, 1, "grape"); // 从索引1删除1个元素并插入'grape'

// 截取子数组（不改变原数组）
const subArray = fruits.slice(0, 2); // ['apple', 'pear']

// 合并数组
const newArr = fruits.concat(["melon", "berry"]);
```

---

### 4. 遍历数组

#### 循环与方法

```javascript
// for循环
for (let i = 0; i < fruits.length; i++) {
  console.log(fruits[i]);
}

// forEach
fruits.forEach((fruit) => console.log(fruit));

// map（返回新数组）
const lengths = fruits.map((fruit) => fruit.length); // [5, 4, 6]

// filter
const longFruits = fruits.filter((fruit) => fruit.length > 5);
```

---

### 5. ES6+ 特性

#### 现代语法

```javascript
// 展开运算符
const combined = [...fruits, ...["melon", "berry"]];

// 解构赋值
const [first, second] = fruits; // first='apple', second='pear'

// Array.from()
const arrFromStr = Array.from("hello"); // ['h', 'e', 'l', 'l', 'o']
```

---

### 6. 注意事项

#### 引用类型与检测

```javascript
// 数组是引用类型
const arr1 = [1, 2];
const arr2 = arr1;
arr2[0] = 99; // arr1也会变为[99, 2]

// 正确检测数组
Array.isArray([1, 2]); // true
```

---

### 7. 实用技巧

#### 去重与扁平化

```javascript
// 去重
const unique = [...new Set([1, 2, 2, 3])]; // [1, 2, 3]

// 扁平化
const flatArray = [1, [2, [3]]].flat(2); // [1, 2, 3]

// 查找
const hasApple = fruits.includes("apple"); // true
const index = fruits.indexOf("pear"); // 1
```

---

## `includes()` vs `indexOf()`

| 特性      | `includes()`   | `indexOf()` |
| --------- | -------------- | ----------- |
| 返回值    | `true`/`false` | 索引或`-1`  |
| 检测`NaN` | 支持           | 不支持      |
| 类型检查  | 严格           | 严格        |

---

## JavaScript 对象（Object）

### 1. 创建对象

```javascript
// 字面量
const person = { name: "John", age: 30 };

// 构造函数
const person = new Object();
person.name = "John";

// ES6类
class Person {
  constructor(name, age) {
    this.name = name;
    this.age = age;
  }
}
```

### 2. 属性操作

```javascript
// 动态属性
const dynamicKey = "email";
const user = { [dynamicKey]: "john@example.com" };

// 属性简写
const name = "John";
const person = { name }; // { name: 'John' }
```

### 3. 方法定义

```javascript
const person = {
  greet() {
    return `Hello, I'm ${this.name}`;
  },
};
```

### 4. 对象

```javascript
// 浅拷贝
const copy = { ...person };

// 深拷贝
const deepCopy = JSON.parse(JSON.stringify(person));
```

---

## `break` vs `continue`

| 关键字     | 作用             | 循环是否终止 |
| ---------- | ---------------- | ------------ |
| `break`    | 立即退出整个循环 | 是           |
| `continue` | 跳过当前迭代     | 否           |

> ​**注意**​：`continue`  不能在  `switch`  语句中使用

---
