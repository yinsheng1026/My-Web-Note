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

JavaScript 中，删除 HTML 元素的类（class）可以通过以下几种方法实现：

### **1. 使用  `classList.remove()`**

最推荐的方式，可以删除一个或多个类名，不会影响其他类名。

const element = document.querySelector('.my-element');

// 删除单个类
element.classList.remove('active');

// 删除多个类
element.classList.remove('class1', 'class2');

**特点**：

- 只删除指定的类，其他类保留。
- 如果类不存在，不会报错。

# 如何监听键盘事件

在 JavaScript 中，可以通过  **`keydown`、`keyup`  和  `keypress`**  事件来监听键盘操作。以下是详细的实现方法：

---

## **1. 基本键盘事件监听**

### **(1) `keydown`（按键按下时触发）**

```javascript
document.addEventListener("keydown", (event) => {
  console.log("按下的键:", event.key);
  console.log("按键代码:", event.code);
});
```

### **(2) `keyup`（按键释放时触发）**

```ja
document.addEventListener('keyup', (event) => {
  console.log('释放的键:', event.key);
});
```

## **2. 获取按键信息**

键盘事件对象 (`event`) 包含以下常用属性：

| 属性             | 说明                                                        | 示例                    |
| ---------------- | ----------------------------------------------------------- | ----------------------- |
| `event.key`      | 返回按下的  **字符**（区分大小写）                          | `"a"`, `"A"`, `"Enter"` |
| `event.code`     | 返回  **物理按键代码**（不区分键盘布局）                    | `"KeyA"`, `"Enter"`     |
| `event.ctrlKey`  | 是否按下了  `Ctrl`  键                                      | `true`/`false`          |
| `event.shiftKey` | 是否按下了  `Shift`  键                                     | `true`/`false`          |
| `event.altKey`   | 是否按下了  `Alt`  键                                       | `true`/`false`          |
| `event.metaKey`  | 是否按下了  `Meta`  键（Windows 的  `Win` / Mac 的  `Cmd`） | `true`/`false`          |

例如：

```javascript
document.addEventListener("keydown", function (e) {
  if (e.key === "Escape") {
    if (!modal.classList.contains("hidden")) {
      closeModal();
    }
  }
});
```

# JavaScript 中的解构 (Destructuring)

解构是 ES6 引入的一种语法，可以方便地从数组或对象中提取数据并赋值给变量。

## 数组解构

```javascript
1. 基本语法
必须使用 [] 表示解构的是数组，变量名按顺序对应数组元素：

const [a, b] = [1, 2]; // a = 1, b = 2
2. 灵活的解构模式
跳过元素：用逗号占位忽略不需要的元素。

const [first, , third] = [1, 2, 3]; // first = 1, third = 3
剩余参数：用 ... 收集剩余元素到新数组。

const [x, ...rest] = [1, 2, 3]; // x = 1, rest = [2, 3]
默认值：为可能不存在的元素提供默认值。

const [a = 10, b] = [, 2]; // a = 10（因为第一个元素是undefined）
3. 嵌套解构
可以解构嵌套数组，但内层仍需用 []：

const [a, [b, c]] = [1, [2, 3]]; // a = 1, b = 2, c = 3
4. 与其他语法结合
解构可以与函数参数、变量声明等结合使用：

function f([x, y]) {
  return x + y;
}
f([1, 2]); // 返回 3
```

## 对象解构

```javascript
1. 基本语法
必须使用 {} 表示解构的是对象，变量名默认匹配对象的属性名：

const person = { name: "Alice", age: 25 };

// 解构 name 和 age
const { name, age } = person;

console.log(name); // "Alice"
console.log(age);  // 25
2. 解构时重命名变量
如果变量名与属性名不同，可以使用 : 指定新名称：

const user = { id: 1, username: "jsDev" };

// 把 username 解构为 newName
const { username: newName } = user;

console.log(newName); // "jsDev"
console.log(username); // 报错！username 未定义
3. 默认值
如果对象没有某个属性，可以设置默认值：

const options = { timeout: 1000 };

// 如果 `retries` 不存在，默认值为 3
const { timeout, retries = 3 } = options;

console.log(timeout); // 1000
console.log(retries); // 3（默认值）
默认值 + 重命名 可以结合使用：

const { timeout: t = 5000, retries: r = 2 } = { timeout: 1000 };
console.log(t); // 1000（覆盖默认值）
console.log(r); // 2（使用默认值）
```

## 混合解构

```javascript
const data = {
  users: [
    { id: 1, name: "Alice" },
    { id: 2, name: "Bob" },
  ],
  meta: {
    page: 1,
    total: 2,
  },
};
const {
  users: [{ name: firstUserName }, { name: secondUserName }],
  meta: { page, total },
} = data;

console.log(firstUserName, secondUserName, page, total); // Alice Bob 1 2
```

## 解构的常见用途

1. 函数返回多个值

2. 导入模块的特定部分

3. 处理 JSON 数据

4. 函数参数默认值

5. 交换变量值

解构语法让代码更简洁易读，是现代 JavaScript 开发中的重要特性。

## 数组扩展符（...）的用法

