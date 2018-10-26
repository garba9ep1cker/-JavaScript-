# 上卷

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