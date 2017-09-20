# 第三章 对象

[TOC]

## 3.1 语法

对象可以通过两种形式定义：声明（文字）形式和构造形式

对象的大概语法大概是这样的：

```javascript
var myObj ={
  key:value
  //....
};
```

构造形式大概是这样的：

```javascript
var myObj = new Object();
myObj.key=value;

```

> **注意**用上面的“构造形式”来创建对象是非常少见的，一般来说你会使用文字语法，绝大多数内置对象也是这样做的

## 3.2 类型

`对象是JavaScript的基础。在JavaScript中一共有六种主要类型`

- string
- number
- boolean
- null
- undefined
- object

**注意，简单基本类型（string、boolean、number、null和undefined）本身并不是对象，null有时候会被当做一种对象类型，但是这其实只是语言本身的一个bug，即对null执行typeof null时会返回字符创“object”。实际上，null本身是基本类型。**

实际上，JavaScript中有许多特殊的对象子类型，我们可以称之为复杂基本类型。

函数就是对象的一个子类型。JavaScript中的函数是“一等公民”,因为它的本质上和普通的对象是一样的（只是可以调用），所以可以想操作其他对象一样操作函数。

数组也是对象的一种类型，具备一些额外的行为。数组中内容的组织方式比一般的对象要稍微复杂一些

### 内置对象

JavaScript中还有一些对象子类型，通常称为内置对象。有些内置对象的名字看起来和简单基础类型遗言，不过实际上他们的关系更复杂。

- string
- number
- Boolean
- Object
- Function
- Array
- Date
- RegExp
- Error

## 3.3 内容

之前我们提到过，对象的内容是由一些存储在特定命名位置的（任意类型）值组成的，我们称之为属性。

思考下面的代码

```javascript
var myObject ={
  a:2
};
myObject.a;//2
myObject['a'];//2
```

.a语法通常被称为**“属性访问”**，['a']语法通常被称为**“键访问”**

这两种语法的主要区别在于.操作符要求属性名满足标识符的命名规范，而[""]语法可以接受任意UTF-8/Unicode字符串作为属性名，举例说明，如果要引用名称为’‘Super-Fun！’‘的属性，那就必须使用["Super-Fun！"]语法来访问，因为Super-Fun！并不是一个有效的标识符属性名。

**在对象中，属性名永远是字符串。**

### 3.3.1 可计算属性名###

ES6增加了可计算的属性名，可以在文字形式中使用[]包裹一个表达式来当做属性名：

```javascript
var prefix ="foo";
var myObject ={
  [prefix+"bar"]:"hello",
  [prefix+"baz"]:"world"
};
myObject["footbar"];//hello
myObject["footbaz"];//world
```

### 3.3.2 属性与方法

### 3.3.5 属性描述符

从ES5开始，所有属性都具备属性描述符

除了正常的value属性，还包括另外三个特性：writable（可写）、enumerable（可枚举）和configurable（可配置）

1. writable

   writable决定是否可以修改属性的值

2. configurable

   只要属性是可配的，就可以使用defineProperty(...)方法来修改描述符

   重要一点：把configurable修改成false是单向操作，无法撤销！

   除了无法修改，configurable：false还会禁止删除这个属性！

3. enumerable

   从名字就可以看出来，这个描述符控制的是属性是否会出现对象的枚举中，比如说for.... in循环。如果把enumerable设置成false，这个属性就不会出现在枚举中，虽然可以正常访问它。相反的，设置成true就会让它出现在枚举中

### 3.3.6 不变性

1. 对象常量

   结合writable：false和configurable：false就可以创建一个真正的常量属性（不可修改，重定义或者删除）

2. 禁止扩展

   如果你想禁止一个对象添加新属性并且保留已有属性，可以使用Object.preventExtensions(...);

3. 密封

   Object.seal(...)会创建一个“密封”的对象，这个方法实际上会在一个现有对象上调用Object.preventExtensions(....)并把所有现有属性标记为configurable:false。

   所以，密封之后不仅不能添加新属性，也不能重新配置或者删除任何现有属性（虽然可以修改属性的值）

