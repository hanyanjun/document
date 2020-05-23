#### 优势

- 更好的错误提示
- 更好的代码提示
- 更好的语义，可读性

#### 基础环境

- node
- vs code 配置

```
preferences -> setting -> Quote -> Quote Style -> single

preferences -> setting -> tab -> Tab Size -> 2

preverences -> setting  -> save -> Format On Save

插件  ->  prettier

（保存文件 ： 自动按照preferences 进行语法格式化）;

```

#### 一些 npm 包

- ts-node
  > 直接使用 node 可以 运行 ts 文件； ts-node xxx.ts
- typescript

#### ts 命令

- tsc xxx.ts
  > typescript 对 ts 文件进行编辑；
  > 转化为 js 文件 ；
  > 编译成 node 可运行或者浏览器运行的文件；

> 类型注解 ： 告诉 ts 变量是什么类型；  
> 类型推断 ： ts 会自动去尝试分析变量的类型；

```
<!-- 不需要类型注解 -->
const firstNumber = 1;
const secondNumber = 2;
const total =  firstNumber + secondNumber;

<!-- 需要类型注解 -->
function getTotal(firstNumber,secondNumber){
  return firstNumber + secondNumber;
}
const total = getTotal(1,2);
```

#### 一些写法

> 函数解构 函数注解

```
function ({a , b } : {a : number , b : number}):number{
  return a + b;
}
```

> 类型推断

```
<!-- 无类型推断 -->
let count ;
count = 1;
<!-- 有类型推断 -->
let count = 1;

```

#### 数组

```
const num : number[] = [1,23,4];
const arr : (number | string ) = [1,'2',3];

const objarr : {name : string} [] = [{name : '1'}];


<!-- type alias -->
type User = {name : string};
const obj1arr : User [] = [{name : '2'}];
```

#### 元组

```
<!-- 适用于数量确定 ， 每个位置类型确定 -->
const teacherInfo : [string , string ,number] = ['dell'   , 'male' , 18];

```

#### 接口 和 类型别名区别

> 接口对应只能是对象或者函数；别名可以对应任意类型；  
> 接口经过 tsc 编译不会编译成 js 代码，只是限制规范编写代码的语法；

```
interface Person {
  name : string
}
type Person = string


interface Person {
  readonly name : string,
  age ? : number,
  color : string,
  [propName : string] : any
}


<!-- 类 应用 某个接口； 必须有接口中存在的属性 -->
class User implements Person {
  name = '11',
  color = '11'
}
<!-- 继承 -->
interface Teacher extends Person {
  teach() : string
}


<!-- 函数接口 -->
interface SayHi  {
  (word : string) : string
}
const say : SayHi = (word : string )=>{
  return '1111'
}

```

#### 类

```
class Person {
   name : string = 'dell'
   getName (){
     return this.name
   }
}

<!-- 当子类 继承父类 重写方法 可以调用super方法去 实现重写； -->

class Teacher extends Person {
  getTeacherName(){
    return 'teacher'
  }
  getName(){
    return super.getName() + 'lee';
  }
}

const person =  new Perosn();
console.log(person.getName());
const teacher  = new Teacher();
console.log(teacher.getTeacherName());

```

#### 类属性 方法 访问类型

> provate ; protected ; publick  
> 默认是 publick 类型：允许在类的内外被调用；  
> private 允许在类内被使用；  
> projected 允许在类内 以及 继承的子类中使用；

```
class Person {
  name : string;
}
const person = new Person();
person.name = 'dell';
console.log(person.name);



```

#### constructor 使用

> 简化变量定义

```
<!-- 传统写法 -->

class Person {
   public name : string
   constructor(name : string){
     this.name = name
   }
}

<!-- 简化写法 -->

class Person {
   constructor(public name : string){}
}
const person = new Person('dell');


```

> 继承中的 constructor

```
class Person {
   constructor(public name : string){}
}
class Teacher extends Person{
  constructor(public age : number){
    <!-- 调父类的构造函数 -->
    super('dell')
  }
}

const teacher = new Teacher(28);

```

####

```
class Person {
  constructor(private : _name : string){}
  get name(){
    return this._name + 'lee';
  }
  set name(name : string){
    const realName = name.split(' ')[0];
    this._name =  realName;
  }
}
const person = new Person('dell');
console.log(person.name);
person.name = 'dell lee';
```

#### getter and setter

> 设计模式 单例模式

```
class Demo {
  private static instance : Demo;

  <!-- 私有化 构造函数 -->
   private constructor(public name : string){}

  <!-- 把方法挂在类上  而不是类实例上 -->
   static getInstance(){
     if(!this.instance){
       this.instance =  new Demo('dell lee')
     }else{
       return this.instance;
     }
   }
}
const demo1 = Demo.getInstance();
const demo1 = Demo.getInstance();

```

#### 限制 class 属性只读

```
class Person {
  public readonly name : string
  constructor( name : string){
    this.name = name;
  }
}
const person = new Person('dell');
console.log(person.name);

```

#### 抽象类

> 把共用的东西封装；

```
class Circle extends Geom{
    getArea(){
      return 123;
    }
}

class Square {

}

class Triangle{

}

<!-- 抽象类 -->
<!-- 只能被继承 不能被实例化 -->
abstract class Geom {
  width : number ;
  getType(){
    return 'Gemo'
  }
  abstract  getArea() : number;
}


-------------------------------------------------

interface Person {
  name : string
}

interface Teacher  extends Person{
  techingAge : number
}
interface Student{
  age : number
}

const teacher = {
  name : 'dell',
  techingAge : 3

}
const student = {
  name : 'lee',
  age : 18
}

const getUserInfo= (user : Person)=>{
  console.log(user.name);
}
getUserInfo(teacher);
getUserInfo(student);
```
