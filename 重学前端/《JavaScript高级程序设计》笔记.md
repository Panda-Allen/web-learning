# javaScript高级程序设计
本小结主要记录两年后重读 **《javaScript高级程序设计》** 这本书的新收获，主要记录一些重要且易忘的概念和知识点，用于平时温故知新；

## 数据类型
**ECMASCRIPT** 中有五种基本数据类型：`Undefined`, `Null`, `Boolean`, `Number` 和 `String`。还有一种复杂数据类型（引用数据类型）——`Object`, `Object`本质上是由一组无序的名值对（又称键值对）组成。

### typeof 操作符
`typeof` 操作符常用于检测数据基本类型，返回值为字符串：
- `undefined` —— 该值为未定义
- `boolean` —— 布尔值
- `string` —— 字符串
- `number` —— 数值
- `object` —— 对象或 `null`（注意 `null` 的运算结果，常表示空的对象引用）
- `function` —— 函数（不是基本数据类型，且存在浏览器兼容性）