```javascript
1. 基本用法：展开数组
const arr1 = [1, 2, 3];
const arr2 = [...arr1]; // 展开 arr1 的所有元素

console.log(arr2); // [1, 2, 3]
✅ 特点：

浅拷贝（arr2 是新数组，但内部引用类型仍共享）。

可用于合并数组、函数传参等场景。

2. 合并数组
const arr1 = [1, 2];
const arr2 = [3, 4];
const combined = [...arr1, ...arr2]; // [1, 2, 3, 4]

// 也可以插入新元素
const newArr = [0, ...arr1, 2.5, ...arr2, 5]; // [0, 1, 2, 2.5, 3, 4, 5]

3. 剩余参数（Rest Parameter）
(1) 函数参数收集
javascript
复制
function logArgs(first, ...rest) {
  console.log(first); // "A"
  console.log(rest);  // ["B", "C"]
}

logArgs("A", "B", "C");
(2) 解构时收集剩余元素
javascript
复制
const [first, ...others] = [1, 2, 3];
console.log(first);  // 1
console.log(others); // [2, 3]

const { a, ...rest } = { a: 1, b: 2, c: 3 };
console.log(a);    // 1
console.log(rest); // { b:2, c:3 }
```

与 function 结合使用：

```javascript
新方法（直接获取数组）：
function sum(...numbers) { // numbers 已经是数组
  return numbers.reduce((a, b) => a + b, 0);
}
sum(1, 2, 3); // 6
✅ 优势：

参数直接是数组，无需转换

可与其他命名参数共存
```

# ？？

在 JavaScript 中，`??`  是  **空值合并运算符（Nullish Coalescing Operator）**，它是 ES2020（ES11）引入的一个新特性。

### 作用：

`??`  用于检查左侧的表达式是否为  `null`  或  `undefined`。（不包括 0）如果是，则返回右侧的值；否则返回左侧的值。

# ||

`||` （逻辑或）会检查左侧的值是否为  **假值（falsy）**（如  `0`、`''`、`false`、`null`、`undefined`、`NaN`），如果是，则返回右侧的值。如果不是就直接返回左边的值

# &&

`&&`  会检查左侧的表达式是否为  **真值（truthy）**：

如果左侧是  **真值**（即非  `false`、`0`、`''`、`null`、`undefined`、`NaN`），则返回  **右侧的值**。

如果左侧是  **假值（falsy）**，则直接返回  **左侧的值**（不会计算右侧）。

## **`&&` vs `??` vs `||`  对比**

| 运算符 | 名称     | 检查条件                                | 返回规则                                                     |
| ------ | -------- | --------------------------------------- | ------------------------------------------------------------ | -------------------- |
| `&&`   | 逻辑与   | 左侧是否为  **真值**                    | 如果左侧是真值 → 返回右侧，否则返回左侧                      |
| `\\    |          | `                                       | 逻辑或                                                       | 左侧是否为  **假值** |
| `??`   | 空值合并 | 左侧是否为  **`null`  或  `undefined`** | 如果左侧是  `null`  或  `undefined` → 返回右侧，否则返回左侧 |

# for-of 用法

```javascript
常见用法
1. 遍历数组
const fruits = ['apple', 'banana', 'orange'];

for (const fruit of fruits) {
  console.log(fruit);
}
// 输出:
// apple
// banana
// orange
2. 遍历字符串
const str = 'hello';

for (const char of str) {
  console.log(char);
}
// 输出:
// h
// e
// l
// l
// o
```

# 简化版：数组的  `entries()`  和  `keys()`  方法

## 一句话总结

- `entries()` → 给你"编号+内容"（如  `[0, '苹果']`）
- `keys()` → 只给"编号"（如  `0`）

## 类比理解

想象你有一排储物柜：

复制

1 号柜：篮球
2 号柜：（空的）
3 号柜：书包

### `keys()`  方法

- **作用**：只告诉你柜子编号
- **结果**：`[1, 2, 3]`（不管柜子里有没有东西）

```javascript
const lockers = ["篮球", , "书包"];
for (const number of lockers.keys()) {
  console.log(number);
}
// 输出：0 → 1 → 2（数组从0开始数）
```

### `entries()`  方法

- **作用**：告诉你"编号+里面有什么"
- **结果**：`[ [0,'篮球'], [1,空], [2,'书包'] ]`

```javascript
for (const [number, item] of lockers.entries()) {
  console.log(`${number}号柜：${item || "空的"}`);
}
// 输出：
// 0号柜：篮球
// 1号柜：空的
// 2号柜：书包
```

## 什么时候用？

| 方法        | 使用场景               | 示例                    |
| ----------- | ---------------------- | ----------------------- |
| `keys()`    | 只需要知道第几个       | 给列表加序号            |
| `entries()` | 需要同时知道序号和内容 | 显示排行榜（名次+姓名） |

## 超简单记忆法

🔑 `keys()` = 只要钥匙编号  
🗝️`entries()` = 钥匙+里面的东西

## 实际例子

```javascript
// 用 keys() 加序号
const fruits = ['苹果', '香蕉', '橘子'];
for (const num of fruits.keys()) {
  console.log(`${num + 1}. ${fruits[num]}`);
}
// 用 entries() 同时获取序号和内容
for (const [num, fruit] of fruits.entries()) {
 console.log(`${num + 1}. ${fruit}`);
}
// 两种方法输出相同：
// 1. 苹果
// 2. 香蕉
// 3. 橘子

记住：`entries()` 更方便，因为一次性给你编号和内容！
```

`Object.values()`  之所以要和  `Object`  一起使用，是因为 JavaScript 中**对象**和**数组**的  `values()`  方法有本质区别，设计上有重要原因：

---

### 1. **根本区别：数组 vs 对象**

- **数组**是**可迭代对象**，自带迭代器方法（如  `values()`）
- **普通对象**默认**不可迭代**，需要特殊方法访问值

