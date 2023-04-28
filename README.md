
## **TypeScript简介**

1. TypeScript是JavaScript的超集。
2. 它对JS进行了扩展，向JS中引入了类型的概念，并添加了许多新的特性。
3. TS代码需要通过编译器编译为JS，然后再交由JS解析器执行。
4. TS完全兼容JS，换言之，任何的JS代码都可以直接当成JS使用。
5. 相较于JS而言，TS拥有了静态类型，更加严格的语法，更强大的功能；TS可以在代码执行前就完成代码的检查，减小了运行时异常的出现的几率；TS代码可以编译为任意版本的JS代码，可有效解决不同JS运行环境的兼容问题；同样的功能，TS的代码量要大于JS，但由于TS的代码结构更加清晰，变量类型更加明确，在后期代码的维护中TS却远远胜于JS。

## **TypeScript 开发环境搭建**

1. 下载Node.js
   - 64位：https://nodejs.org/dist/v14.15.1/node-v14.15.1-x64.msi
   - 32位：https://nodejs.org/dist/v14.15.1/node-v14.15.1-x86.msi
   
2. 安装Node.js

3. 使用npm全局安装typescript
   - 进入命令行
   - 输入：npm i -g typescript
   
4. 创建一个ts文件

5. 使用tsc对ts文件进行编译
   - 进入命令行
   
   - 进入ts文件所在目录
   
   - 执行命令：tsc xxx.ts

## **TypeScript中的基本类型**

TypeScript中的基本类型：

- 类型声明

  - 类型声明是TS非常重要的一个特点；

  - 通过类型声明可以指定TS中变量（参数、形参）的类型；

  - 指定类型后，当为变量赋值时，TS编译器会自动检查值是否符合类型声明，符合则赋值，否则报错；

  - 简而言之，类型声明给变量设置了类型，使得变量只能存储某种类型的值；

  - 语法：

    - ```typescript
      let 变量: 类型;
      
      let 变量: 类型 = 值;
      
      function fn(参数: 类型, 参数: 类型): 类型{
          ...
      }
      ```

- 自动类型判断

  - TS拥有自动的类型判断机制
  - 当对变量的声明和赋值是同时进行的，TS编译器会自动判断变量的类型
  - 所以如果你的变量的声明和赋值时同时进行的，可以省略掉类型声明

- 类型：

  | **类型** |     **例子**      |            **描述**            |
  | :------: | :---------------: | :----------------------------: |
  |  number  |    1, -33, 2.5    |            任意数字            |
  |  string  | 'hi', "hi", `hi`  |           任意字符串           |
  | boolean  |    true、false    |       布尔值true或false        |
  |  字面量  |      其本身       |  限制变量的值就是该字面量的值  |
  |   any    |         *         |            任意类型            |
  | unknown  |         *         |         类型安全的any          |
  |   void   | 空值（undefined） |     没有值（或undefined）      |
  |  never   |      没有值       |          不能是任何值          |
  |  object  |  {name:'孙悟空'}  |          任意的JS对象          |
  |  array   |      [1,2,3]      |           任意JS数组           |
  |  tuple   |       [4,5]       | 元素，TS新增类型，固定长度数组 |
  |   enum   |    enum{A, B}     |       枚举，TS中新增类型       |

- number

  - ```typescript
    let decimal: number = 6;
    let hex: number = 0xf00d;
    let binary: number = 0b1010;
    let octal: number = 0o744;
    let big: bigint = 100n;
    ```

- boolean

  - ```typescript
    let isDone: boolean = false;
    ```

- string

  - ```typescript
    let color: string = "blue";
    color = 'red';
    
    let fullName: string = `Bob Bobbington`;
    let age: number = 37;
    let sentence: string = `Hello, my name is ${fullName}.
    
    I'll be ${age + 1} years old next month.`;
    ```

- 字面量

  - 也可以使用字面量去指定变量的类型，通过字面量可以确定变量的取值范围

  - ```typescript
    let color: 'red' | 'blue' | 'black';
    let num: 1 | 2 | 3 | 4 | 5;
    ```

- any

  - ```typescript
    let d: any = 4;
    d = 'hello';
    d = true;
    ```

- unknown

  - ```typescript
    let notSure: unknown = 4;
    notSure = 'hello';
    ```

- void

  - ```typescript
    let unusable: void = undefined;
    ```

- never

  - ```typescript
    function error(message: string): never {
      throw new Error(message);
    }
    ```

- object（没啥用）

  - ```typescript
    let obj: object = {};
    ```

- array

  - ```typescript
    let list: number[] = [1, 2, 3];
    let list: Array<number> = [1, 2, 3];
    ```

- tuple

  - ```typescript
    let x: [string, number];
    x = ["hello", 10]; 
    ```

- enum

  - ```typescript
    enum Color {
      Red,
      Green,
      Blue,
    }
    let c: Color = Color.Green;
    
    enum Color {
      Red = 1,
      Green,
      Blue,
    }
    let c: Color = Color.Green;
    
    enum Color {
      Red = 1,
      Green = 2,
      Blue = 4,
    }
    let c: Color = Color.Green;
    ```

- 类型断言

  - 有些情况下，变量的类型对于我们来说是很明确，但是TS编译器却并不清楚，此时，可以通过类型断言来告诉编译器变量的类型，断言有两种形式：

    - 第一种

      - ```typescript
        let someValue: unknown = "this is a string";
        let strLength: number = (someValue as string).length;
        ```

    - 第二种

      - ```typescript
        let someValue: unknown = "this is a string";
        let strLength: number = (<string>someValue).length;
        ```

