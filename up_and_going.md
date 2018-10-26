# up&going

  ## 作用域和闭包

* 作用域
  * 存储和寻找变量的机制
  * 不是提前编译，不可移植，编译发生在执行前的几微秒
    1. 词法分析
        >  字符组成的字符串分解成有意义的代码块--词法单元
    2. 语法分析
        > 词法单元 =>  抽象语法树
    3. 代码生成
        > AST转换成可执行代码

* Statements
  > perform a specific task
  * expressions
    > statements are made up of one or more expressions
    > any reference ot a variable or value or a set of variables and value combined with operators
* code
  > a set of special instructions to tell the computer what tasks to perform
* syntax
* variables
  > hold values
  > a value to a symbolic container
  * static typing
  * dynamic typing
* constants
  > capitalized with underscores_between multiple words
  > `const`
* literal value
  > directly in the source code
* operators
  > perform actions with values and variables
  > assignment | math | compound assignment | increment/Decrement| object property access |
* executing a program
  * a special utility
    * interpreter
    * compiler
  > **JavaScript engine compiles the program on the fly and immediately runs the compiled code**
* coercion
  * implicit coercion
  * explicitly coercion
* code comments
  * single-line comment
    * `//`
  * multi-line comment
    * `/*comment*/`
    * `var a = /* arbitrary value */ 42;`
* blocks
  > group a series of statements
  > `{}`
  > blocks are attached to some other control statement
  > does not need a semicolon`;`
* conditionals

    ```JavaScript
        if (amount < bank_balance) {
          console.log("I want to buy this phone!");
        }
    ```
* falsy
  * 0 "" NaN undefined null

* loops
  > `while`
  > `do..while`
  > `break` statement
  > `for(initialization;conditional_test;update_clause) {//do something}`

* Functions
  > arguments
  > functional programming

* Scope
  > lexical scope
  > a collection of variables as well as the rules for how those variables are accessed by name
  > code in one scope can access variables of either that scope or any scope outside of it

## practice

  ```JavaScript
  const   SPENDING_THRESHOLD = 200;
  const TAX_RATE = 0.08;
  const PHONE_PRICE = 99.99;
  const ACCESSORY_PRICE = 9.99;

  var bank_balance = 1000;
  var amount = 0;

  function calculateTax(amount) {
    return amount * TAX_RATE;
  }

  function formatAmount(amount) {
    return "$" + amount.toFixed(2);
  }

  while (amount < bank_balance) {
    amount += PHONE_PRICE;

    if(amount < SPENDING_THRESHOLD) {
      amount += ACCESSORY_PRICE;
    }
  }

  amount = amount + calculateTax(amount);

  if (amount > bank_balance) {
    console.log("You can't afford this purchase. :(")
  }
  ```

## values and types

* built-in types
  * string
  * number
  * boolean
  * null and undefined
  * object
  * symbol
    * `typeof` operator to examine the type
      * return string
      > type of the value currently in `a`
      > only values have types in JavaScript
      * `typeof null` // "object"