| 类型 | 是否可迭代 | 获取值的方法         | 返回值类型 |
| ---- | ---------- | -------------------- | ---------- |
| 数组 | ✅ 是      | `arr.values()`       | **迭代器** |
| 对象 | ❌ 否      | `Object.values(obj)` | **数组**   |

---

### 2. **为什么对象要用  `Object.values()`？**

#### (1) 对象没有内置的  `values()`  方法

```javascript
const obj = { a: 1, b: 2 };
obj.values(); // ❌ 报错！普通对象没有 .values() 方法
```

#### (2) `Object.values()`  是静态方法

- 需要通过  `Object`  构造函数调用
- 目的是**统一处理所有对象**（包括没有原型的对象）

```javascript
// ✅ 正确用法
const values = Object.values({ a: 1, b: 2 }); // [1, 2]
```

---

### 3. **设计哲学解释**

#### ▶ **数组的  `values()`**

- 返回**迭代器**（按需生成值，节省内存）
- 属于**实例方法**（因为数组本身就是可迭代的）

```javascript
const arr = ["A", "B"];
const iterator = arr.values(); // 返回迭代器
iterator.next().value; // 'A'
```

#### ▶ **对象的  `Object.values()`**

- 直接返回**值数组**（一次性计算所有值）
- 属于**静态方法**（因为对象不可迭代，需要额外处理）

```javascript
const obj = { a: 1, b: 2 };
const values = Object.values(obj); // 直接返回 [1, 2]
```

## 1. 数组 vs 对象的方法对比

| 方法        | 数组调用方式    | 对象调用方式          | 返回值类型 |
| ----------- | --------------- | --------------------- | ---------- |
| `values()`  | `arr.values()`  | `Object.values(obj)`  | 数组       |
| `keys()`    | `arr.keys()`    | `Object.keys(obj)`    | 数组       |
| `entries()` | `arr.entries()` | `Object.entries(obj)` | 数组       |

Map 可以通过键值增删改查

Map 的键值可以是任何东西

在 JavaScript 中，将对象（`Object`）转换为  `Map`  可以通过以下几种方式实现。`Map`  的键可以是任意类型（包括对象），而普通对象的键只能是字符串或 Symbol，因此转换时需要注意键的处理。

---

## **方法 1：使用  `Object.entries()`  和  `Map`  构造函数**

这是最直接的方法，利用  `Object.entries()`  获取对象的键值对数组，然后传给  `Map`  构造函数。

### **语法**

```jav
const map = new Map(Object.entries(obj));
```

# 字符串的方法

## 1. 获取长度

```javascript
let str = "Hello";
console.log(str.length); // 5 - 字符串长度
```

## 2. 索引访问

```javascript
let str = "Hello";
console.log(str[0]); // "H" - 第一个字符
console.log(str.charAt(1)); // "e" - 第二个字符
```

## 3. 查找元素

```javascript
let str = "Hello World";
// 查找子字符串位置
console.log(str.indexOf("World")); // 6 - 第一次出现的位置
console.log(str.lastIndexOf("l")); // 9 - 最后一次出现的位置

// 检查是否包含
console.log(str.includes("Hello")); // true
console.log(str.startsWith("He")); // true
console.log(str.endsWith("ld")); // true
```

## 4. 切片方法 slice

```javascript
let str = "Hello World";
console.log(str.slice(6, 11)); // "World" - 从6到11(不包括11)
```

## 5. 指定字符转换

使用  `replace()`  方法替换特定字符：

```javascript
let str = "apple,banana,orange";
// 替换第一个匹配项
console.log(str.replace(",", " | ")); // "apple | banana,orange"
// 替换所有匹配项（使用正则表达式）
console.log(str.replace(/,/g, " | ")); // "apple | banana | orange"
```

## 6. 切开成数组 split

使用  `split()`  方法将字符串分割为数组：

```javascript
let str = "apple,banana,orange";
console.log(str.split(",")); // ["apple", "banana", "orange"]
// 按每个字符分割
console.log("hello".split("")); // ["h", "e", "l", "l", "o"]
```

## 7. 填充字符串

使用  `padStart()`  和  `padEnd()`  填充字符串：

```javascript
let str = "5";
// 开头填充到总长度4，用0填充
console.log(str.padStart(4, "0")); // "0005"
// 结尾填充到总长度6，用*填充
console.log(str.padEnd(6, "*")); // "5*****"
```

## 8. 重复字符串

使用  `repeat()`  方法重复字符串：

```javascript
console.log("ha".repeat(3)); // "hahaha"
console.log("*".repeat(5)); // "*****"
```

# JavaScript 高阶函数介绍

## 什么是高阶函数

高阶函数是指可以操作其他函数的函数，满足以下任一条件：

1. 接收一个或多个函数作为参数

2. 返回一个函数作为结果

3. 同时具备上述两种特性

## 常见高阶函数示例

### 1. 接收函数作为参数的高阶函数

```javascript
// 数组常用高阶函数
var numbers = [1, 2, 3, 4];
// forEach - 遍历数组
numbers.forEach(function (num) {
  console.log(num * 2);
});

// map - 转换数组元素
var doubled = numbers.map(function (num) {
  return num * 2;
});

// filter - 过滤数组
var evens = numbers.filter(function (num) {
  return num % 2 === 0;
});

// reduce - 累积计算
var sum = numbers.reduce(function (total, num) {
  return total + num;
}, 0);
```

### 2. 返回函数的高阶函数

```javascript
// 创建乘法器函数
function createMultiplier(factor) {
  return function (num) {
    return num * factor;
  };
}
var double = createMultiplier(2);
console.log(double(5)); // 输出 10
```

