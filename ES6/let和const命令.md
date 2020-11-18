# let和const命令

#### let :star:

用法类似于var，但是声明的变量只在let命令所在的代码块内有效

```js
{
  let a = 1;
  var b = 1;
}

console.log(a) // 报错 a is not defined
console.log(b) // 1
```

##### 不存在变量提升​ :star:

就是说变量调用要在声明之后，var存在变量提升

##### 暂时性死区:star:

在代码块中使用let，即使全局有相同变量被var声明，代码块中的变量也不会被全局所影响

##### 不允许重复声明​  :star:

不能在同一作用域中重复声明

##### 块级作用域​ :star:

什么情况下需要块级作用域？

```js
// 内层变量可能会覆盖外层变量
var tmp = new Date();

function f() {
  console.log(tmp);
  if (false) {
    var tmp = "hello world";
  }
}

f(); // undefined

// 用来计数的循环变量泄露为全局变量
var s = 'hello';

for (var i = 0; i < s.length; i++) {
  console.log(s[i]);
}

console.log(i); // 5
```

##### ES6的块级作用域 :star:

```js
function f1() { // 块
  let n = 5;
  if (true) {  // 块
    let n = 10;
  }
  console.log(n); // 5
}
```

上面代码存在两个代码块，都声明了n，但是外层不会被内层影响，所以最后console得到5。

块作用域的出现，立即执行函数表达式大可不必了。（因为立即执行函数的作用就是避免污染全局，形成一个单独的作用域）

#### const :star:

const声明一个只读的变量（一旦声明立即赋值，不能更改，只声明不赋值会报错）

和let一样不可重复声明，只在块级作用域内作用，不存在变量提升

对于复合类型的对象，变量名指向地址，const只是保证变量名指向的地址不变，并不保证该地址的数据不变。

```js
const foo = {};
foo.prop = 123;

foo.prop
// 123

foo = {}; // TypeError: "foo" is read-only
```

#### 顶层对象 :star:

ES5中顶层对象是window，var和function定义的全局变量可使用window调用

ES6中，使用let和const定义的全局变量虽然是全局使用的，但是使用window调用会undefined

同一段代码为了能够在各种环境，都能取到顶层对象，现在一般是使用`this`变量，但是有局限性。

- 全局环境中，`this`会返回顶层对象。但是，Node模块和ES6模块中，`this`返回的是当前模块。
- 函数里面的`this`，如果函数不是作为对象的方法运行，而是单纯作为函数运行，`this`会指向顶层对象。但是，严格模式下，这时`this`会返回`undefined`。
- 不管是严格模式，还是普通模式，`new Function('return this')()`，总是会返回全局对象。但是，如果浏览器用了CSP（Content Security Policy，内容安全政策），那么`eval`、`new Function`这些方法都可能无法使用。