* Objects
  > A compound value where you can set **properties(name locations)** that each hold their own values of **any type**

    ``` JavaScript
    var obj = {
      a: "hello world",
      b: 42,
      c: true
    };

    console.log(obj.a) //dot notation
    console.log(obj["a"]) /* bracket notation*/
    ```

  > Bracket notation is useful if you have a property name that has special characters in it

  * Array
    > an object holds values not particularly in named properties/key, but rather in numerically indexed position.

    ```JS
      var arr["hello world", 42, true];

      arr[1]; //42
      arr.length; //3
      typeof arr //"object"
    ```

      ![Array](http://github.com/getify/You-Dont-Know-JS/blob/master/up%20%26%20going/fig5.png)
    
    > arrays for numerically positioned values

    > objects for named properties
  * Functions
    > object subtype
    > `typeof function` // "function"
    ```JS
      var a = "hello world";
      var b = 3.14159;

      a.length; //11
      a.toUperCase(); // "HELLO WORLD"
      b.toFixed(2); //3.14
      // JS automatically boxes the value to its object wrapper counterpart
    ```
* coercion
  * implicit coercion
  * explicit coercion
* falsy values
  * ""
  * 0, -0, NaN
  * null, undefined
  * false
  > non-boolean follows coercion if it's coerced to a boolean
* Equality
  > `==,===,!=,!==`

  > `==, !=` check for value equality with coercion allowed

  > `===, !==` check for value equality without allowing coercion

  > non-primitive value --check the references
  
  ```JS
    var a = [1,2,3];
    var b = [1,2,3];
    var c = "1,2,3";
    a == c; //true
    b == c; // true
    a == b; //false
  ```

* inequality
  > both values in the comparison are strings, the comparison is made lexicographically.

  > otherwise, both coerced to be numbers

  > if can not coered to be a number will result `NaN` and `NaN` si neither greater-than nor less-than any other value

* variables
  * valid identifier
  * start with `a-z, A-Z, $ or _` and followed numbers and other characters.
  * certain words cannot be used as variables, but are OK as property names.

* Function Scope
  > `var` keyword to declare a variable that will belong to the current function scope or the global scope.

  > without `var` will belong to the global scope(non-strict mode) or an error in strict mode.

  * hoisting
    > move to the top of its enclosing scope

    * nested scope
      > available anywhere in that scope and any lower/inner scopes
    * `let`
      > block scope
* conditionals
  ```JS
    switch(a) {
      case 2:
      //do something
      break;
      case 10:
      case 12:
      //do something
      break;
      default:
      // fallback 
    }// **and switch do the strict equation**
  ```

  * condition operator
    > `var b = (42 > 41) ? "hello" : "world";`

* Strict Mode

  > tighten the rules for certain behaviors
    * keep the code to a safer and more appropriate set of guidelines
  

  ```JS
    function foo() {
      "use strict"

      // this code is strict mode

      function bar() {
        //this code is strict mode too
      }
    }
    // this code is not strict mode
  ```

  ```JS
    "use strict"

    function foo() {
      //this code is strict mode
      
      function bar() {
        // this coe is strict mode
      }
    }
    // this code is strict mode
  ```

  > disallowing the implicit auto-global variable declaration from omitting the `var`

* functions as values
  > `foo` is basically just a variable in the outer enclosing scope that's given a reference to the function being declared and the `function` itself is a value

  ```JS
    var foo = function() {
      // anonymous function expression
    };

    var x = function bar() {
      // named function expression
    };
  ```

* Immediately Invoked Function Expressions(IIFEs)

  ```JavaScript
    (function IIFE() { console.log("Hello!");})();
    // used to declare variables that won't affect the surrounding code outside the IIFE.
  ```

* Closure
  > a way to remember and continue to access a function's scope even once teh function has finished running

  ```JS
    function makeAdder(x) {
      function add(y) {
        return x + y;
      }

      return add;
    }

    var plusOne = makeAdder(1);

    plusOne(4);
  ```
  1. when call makeAdder(1), get back a reference to its inner add(..) that remember `x` as `1` we call this function reference as `plusOne`
  2. call `plusOne` function when x remembered

* Modules
  > define private implementation details that are hidden from the outside world as well as a public API that is accessible from the outside.
  
  ```JS
    function User() {
      var username, password;

      function doLogin(user,pw) {
        username = user;
        password = pw;
      }

      var publicAPI = {
        login: doLogin
      };

      return publicAPI;
    }

    var fred = User();

    fred.login("fred", "12Battery34");

  ```

  * executing User() create an instance of the User module--a whole new scope.

* `this` Identifier
  > depends on how the function was called--points to an `object`

  ```JS
    function foo() {
      console.log(this.bar);
    }
    var bar = "global";

    var obj1 = {
      bar: "obj1",
      foo: foo
    };

    var obj2 = {
      bar: "obj2"
    };

    foo();  // non-strict mode => "global"  strict-mode will throw an error
    obj1.foo();
    foo.call(obj2);
    new foo();  // undefined  set `this` to a brand new empty object.

  ```

* Prototypes
  > internal prototype reference to find another object to look for the property
  ```JS
    var foo = {
      a: 42
    };

    var bar = Object.create(foo);// create 'bar' and link it to `foo`
    bar.b = "hello world";

    bar.b
    bar.a
  ```

* polyfilling
  > take the definition of a newer feature and producing a piece of code that's equivalent to the behavior, but is able to run in older JS environments

  ```JS
    if (!Number.isNaN) {
      Number.isNan = function isNaN(x) {
        return x !== x;
      }
    }
  ```

* Transpiling
  > transforming + compiling // 转换和编译

  ```JS
    function foo(a=2) {
      console.log(a);
    }
    foo();
    foo(42);
  ```

  ```JS
    function foo() {
      var a = arguments[0] !== (void 0) ? arguments[0] : 2; // `void 0` aka `undefined`
      console.log( a )
    }
  ```

* Non-JavaScript
  > DOM API

  ```JS
    var el = document.getElementById("foo");

  ```
  * host object

## Scope & Closures

* module pattern
* `this` is dynamically bound based on how the function in question is executed
  * function
  * property
  * fun.call(obj)
  * new Object()
* prototype mechanism
  > behavior delegation

* 状态
  > 变量中存储值和取出值的能力
* 作用域
  > 存储和取出值
  * 词法作用域
    > 词法分析时被定义的
  * 全局变量也自动地是全局对象的属性
  * 动态作用域
* JavaScript 即时编译
  1. 词法分析 --token
  2. 解析 token流-->AST
  3. 代码生成 AST --> 可执行的代码
* 三兄弟
  * 引擎
  * 编译器
    * 作用域
  * 查询
    * LHS -- 找到变量容器
      * 赋值的目标
    * RHS --查询变量的值
      * 赋值的源
      > 赋值操作的左右边
* 嵌套的作用域
  ```JS
    function foo(a) {
      console.log(a + b);
      b = a; // 没用`var`的变量不提升
    }
  ```

* 欺骗词法作用域
  * eval(stringOfCode)
  * with(obj) {}

  ```JS
    function foo(obj) {
      with(obj) {
        a = 2;
      }
    }

    var 01 = { a: 3};
    var 02 = { b: 3};

    foo(o1);
    console.log(o1.a);

    foo(o2);
    console.log(o2.a);// undefined
    // with将一个对象当作一个作用域并将对象的属性当作标识符，创建一个全新的词法作用域
  ```

* 函数作用域
  * `(function foo() { .. })`作为一个表达式，foo只能在`{..}`中找到
  * `(function foo() {})()` 第一对括号使成为表达式  第二对括号使之执行
  * 立即被调用的函数表达式 IIFE
* 块作用域

* 利用作用域隐藏
  * 最低权限原则
  * 避免冲突
  * 全局名称空间
  * 模块管理
* 命名与匿名
  
  ```JS
    setTimeout( function() {
      console.log("I waited 1 second!");
    }, 1000 );
  ```
  * `arguments.callee`

  ```JS
    undefined = true;

    (function IIFE( undefined ) {
      var a;
      if (a === undefined) {
        console.log("Undefined is safe here!");
      }
    })()
  ```

  ```JS
    var a = 2;

    (function IIFE(def) {
      def(window);
    })(function def(global) {
      var a = 3;
      console.log(a);
      console.log(global.a);
    })
  ```