### 3. 函数组合的高阶函数

```javascript
// 组合两个函数
function compose(f, g) {
  return function (x) {
    return f(g(x));
  };
}
function add1(x) {
  return x + 1;
}

function mul2(x) {
  return x * 2;
}

var addThenMul = compose(mul2, add1);
console.log(addThenMul(3)); // 输出 8
```

## 高阶函数的优势

1. **代码复用性** - 避免重复编写相似代码

2. **抽象层次高** - 关注做什么而非怎么做

3. **灵活性** - 通过传入不同函数实现不同行为

4. **可维护性** - 业务逻辑更加集中和清晰

高阶函数是 JavaScript 函数式编程的重要特性，广泛用于数组处理、事件回调、异步编程等场景。

# JavaScript 中绑定 this 的简单解释

在 JavaScript 中，`this`  的值取决于函数被调用的方式。为了避免每次调用时都要处理  `this`  的问题，我们可以使用绑定方法来固定  `this`  的值。

## 三种主要绑定方法

### 1. bind() - 永久绑定 this

```javascript
const obj = { name: "小明" };
function sayName() {
  console.log(this.name);
}

// 创建新函数，this 永久绑定为 obj
const boundSayName = sayName.bind(obj);

boundSayName(); // "小明" (this 永远是 obj)
```

### 2. call() - 立即调用并临时绑定 this

```javascript
function greet(greeting) {
  console.log(greeting + ", " + this.name);
}
const person = { name: "小红" };

// 立即调用，this 临时绑定为 person
greet.call(person, "你好"); // "你好, 小红"
```

### 3. apply() - 类似 call()，但参数是数组

```javascript
function introduce(age, job) {
  console.log(`我是${this.name}, ${age}岁, 职业是${job}`);
}
const user = { name: "小刚" };

// 立即调用，this 绑定为 user，参数用数组传递
introduce.apply(user, [25, "工程师"]);
// "我是小刚, 25岁, 职业是工程师"
```

## 为什么需要绑定 this？

1. **避免重复设置** - 绑定一次后可以多次调用，不用每次都指定 this

2. **保持上下文** - 在回调函数中保持正确的 this 指向

3. **代码更简洁** - 减少重复代码

## 实际应用场景

```javascript
const button = document.querySelector('button');
const handler = {
  message: '按钮被点击了',
  handleClick: function() {
    console.log(this.message);
  }
};
// 绑定 this 后可以安全用作事件处理器
button.addEventListener('click', handler.handleClick.bind(handler));
这样无论何时点击按钮，`handleClick` 方法中的 `this` 都会正确指向 `handler` 对象。
```

# at 方法

在 JavaScript 中，`at()`  方法是一个数组和字符串的实例方法，用于根据索引获取元素或字符，**支持负数索引**（从末尾开始计算）。

### **1. 数组的  `at()`  方法**

```javascript
const arr = [10, 20, 30, 40];
console.log(arr.at(1)); // 20（正索引，从 0 开始）
console.log(arr.at(-1)); // 40（负索引，-1 表示最后一个元素）
console.log(arr.at(4)); // undefined（越界返回 undefined）
```

### **2. 字符串的  `at()`  方法**

```javascript
const str = "Hello";
console.log(str.at(1)); // "e"（正索引）
console.log(str.at(-1)); // "o"（负索引，-1 表示最后一个字符）
console.log(str.at(5)); // undefined（越界返回 undefined）
```

# JavaScript 中的  `insertAdjacentHTML()`  方法

`insertAdjacentHTML()`  是一个  **DOM 操作方法**，用于在指定位置插入 HTML 字符串，并解析为真实的 DOM 节点。它比  `innerHTML`  更灵活，可以在元素的不同位置插入内容，而不会覆盖现有内容。

## **语法**

```javascript
element.insertAdjacentHTML(position, htmlString);
```

- **`position`**：插入位置，必须是以下 4 种之一：

  - `'beforebegin'` → 在元素之前插入（作为前一个兄弟节点）
  - `'afterbegin'` → 在元素内部的开头插入（作为第一个子节点）
  - `'beforeend'` → 在元素内部的末尾插入（作为最后一个子节点）
  - `'afterend'` → 在元素之后插入（作为下一个兄弟节点）

- **`htmlString`**：要插入的 HTML 字符串（会被解析为 DOM 节点）

---

## **示例**

### **1. 基本用法**

```html
<div id="container">Hello</div>
```

```javascript
const container = document.getElementById("container");
container.insertAdjacentHTML("beforebegin", "<p>Before</p>"); // 在 div 之前插入
container.insertAdjacentHTML("afterbegin", "<span>Start</span>"); // 在 div 内部开头插入
container.insertAdjacentHTML("beforeend", "<span>End</span>"); // 在 div 内部末尾插入
container.insertAdjacentHTML("afterend", "<p>After</p>"); // 在 div 之后插入
```

\*\*最终 HTML 结构

```html
<p>Before</p>
<div id="container">
  <span>Start</span>
  Hello
  <span>End</span>
</div>
<p>After</p>
```

# forEach 方法

`forEach()`  是 JavaScript 数组提供的一个迭代方法，用于遍历数组的每个元素并执行回调函数。

## 基本语法

```javascript
array.forEach(function(currentValue, index, array) {
  // 在遍历过程中执行操作
}[, thisArg]);
```

### 参数说明：

- **currentValue**：当前正在处理的数组元素
- **index**（可选）：当前元素的索引
- **array**（可选）：正在遍历的数组本身
- **thisArg**（可选）：执行回调时用作  `this`  的值