4. 冻结

   Object.freeze(...)会创建一个冻结对象，这个方法实际上会在一个现有对象上调用Object.seal(...)并把所有“数据访问”属性标记为writable:false，这样就无法修改它们的值。

   这个方法是你可以应用在对象上的级别最高的不可变性，它会禁止对于对象本身及其任意直接属性的修改。
###3.3.7 [[Get]]

首先思考下面代码

```javascript
var myObject = {
  a:2
};
myObject.a;//2
```

在语言规范中，myObject.a在myObject上实际上是实现了[[GET]]操作。对象默认的内置[[GET]]操作首先在对象中查找是否有名称相同的属性，如果找到就会返回这个属性的值。

然而，如果没有找到名称相同的属性，按照[[GET]]算法定义会执行另外一种非常重要的行为.(其实就是遍历可能存在的原型链)

如果无论如何都没有找到名称相同的属性，那么[[GET]]操作会返回undefined；

```javascript
var myObject = {
  a:2
};
myObject.b;//undefined
```

**注意，这种方法和访问变量时是不一样的。如果你引用了一个当前词法作用域中不存在变量，并不会像对象属性一样返回undefined，而是会抛出一个ReferenceError异常**

### 3.3.8 [[Put]]

[[Put]]被触发时，实际的行为取决于许多因素，包括对象中是否已经存在这个属性（这是最重要的因素）

如果已经存在这个属性，[[Put]]算法大致会检查下面这些内容。

- 属性是否是访问描述符？如果是并且存在setter就调用setter。

- 属性的数据描述符中writable是否是false？如果是，在非严格模式下静默失败，在严格模式下抛出TypeError异常。

- 如果都不是的话，将该值设置为属性的值。

###3.3.9 Getter和Setter

对象默认的[[Put]]和[[Get]]操作分别可以控制属性值的设置和获取。

在ES5中可以使用setter和getter部分改写默认操作，但是只能应用在单个属性上，无法应用在整个对象上。getter是一个隐藏函数，会在获取属性值时调用。setter也是一个隐藏函数，会在设置属性值时调用。

```javascript
var myObject = {
  //给a定义一个getter
  get a(){
    return 2;
  }
};
myObject.a = 3;
myObject.a //2
```

由于我们只定义a的getter，所以对a的值进行设置时set操作会忽略赋值操作，不会抛出错误。而且即便有合法的setter，由于我们定义的getter只会返回2，所以set操作是没有意义的。

### 3.3.10 存在性

我们可以在不访问属性的情况下判断对象中是否存在这个这个属性：

```javascript
var myObject = {
  a:2
};
("a" in myObject);//true
("b" in myObject);//false

myObject.hasOwnProperty("a");//true
myObject.haeOwnProperty("b");//false
```

in 操作符会检查属性是否在对象及其[[Prototype]]原型链中。相比之下，hasOwnProperty(...)只会检查属性是否在myObject对象中，**不会检查[[Prototype]]链**

**看起来in操作符可以检查容器内是否有某个值，但是它实际上检查的是某个属性名是否存在。对于数组来说这个区别是非常重要的，4 in [2, 4, 6]的结果并不是你期待的true，因为[2, 4, 6]这个数组中包含的属性名是0、1、2，没有4.**

##3.4 遍历

for....in循环可以用来遍历对象的可枚举属性的列表（包括[[Prototype]]链）

使用for... in 遍历对象是无法直接获取属性值的，引文它实际遍历的是对象中的所有可枚举属性，你需要手动获取属性值。

for...of循环

```javascript
var myArray = [1,2,3];
for (var v of myArray){
  console.log(v);
}
//1
//2
//3
```

for...of循环首先会向被访问对象请求一个迭代器对象，然后通过调用迭代器对象的next()方法来遍历所有返回值。

for...of循环每次调用myObject迭代器对象的next()方法时，内部指针都会向前移动并返回对象属性列表的下一个值。









