### Typescript 安装和编译

```js
npm install -g typescript
```



#### 如何自动编译ts

```js
// 1.创建tsconfig.json文件  tsc --init 生成配置文件

// 2.将里面 "outDir":"./" 改为 "outDir":"./js

// 3.终端 -> 运行任务 -> typescript -> tsc监视-tsconfig.json
```



### ts数据类型

```js
// 布尔类型  boolean
// 数字类型  number
// 字符串类型 string
// 数组类型  array
// 元组类型  tuple
// 枚举类型  enum
// 任意类型  any
// null undefined
// void类型
// never类型

// 定义了一种类型的变量 再赋值其他类型的值会报错
// 修改同类型的可以直接赋值
```



#### 布尔类型

```js
// 定义了布尔类型 数据只能是 true 或者 false
let flag:boolean = true
flag = false
```



#### 数字类型

```js
let a:number = 123
```



#### 字符串类型

```js
let str:string = "123"
```



#### 数组类型

```js
// 方法一
let arr:number[] = [1,2,3,4,5]  //定义一个元素都为数值类型的数组
let arr2:string[] = ['js','es6','ts']  //定义一个元素都为字符串类型的数组

// 方法二
let arr:Array<number> = [1,2,3,4,5]
let arr:Array<string> = ['js','es6','ts']

// 方法三
let arr:any[] = [1,'2',true]
```



#### 元组类型 tuple

```js
// 属于数组的一种
// 可以指定数组中每个元素的类型
let  arr:[string,number,boolean] = ['ts',1,true]
```



#### 枚举类型

``` js
// 事先考虑到某一变量可能取到的值 尽量用自然语言中含义清楚的单词来表示每一个值 这种方法叫做枚举法
/**
	enum 枚举名 {
		标识符[=整型常数]，
		标识符[=整型常数]，
		...
		标识符[=整型常数]，		
	}
*/
enum Flag {
    success=1,
    error=-1
}
let f:Flag = Flag.success

enum Color {
    red,
    blue,
    green
}
console.log(Color.red )  //0
//如果没有定义值 那么打印出来的是索引
enum Color {
    red,
    blue = 5,
    green
}
console.log(Color.red)  // 0
console.log(Color.blue)  // 5
console.log(Color.green)  // 6   以前一个值为基准

// 字符串枚举 必须保证每个成员都用字符串来表示
enum Color {
  red = '你',
  blue = '我',
  green = '他'
}
```



#### 任意类型

```js
let num:any = 123
num = '456'   // 不会报错

// 任意类型 在ts中
let oBox:any = document.querySelector('#box')
oBox.style.color = red
```



#### null undefined

```js
// 其他（never类型）数据类型的子类型

let num:number;  // 输出 为undefined 会报错

let num:undefined; // 输出 

let num:number | undefined;


let num:null;

let num:number | null | undefined

```



#### void类型

```js
// ts 中的void类型表示没有任何类型 一般用于定义方法的时候没有返回值

// es5
function run(){
    console.log(111)
}
run()

// 表示方法没有返回任何类型
function run():void{
    console.log(22)
}
run()

```



#### never类型

```js
// never类型：是其他类型 包括null undefined 的子类型 代表从不会出现的值
// 这意味着声明never的变量只能被never类型所赋值
// 即 定义数值类型的值 只能被数值类型的值进行赋值 ...

let a:never;
a = 123 // 错误的写法

a = (()=>{
    throw new Error('错误')
})()
```



### ts中的函数