## 特点和使用场景

### 主要特点：

1. **自动遍历**：自动迭代数组的每个元素

2. **无返回值**：返回  `undefined`（与  `map()`、`filter()`  不同）

3. **不能中断**：无法使用  `break`  或  `return`  终止循环

4. **会跳过空位**：不处理稀疏数组中缺失的元素

### 适用场景：

- 需要对数组每个元素执行操作
- 不需要返回新数组
- 不需要中途终止循环

## 使用示例

### 基础用法：

```javascript
const fruits = ["apple", "banana", "orange"];
fruits.forEach(function (fruit, index) {
  console.log(`${index + 1}. ${fruit}`);
});
// 输出：
// 1. apple
// 2. banana
// 3. orange
```

### 修改原数组：

```javascript
const numbers = [1, 2, 3];
numbers.forEach((num, index, arr) => {
  arr[index] = num * 2; // 直接修改原数组
});
console.log(numbers); // [2, 4, 6]
```

# JavaScript 数组的  `map()`  方法详解

`map()`  是 JavaScript 数组最常用的方法之一，它**创建一个新数组**，其结果是该数组中的<mark>每个元素调用一次提供的回调函数后的返回值</mark>。

## 基本语法

```javascript
const newArray = arr.map(function(currentValue, index, array) {
  // 返回处理后的新元素
}[, thisArg])
```

### 参数说明：

- **currentValue**：当前处理的元素
- **index**（可选）：当前元素的索引
- **array**（可选）：原数组
- **thisArg**（可选）：执行回调时用作  `this`  的值

## 核心特点

1. **不改变原数组**（纯函数）

2. **返回一个新数组**（长度与原数组相同）

3. **自动跳过空位**（稀疏数组）

## 使用示例

### 1. 基础用法：数值数组转换

```javascript
const numbers = [1, 2, 3];
const doubled = numbers.map((num) => num * 2);
// doubled: [2, 4, 6]
// numbers 保持不变: [1, 2, 3]
```

### 2. 对象数组转换

```javascript
const users = [
  { id: 1, name: "Alice" },
  { id: 2, name: "Bob" },
];
const names = users.map((user) => user.name);
// names: ['Alice', 'Bob']
```

### 3. 使用索引参数

```javascript
const letters = ["a", "b", "c"];
const withIndex = letters.map((letter, index) => `${index}:${letter}`);
// withIndex: ['0:a', '1:b', '2:c']
```

### 4. 处理 DOM 元素

```javascript
const divs = document.querySelectorAll("div");
const texts = Array.from(divs).map((div) => div.textContent);
```

## 与 forEach 的区别

| 特性       | map()    | forEach()          |
| ---------- | -------- | ------------------ |
| 返回值     | 新数组   | undefined          |
| 是否纯函数 | 是       | 否（可修改原数组） |
| 链式调用   | 支持     | 不支持             |
| 使用场景   | 数据转换 | 执行副作用         |

# JavaScript 中的 filter 方法简单解释（不使用箭头函数）

`filter()`  是 JavaScript 数组的一个方法，它用于**筛选**数组中的元素，返回一个新的数组，其中包含通过测试的所有元素。

## 工作原理：

1. 遍历数组的每个元素

2. 对每个元素执行一个测试函数（回调函数）

3. 如果测试函数返回  `true`，该元素会被保留在新数组中

4. 如果返回  `false`，该元素会被过滤掉

## 简单示例：

```javascript
const numbers = [1, 2, 3, 4, 5];
// 筛选出所有偶数（使用普通函数）
const evenNumbers = numbers.filter(function (num) {
  return num % 2 === 0;
});

console.log(evenNumbers); // 输出: [2, 4]
```

## 更完整的例子：

```javascript
const fruits = ["apple", "banana", "orange", "grape"];
// 筛选出长度大于5的水果
const longFruits = fruits.filter(function (fruit) {
  return fruit.length > 5;
});

console.log(longFruits); // 输出: ['banana', 'orange']
```

## 特点：

- 不会改变原数组
- 返回一个新数组
- 如果没有任何元素通过测试，返回空数组
- 回调函数可以接收三个参数：当前元素、索引和原数组

## 完整语法示例：

```javascript
array.filter(function (currentValue, index, arr) {
  // 筛选逻辑
  return 测试条件; // 返回true或false
}, thisValue);
```

# JavaScript 中的 reduce 方法简单解释

`reduce()`  是 JavaScript 数组的一个方法，它用于**将数组中的所有元素通过计算累积为<mark>一个最终值**</mark>。

## 工作原理：

1. 遍历数组的每个元素

2. 对每个元素执行一个回调函数（称为 reducer 函数）

3. 每次回调的返回值会作为下一次回调的第一个参数（累积值）

4. 最终返回一个累积结果

## 基本语法：

```javascript
array.reduce(function (accumulator, currentValue, currentIndex, array) {
  // 计算并返回新的累积值
}, initialValue);
```

## 简单示例（求和）：

```javascript
const numbers = [1, 2, 3, 4];
const sum = numbers.reduce(function (total, num) {
  return total + num;
}, 0);

console.log(sum); // 输出: 10
```

## 关键参数解释：

- `accumulator`：累积器，累积回调的返回值
- `currentValue`：当前处理的数组元素
- `currentIndex`（可选）：当前元素的索引
- `array`（可选）：调用 reduce 的数组
- `initialValue`（可选）：作为第一次调用回调时的第一个参数值

## 更多示例：

### 计算乘积：

