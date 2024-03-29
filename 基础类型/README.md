# 基础类型

* 布尔值 `boolean`
  
  ```typescript
  let isDone : boolean = false;
  ```

* 数字 `number`
  
  > 除了支持十进制和十六进制字面量，TypeScript还支持ECMAScript 2015中引入的二进制和八进制字面量。
  
  ```typescript
  let decLiteral : number = 6; 
  
  let hexLiteral : number = 0xf00d; 
  
  let binaryLiteral : number = 0b1010; 
  
  let octalLiteral : number = 0o744;
  ```

* 字符串 `string`
  
  ```typescript
  let str : string = 'string';
  ```

* 数组 
  
  ```typescript
  // 第一种定义方式 可以在元素类型后面接上 []，表示由此类型元素组成的一个数组
  let arr : number[] = [1, 2, 3];
  
  // 第二种方式是使用数组泛型  Array<元素类型>
  let arr : Array<number> = [1, 2, 3];
  ```

* 元组 Tuple
  
  > 元组类型允许表示一个已知元素数量和类型的数组，各元素的类型不必相同。
  
  ```typescript
  // 定义一对值分别为 string 和 number 类型的元组。
  let tuple : [string, number];
  
  // 赋值
  tuple = ['hello', 10]; // ok
  
  // 错误赋值
  tuple = [10, 'string']; // 类型错误，与定义索引对不上
  
  /* ------- */
  
  // 当访问一个已知索引的元素，会得到正确的类型：
  console.log(x[0].substr(1)); // OK
  console.log(x[1].substr(1)); // Error, number类型没有substr方法
  
  /* ------- */
  
  // 当访问一个越界的元素，会使用联合类型替代：
  x[3] = 'world'; // OK, 字符串可以赋值给(string | number)类型
  console.log(x[5].toString()); // OK, 'string' 和 'number' 都有 toString
  x[6] = true; // Error, 布尔不是(string | number)类型
  ```

* 枚举 `enum`
  
  ```typescript
  enum Color {Red, Green, Blue}
  let c: Color = Color.Green;
  
  /* ------- */
  
  // 默认情况下，从0开始为元素编号。 你也可以手动的指定成员的数值。
  enum Color {Red = 1, Green, Blue}
  let c: Color = Color.Green;
  
  /* ------- */
  
  // 或者，全部都采用手动赋值：
  enum Color {Red = 1, Green = 2, Blue = 4}
  let c: Color = Color.Green;
  
  /* ------- */
  
  // 枚举类型可以由枚举值得到名字
  enum Color {Red = 1, Green, Blue}
  let colorName: string = Color[2];
  
  console.log(colorName);  // 显示'Green'因为上面代码里它的值是2
  ```

* Any
  
  > 为那些在编程阶段还不清楚类型的变量指定一个类型
  
  ```typescript
  let notSure: any = 4;
  notSure = "maybe a string instead";
  notSure = false; // okay, definitely a boolean
  ```

* 类型断言
  
  ```typescript
  // 第一种 “尖括号”语法
  let someValue: any = "this is a string";
  
  let strLength: number = (<string>someValue).length;
  
  // 第二种 as语法
  let someValue: any = "this is a string";
  
  let strLength: number = (someValue as string).length;
  ```

* Object、Never、Null、Undefined
  
  * `object` 表示非原始类型，也就是除`number`，`string`，`boolean`，`symbol`，`null`或`undefined`之外的类型。
  
  * 使用`object`类型，就可以更好的表示像`Object.create`这样的API
  
  * `never` `null` `undefined` 基本上不常用