```javascript
const product = [1, 2, 3, 4].reduce(function (acc, val) {
  return acc * val;
}, 1);
console.log(product); // 24
```

### 找出最大值：

```javascript
const max = [5, 2, 9, 1].reduce(function (a, b) {
  return a > b ? a : b;
});
console.log(max); // 9
```

### 数组转对象：

```javascript
const people = [
  { name: "Alice", age: 21 },
  { name: "Bob", age: 25 },
];
const peopleObj = people.reduce(function (acc, person) {
  acc[person.name] = person.age;
  return acc;
}, {});

console.log(peopleObj); // { Alice: 21, Bob: 25 }
```

## 注意事项：

1. 如果没有提供初始值  `initialValue`，则使用数组的第一个元素作为初始值，并从第二个元素开始迭代

2. 对空数组调用 reduce 且没有提供初始值会抛出错误

3. `reduce`  不会改变原数组

`reduce`  是一个非常强大的方法，可以用于<mark>各种累积计算和数据处理场景</mark>。

## 每次的回调累加的 return 是回到累加器上面

# JavaScript 中的 find 方法详解

`find()`  是 JavaScript 数组的一个非常有用的方法，它用于**查找并返回数组中第一个满足条件的元素**。

## 基本语法

```jav
array.find(function(currentValue, index, arr), thisValue)
```

## 核心特点

1. **返回第一个匹配的元素**（不是数组）

2. **如果找不到则返回  `undefined`**

3. **不会改变原数组**

4. **找到第一个匹配项后立即停止搜索**

## 使用示例

### 基本用法：查找数字

```javascript
const numbers = [5, 12, 8, 130, 44];
const found = numbers.find(function (num) {
  return num > 10;
});

console.log(found); // 输出: 12
```

# JavaScript 中的 findIndex 方法简介

`findIndex()` 是 JavaScript 数组的一个内置方法，它返回数组中满足提供的测试函数的第一个元素的**索引**。如果没有任何元素满足条件，则返回 -1。

## 基本语法

```javascript
array.findIndex(callback(element[, index[, array]])[, thisArg])
```

## 参数说明

- `callback`：用来测试每个元素的函数，接受三个参数：
  - `element`：当前正在处理的元素
  - `index`（可选）：当前元素的索引
  - `array`（可选）：调用 `findIndex` 的数组本身
- `thisArg`（可选）：执行 `callback` 时用作 `this` 的值

## 返回值

数组中第一个通过测试的元素的索引，如果没有找到则返回 -1。

## 示例

```javascript
const numbers = [5, 12, 8, 130, 44];

// 查找第一个大于 10 的元素的索引
const index = numbers.findIndex((num) => num > 10);
console.log(index); // 输出: 1 (因为 12 是第一个大于 10 的元素，它的索引是 1)

// 查找不存在的元素
const notFound = numbers.findIndex((num) => num > 200);
console.log(notFound); // 输出: -1
```

## 与 find() 的区别

- `find()` 返回第一个匹配的**元素本身**
- `findIndex()` 返回第一个匹配的**元素的索引**

## 浏览器兼容性

`findIndex()` 是 ES6 (ECMAScript 2015) 新增的方法，现代浏览器都支持它。如果需要在不支持的环境中运行，可以使用 polyfill 或者传统的 for 循环来实现类似功能。

## 总结

`findIndex()` 是一个非常有用的数组方法，当你需要查找数组中满足特定条件的元素的索引时，它可以提供简洁高效的解决方案。

# JavaScript 中的 `includes()` 方法简介

`includes()` 是 JavaScript 中用于检查数组或字符串是否包含特定元素/子字符串的方法，返回布尔值（`true` 或 `false`）。

## 数组的 `includes()`

### 基本语法

```javascript
array.includes(searchElement[, fromIndex])
```

### 参数说明

- `searchElement`：要查找的元素
- `fromIndex`（可选）：开始查找的位置（索引），默认为 0

### 示例

```javascript
const fruits = ["apple", "banana", "orange"];

console.log(fruits.includes("banana")); // true
console.log(fruits.includes("grape")); // false
console.log(fruits.includes("apple", 1)); // false (从索引1开始查找)
```

### 特点

- 使用 **严格相等（===）** 进行比较
- 可以检测 `NaN`（与 `indexOf` 不同）
- 不会改变原数组

## 字符串的 `includes()`

### 基本语法

```javascript
str.includes(searchString[, position])
```

### 参数说明

- `searchString`：要查找的子字符串
- `position`（可选）：开始查找的位置（索引），默认为 0

### 示例

```javascript
const sentence = "The quick brown fox";

console.log(sentence.includes("quick")); // true
console.log(sentence.includes("fox", 16)); // false (从索引16开始查找)
console.log(sentence.includes("Fast")); // false (区分大小写)
```

### 特点

- 区分大小写
- 是 **ES6 新增方法**，替代传统的 `indexOf() !== -1` 写法

## 与相关方法的比较

| 方法         | 适用对象    | 返回值                     | 检测 NaN | 区分大小写 |
| ------------ | ----------- | -------------------------- | -------- | ---------- |
| `includes()` | 数组/字符串 | 布尔值                     | 可以     | 是         |
| `indexOf()`  | 数组/字符串 | 索引/-1                    | 不可以   | 是         |
| `find()`     | 数组        | 第一个匹配的元素/undefined | -        | -          |

## 浏览器兼容性

`includes()` 是 ES6 (ECMAScript 2015) 新增的方法，现代浏览器都支持。对于旧环境，可以使用 polyfill 或 `indexOf()` 替代。

# JavaScript 中的 `every()` 方法详解

`every()` 是 JavaScript 数组的一个高阶函数方法，用于检测数组中的**所有元素是否都满足**指定的测试条件。

## 基本语法

```javascript
array.every(callback(element[, index[, array]])[, thisArg])
```

## 参数说明

- **callback**：测试每个元素的函数，接受三个参数：
  - `element`：当前处理的元素（必选）
  - `index`：当前元素的索引（可选）
  - `array`：调用 `every` 的数组本身（可选）
- **thisArg**（可选）：执行 callback 时用作 `this` 的值

## 返回值

- **true**：如果所有元素都通过测试
- **false**：如果有任何一个元素未通过测试

## 核心特点

1. **短路特性**：只要有一个元素不满足条件，立即返回 `false`，不再检查剩余元素
2. **空数组调用**：对空数组调用始终返回 `true`
3. **不会修改原数组**

## 使用示例

### 基本用法

```javascript
const ages = [32, 33, 18, 40];

// 检查是否所有年龄都大于18
const allAdult = ages.every((age) => age > 18);
console.log(allAdult); // false（因为18不大于18）
```

### 使用索引参数

```javascript
const numbers = [1, 2, 3, 4, 5];

// 检查每个元素是否都小于其索引+2
const result = numbers.every((num, index) => num < index + 2);
console.log(result); // true
```

### 空数组情况

```javascript
[].every((x) => x > 0); // 总是返回 true
```

## 与 some() 的对比

| 方法    | 返回值条件                | 空数组结果 |
| ------- | ------------------------- | ---------- |
| every() | 所有元素满足条件返回 true | true       |
| some()  | 任一元素满足条件返回 true | false      |

## 实际应用场景

1. 表单验证：

```javascript
const formFields = [
  { value: "John", isValid: true },
  { value: "Doe", isValid: true },
  { value: "30", isValid: true },
];
```

const isFormValid = formFields.every(field => field.isValid);

````
2. 检查数组类型一致性：
```javascript
const mixedArray = [1, '2', 3];
const numbersArray = [1, 2, 3];

const isAllNumbers = arr => arr.every(item => typeof item === 'number');

isAllNumbers(mixedArray); // false
isAllNumbers(numbersArray); // true
````

## 兼容性说明

`every()` 是 ES5 标准方法，所有现代浏览器都支持。如需支持 IE8 及更早版本，需要使用 polyfill 或替代方案。

## 性能提示

由于有短路特性，`every()` 在大型数组中性能优于先 `filter()` 再比较长度的方式。

# JavaScript 中的 `flat()` 方法详解

`flat()` 是 JavaScript 数组的一个方法，用于将**嵌套数组**"展平"（扁平化）变成一维数组。

## 基本语法

```javascript
array.flat([depth]);
```

## 参数说明

- **depth**（可选）：指定要展平的嵌套深度，默认为 `1`

## 返回值

- 返回一个新数组，不会修改原数组

## 核心特点

1. **默认只展平一层**（depth=1）
2. **自动跳过空项**（稀疏数组中的 empty slots）
3. **不改变原数组**（纯函数特性）

## 使用示例

### 基本用法

```javascript
const arr1 = [1, 2, [3, 4]];
arr1.flat(); // [1, 2, 3, 4]

const arr2 = [1, 2, [3, 4, [5, 6]]];
arr2.flat(); // [1, 2, 3, 4, [5, 6]] （默认只展平一层）
```

### 指定展平深度 flat

```javascript
const arr3 = [1, 2, [3, 4, [5, 6]]];

arr3.flat(2); // [1, 2, 3, 4, 5, 6]
arr3.flat(Infinity); // 完全展平所有嵌套
```

### 处理空项

```javascript
const arr4 = [1, 2, , 4, 5];
arr4.flat(); // [1, 2, 4, 5] （自动移除空位）
```

## 实际应用场景

1. **处理 API 返回的嵌套数据**：

```javascript
const apiResponse = [{ items: [1, 2] }, { items: [3, 4] }, { items: [5, 6] }];
```

const allItems = apiResponse
.map(obj => obj.items) // [[1,2], [3,4], [5,6]]
.flat(); // [1, 2, 3, 4, 5, 6]

````
2. **替代递归展平**：
```javascript
// 旧方法：递归实现
function flattenDeep(arr) {
  return arr.reduce((acc, val) =>
    Array.isArray(val) ? acc.concat(flattenDeep(val)) : acc.concat(val), []);
}

// 新方法：一行搞定
const flattenDeep = arr => arr.flat(Infinity);
````

## 与相关方法对比

| 方法        | 作用               | 是否修改原数组 | 处理空位 |
| ----------- | ------------------ | -------------- | -------- |
| `flat()`    | 展平嵌套数组       | 否             | 跳过     |
| `flatMap()` | 先映射后展平一层   | 否             | 跳过     |
| `concat()`  | 合并数组（不展平） | 否             | 保留     |

## 兼容性说明

`flat()` 是 ES2019 (ES10) 新增的方法，现代浏览器和 Node.js 都支持。对于旧环境可以使用以下替代方案：

```javascript
// 替代方案：使用reduce和concat
const flat1 = (arr) => arr.reduce((acc, val) => acc.concat(val), []);

// 替代方案：使用展开运算符
const flat2 = (arr) => [].concat(...arr);
```

## 性能提示

对于大型深层嵌套数组，直接使用 `flat(Infinity)` 可能不是最高效的方案，可以考虑分步展平或自定义递归函数。

# JavaScript 中的 `sort()` 方法详解

`sort()` 是 JavaScript 数组的一个内置方法，用于**对数组元素进行排序**。它非常实用但也有些特殊行为需要注意。

## 基本语法

```javascript
array.sort([compareFunction]);
```

## 参数说明

- **compareFunction**（可选）：定义排序顺序的函数
  - 如果省略，元素会被**转换为字符串**并按 Unicode 码点排序
  - 函数应返回：
    - 负数（如果第一个参数应排在第二个参数前面）
    - 正数（如果第一个参数应排在第二个参数后面）
    - 0（如果两个参数相等）

## 核心特点

1. **原地排序**：会改变原数组（非纯函数）
2. **默认按字符串排序**：即使数组元素是数字
3. **不稳定排序**（在 ES2019 后变为稳定排序）
4. **返回排序后的数组**（注意是原数组的引用）

## 使用示例

### 基本用法

```javascript
const fruits = ["banana", "apple", "orange"];
fruits.sort();
// ['apple', 'banana', 'orange']（按字母顺序）

const numbers = [40, 1, 5, 200];
numbers.sort();
// [1, 200, 40, 5]（按字符串Unicode排序，不是数值大小！）
```

### 数字排序

```javascript
// 正确排序数字数组
const nums = [40, 1, 5, 200];
nums.sort((a, b) => a - b); // 升序 [1, 5, 40, 200]
nums.sort((a, b) => b - a); // 降序 [200, 40, 5, 1]
```

### 对象数组排序

```javascript
const users = [
  { name: "John", age: 25 },
  { name: "Alice", age: 20 },
  { name: "Bob", age: 30 },
];

// 按年龄升序
users.sort((a, b) => a.age - b.age);

// 按名字字母顺序
users.sort((a, b) => a.name.localeCompare(b.name));
```

## 高级用法

### 多条件排序

```javascript
const products = [
  { name: "Laptop", price: 1000, rating: 4.5 },
  { name: "Phone", price: 500, rating: 4.7 },
  { name: "Tablet", price: 500, rating: 4.3 },
];

// 先按价格升序，价格相同则按评分降序
products.sort((a, b) => {
  if (a.price !== b.price) {
    return a.price - b.price;
  }
  return b.rating - a.rating;
});
```

### 本地化排序（考虑语言规则）

```javascript
const items = ["réservé", "Premier", "Cliché"];
items.sort((a, b) => a.localeCompare(b, "fr"));
// 法语正确排序: ['Cliché', 'Premier', 'réservé']
```

## 注意事项

1. **原数组会被修改**：

```javascript
const arr = [3, 1, 2];
const sorted = arr.sort();
console.log(arr); // [1, 2, 3]（原数组被改变！）
```

2. **默认排序的陷阱**：

```javascript
[10, 2, 1].sort(); // 返回 [1, 10, 2]（不是数值顺序！）
```

3. **性能考虑**：

- 不同 JavaScript 引擎使用不同的排序算法
- 对于大型数组，复杂的比较函数可能影响性能

`sort()`是 JavaScript 中最常用的数组方法之一，理解它的行为特点对写出正确的排序逻辑非常重要！

# JavaScript 中的 Array.from() 方法详解

`Array.from()` 是 ES6 (ES2015) 引入的一个静态方法，用于将类数组对象或可迭代对象转换为真正的数组。

## 基本语法

```javascript
Array.from(arrayLike[, mapFn[, thisArg]])
```

参数说明：

- `arrayLike`: 想要转换成数组的类数组对象或可迭代对象
- `mapFn` (可选): 新数组中的每个元素都会执行该回调函数
- `thisArg` (可选): 执行回调函数 `mapFn` 时 `this` 对象

## 主要用途

### 1. 将类数组对象转换为数组

类数组对象是具有 `length` 属性和索引元素的对象，例如：

```javascript
// 将 arguments 转换为数组
function foo() {
  const argsArray = Array.from(arguments);
  console.log(argsArray); // 真正的数组
}

foo(1, 2, 3); // [1, 2, 3]

// 将 DOM 节点列表转换为数组
const divs = document.querySelectorAll("div");
const divArray = Array.from(divs);
```

### 2. 将可迭代对象转换为数组

可迭代对象包括 String、Set、Map 等：

```javascript
// 字符串转换为字符数组
Array.from("hello"); // ['h', 'e', 'l', 'l', 'o']

// Set 转换为数组
const set = new Set([1, 2, 3]);
Array.from(set); // [1, 2, 3]

// Map 转换为数组
const map = new Map([
  [1, "one"],
  [2, "two"],
]);
Array.from(map); // [[1, 'one'], [2, 'two']]
```

### 3. 创建指定长度的数组并初始化

```javascript
// 创建长度为5的数组，所有元素为0
Array.from({ length: 5 }, () => 0); // [0, 0, 0, 0, 0]

// 创建长度为5的数组，元素为索引+1
Array.from({ length: 5 }, (v, i) => i + 1); // [1, 2, 3, 4, 5]
```

## 与扩展运算符(...)的区别

扩展运算符也可以将某些可迭代对象转换为数组：

```javascript
[..."hello"]; // ['h', 'e', 'l', 'l', 'o']
```

但 `Array.from()` 更强大：

1. 可以处理类数组对象（如具有 length 属性的对象）
2. 可以接受映射函数作为第二个参数

## 注意事项

1. `Array.from()` 不会改变原始对象，而是返回一个新数组
2. 对于稀疏数组，空位会被转换为 `undefined`
3. 如果对象既不是类数组也不是可迭代对象，会抛出 TypeError

#
