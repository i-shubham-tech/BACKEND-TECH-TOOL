# 💡 JavaScript Interview Preparation

## 📘 Table of Contents

1. [Introduction](#introduction)
2. [Normal Feature & ES6 Feature](#normal-feature--es6-feature)
3. [Variable (let, var, const) & Their Differences](#variable-let-var-const--their-differences)
4. [Data Type & Type Casting](#data-type--type-casting)
5. [Operator](#operator)
6. [Conditional](#conditional)
7. [Loops](#loops)
8. [Functions](#functions)
   - [Normal Function](#-normal-function)
   - [Arrow Function](#-arrow-function)
   - [Pure Function](#-pure-function)
   - [Impure Function](#-impure-function)
   - [First Order Function](#-first-order-function)
   - [Higher Order Function](#-higher-order-function)
   - [Currying Function](#-currying-function)
9. [Built-in Methods](#built-in-methods)
   - [Array Methods](#-array-methods)
   - [String Methods](#-string-methods)
   - [Date Methods](#-date-methods)
   - [Math Methods](#-math-methods)
10. [Hoisting](#hoisting)
11. [Closure](#closure)
12. [Promises](#promises)
13. [Sync, Async & Await](#sync-async--await)
14. [Timing Functions](#timing-functions)
15. [Debouncing & Throttling](#debouncing--throttling)
16. [Lazy Loading](#lazy-loading)
17. [Memoization](#memoization)
18. [Code Splitting](#code-splitting)
19. [URL Encoding & Decoding](#url-encoding--decoding)
20. [XSS Attack](#xss-attack)
21. [Service Worker](#service-worker)

---

## Introduction

**JavaScript (JS)** is a **high-level**, **interpreted**, and **dynamic programming language** primarily used for creating interactive web pages.  
It runs in the browser and  also run on the **server side** using environments like **Node.js**.

### ⚙️ Core Characteristics

| **Feature** | **Description** |
|--------------|----------------|
| **Single-Threaded** | JavaScript executes one task at a time in a single call stack. It handles multiple tasks through asynchronous operations (like callbacks, promises, and async/await). |
| **Event-Driven** | JavaScript reacts to events (like clicks, inputs, or server responses) via the **event loop**, which manages queued tasks efficiently. |
| **Non-Blocking I/O** | Instead of waiting for a task (like reading a file) to complete, JavaScript continues executing other code and handles the result later — improving performance. |
| **Interpreted** | Code is executed line by line by the JavaScript engine (like V8 in Chrome), without the need for pre-compilation. |
| **Prototype-Based** | Objects can inherit directly from other objects — enabling flexible and reusable code structures. |
| **Dynamically Typed** | Variable types are determined at runtime, meaning a variable can hold different types of data at different times. |
| **Cross-Platform** | Runs on browsers, servers, desktops, and even IoT devices — making it one of the most versatile languages. |

---

## Normal Feature & ES6 Feature

### 🧩 Overview
Before **ES6 (ECMAScript 2015)**, JavaScript had many limitations such as function-based scoping, callback hell, and lack of modularity.  
**ES6+** introduced modern features that made JavaScript more powerful, readable, and developer-friendly.

### 🔍 Comparison Table

| **Feature** | **Pre-ES6** | **ES6+** |
|--------------|--------------|-----------|
| **Variable Declaration** | `var` | `let`, `const` |
| **Functions** | Normal functions | Arrow functions, Default parameters |
| **Strings** | Concatenation using `+` | Template literals using backticks `` ` `` |
| **Loops** | `for`, `while` | `for...of`, `for...in` |
| **Modules** | No module system | `import`, `export` |
| **Objects** | Manual key-value creation | Object shorthand, destructuring |
| **Classes** | Prototype-based functions | `class` syntax |
| **Promises** | Callback-based async handling | `Promise`, `async/await` |

---

## Variable (let, var, const) & Their Differences 
In JavaScript, variables can be declared using **`var`**, **`let`**, or **`const`**.  
The difference lies mainly in their **scope**, **hoisting behavior**, and **mutability**.

### 📊 Comparison Table

| **Feature** | **var** | **let** | **const** |
|--------------|----------|----------|------------|
| **Scope** | Function-scoped | Block-scoped | Block-scoped |
| **Hoisting** | ✅ Hoisted (initialized as `undefined`) | ✅ Hoisted (in **TDZ** – Temporal Dead Zone) | ✅ Hoisted (in **TDZ**) |
| **Reassign** | ✅ Allowed | ✅ Allowed | ❌ Not allowed |
| **Redeclare** | ✅ Allowed | ❌ Not allowed | ❌ Not allowed |
| **Initialization** | Optional | Optional | Mandatory |
| **Best Use Case** | Legacy / function-level variables | Mutable variables (loops, reassignments) | Constants / configuration values |

> ⚠️ **TDZ (Temporal Dead Zone):**  
> A period between variable hoisting and its declaration where the variable exists but **cannot be accessed**.  
> Accessing it before declaration results in a **ReferenceError**.

---

## Data Type & Type Casting

### 🧩 Overview
JavaScript data types define the **kind of value** a variable can hold.  
They are divided into **two main categories:**

### 📘 1. Primitive Data Types
Primitive types are **immutable** (cannot be changed) and stored **by value**.

| **Type** | **Example** | **Description** |
|-----------|--------------|-----------------|
| **String** | `"Hello"` | Sequence of characters |
| **Number** | `42`, `3.14` | Integer or floating point |
| **Boolean** | `true`, `false` | Logical value |
| **Null** | `null` | Intentional empty value |
| **Undefined** | `undefined` | Declared but not assigned |
| **BigInt** | `123n` | Represents integers larger than `2^53 - 1` |
| **Symbol** | `Symbol("id")` | Unique and immutable identifier |

#### 🧠 Example
```javascript
let name = "Alice";         // String
let age = 25;               // Number
let isLoggedIn = true;      // Boolean
let emptyValue = null;      // Null
let notAssigned;            // Undefined
let bigNumber = 12345678901234567890n; // BigInt
let uniqueKey = Symbol("id"); // Symbol

console.log(typeof name); // "string"
```

### 🧱 2. Non-Primitive Data Types

Non-primitives are **mutable** and stored **by reference** (pointing to memory locations).

#### 📦 Types of Non-Primitive Data

| Type | Example | Description |
|------|----------|-------------|
| **Object** | `{ name: "John", age: 30 }` | Collection of key-value pairs |
| **Array** | `[1, 2, 3]` | Ordered list of elements |
| **Function** | `function greet() {}` | Reusable block of code |

#### 💡 Example

```js
let user = { name: "Alice", age: 25 }; // Object
let numbers = [1, 2, 3];               // Array
function greet() {                     // Function
  return "Hello!";
}

console.log(typeof user);    // "object"
console.log(typeof numbers); // "object"
console.log(typeof greet);   // "function"
```

### 🔄 Type Casting (Type Conversion)

JavaScript **automatically** or **manually** converts values between data types.

#### 🧠 Conversion Types

| Conversion Type | Example | Result |
|------------------|----------|---------|
| **String → Number** | `Number("10")` | `10` |
| **Number → String** | `String(20)` | `"20"` |
| **Any → Boolean** | `Boolean(0)` | `false` |
| **Implicit (auto)** | `"5" * 2` | `10` |
| **Explicit (manual)** | `parseInt("100")` | `100` |

#### ⚙️ Example

```js
let a = "10";
let num = Number(a);   // Explicit conversion
let str = String(20);  // Explicit conversion
let bool = Boolean(0); // false

console.log(typeof num, typeof str, bool); // number string false
```

---

## Operator

### 🧩 Overview

Operators are symbols used to perform operations on variables and values.  
JavaScript supports several types of operators: **Arithmetic**, **Assignment**, **Comparison**, **Logical**, **Bitwise**, **Ternary**, and **Type** operators.

### ➕ 1. Arithmetic Operators

Used to perform mathematical calculations.

| Operator | Description | Example | Result |
|-----------|--------------|----------|--------|
| + | Addition | `5 + 2` | `7` |
| - | Subtraction | `5 - 2` | `3` |
| * | Multiplication | `5 * 2` | `10` |
| / | Division | `5 / 2` | `2.5` |
| % | Modulus (Remainder) | `5 % 2` | `1` |
| ** | Exponentiation | `2 ** 3` | `8` |
| ++ | Increment | `let a = 5; a++` | `6` |
| -- | Decrement | `let a = 5; a--` | `4` |

**Example:**
```js
let x = 10, y = 3;
console.log(x + y);  // 13
console.log(x ** y); // 1000
console.log(x % y);  // 1
```

### 📝 2. Assignment Operators

Used to assign or update values.

| Operator | Example | Same As |
|-----------|----------|----------|
| = | `x = 10` | Assign value |
| += | `x += 5` | `x = x + 5` |
| -= | `x -= 3` | `x = x - 3` |
| *= | `x *= 2` | `x = x * 2` |
| /= | `x /= 4` | `x = x / 4` |
| %= | `x %= 2` | `x = x % 2` |

**Example:**
```js
let a = 5;
a += 3; // a = 8
a *= 2; // a = 16
```

### ⚖️ 3. Comparison Operators

Used to compare two values and return a Boolean (`true` / `false`).

| Operator | Description | Example | Result |
|-----------|--------------|----------|--------|
| == | Equal to (value only) | `5 == "5"` | `true` |
| === | Strict equal (value + type) | `5 === "5"` | `false` |
| != | Not equal (value only) | `5 != "5"` | `false` |
| !== | Strict not equal | `5 !== "5"` | `true` |
| > | Greater than | `10 > 5` | `true` |
| < | Less than | `10 < 5` | `false` |
| >= | Greater than or equal | `5 >= 5` | `true` |
| <= | Less than or equal | `4 <= 3` | `false` |

**Example:**
```js
console.log(5 == "5");  // true
console.log(5 === "5"); // false
```

### 🔗 4. Logical Operators

Used to combine or invert Boolean expressions.

| Operator | Description | Example | Result |
|-----------|--------------|----------|--------|
| && | Logical AND | `true && false` | `false` |
| \|\| | Logical OR | `true || false` | `true` |
| ! | Logical NOT | `!true` | `false` |

**Example:**
```js
let a = true, b = false;
console.log(a && b); // false
console.log(a || b); // true
console.log(!a);     // false
```

### ⚙️ 5. Bitwise Operators

Operate on binary (bit-level) representations of numbers.

| Operator | Description | Example | Result |
|-----------|--------------|----------|--------|
| & | AND | `5 & 1` | `1` |
| \| | OR | `5 \| 1` | `5` |
| ^ | XOR | `5 ^ 1` | `4` |
| ~ | NOT | `~5` | `-6` |
| << | Left shift | `5 << 1` | `10` |
| >> | Right shift | `5 >> 1` | `2` |

**Example:**
```js
console.log(5 & 1); // 1
console.log(5 | 1); // 5
console.log(5 ^ 1); // 4
console.log(~5);    // -6
console.log(5 << 1); // 10
console.log(5 >> 1); // 2
```

### ❓ 6. Ternary Operator

A shorthand for `if-else` statements.

| Syntax | Example | Result |
|---------|----------|--------|
| `condition ? valueIfTrue : valueIfFalse` | `age >= 18 ? "Adult" : "Minor"` | `"Adult"` |

**Example:**
```js
let age = 20;
let type = age >= 18 ? "Adult" : "Minor";
console.log(type); // "Adult"
```

### 🧠 7. Type Operators

Used to check or manipulate data types in JavaScript.

| Operator | Description | Example | Result |
|-----------|--------------|----------|--------|
| typeof | Returns the variable type | `typeof "Hello"` | `"string"` |
| instanceof | Checks if an object is an instance of a class | `arr instanceof Array` | `true` |

**Example:**
```js
let arr = [1, 2, 3];
console.log(typeof arr);           // "object"
console.log(arr instanceof Array); // true
```

---

## Conditional

### 📚 Overview
Conditional statements in JavaScript are used to perform different actions based on different conditions.  
They help control the flow of execution in your program.

JavaScript supports the following conditional statements:
- `if` statement  
- `if...else` statement  
- `switch` statement  
- `ternary (?:)` operator  

### 🔹 if Statement

#### 🧩 Syntax
```javascript
if (condition) {
  // code to execute if condition is true
}
```
#### Example 
```
let age = 18;

if (age >= 18) {
  console.log("You are eligible to vote.");
}
```

### 🔹 if-else Statement

#### 🧩 Syntax
```javascript
if (condition) {
  // code executes if condition is true
} else {
  // code executes if condition is false
}
```
#### Example 
```
let isRaining = true;

if (isRaining) {
  console.log("Take an umbrella!");
} else {
  console.log("Enjoy the sunshine!");
}
```

### 🔹 if-else if Ladder

#### 🧩 Syntax
```javascript
if (condition1) {
  // code executes if condition1 is true
} else if (condition2) {
  // code executes if condition2 is true
} else {
  // executes if none of the above are true
}
```
#### Example 
```
let marks = 85;

if (marks >= 90) {
  console.log("Grade: A");
} else if (marks >= 75) {
  console.log("Grade: B");
} else {
  console.log("Grade: C");
}
```

### 🔹 switch Statement

#### 🧩 Syntax
```javascript
switch (expression) {
  case value1:
    // code block
    break;

  case value2:
    // code block
    break;

  default:
    // code block
}
```
#### Example 
```
let day = "Tuesday";

switch (day) {
  case "Monday":
    console.log("Start of the week");
    break;
  case "Tuesday":
    console.log("Second day of the week");
    break;
  case "Friday":
    console.log("Weekend is near!");
    break;
  default:
    console.log("Just another day");
}
```

### 🔹Ternary Operator (?:)

#### 🧩 Syntax
```javascript
condition ? expressionIfTrue : expressionIfFalse;
```
#### Example 
```
let age = 20;
let message = (age >= 18) ? "Adult" : "Minor";

console.log(message);
```

---

## Loops

### 📚 Overview
Loops in JavaScript are used to execute a block of code repeatedly as long as a specified condition is true.

JavaScript supports several types of loops:
- `for` loop  
- `while` loop  
- `do...while` loop  
- `for...in` loop  
- `for...of` loop  

### 🔹 for Loop

#### 🧩 Syntax
```bash
for (initialization; condition; increment/decrement) {
  // code block to be executed
}
```
#### Example 
```
for (let i = 1; i <= 5; i++) {
  console.log("Count:", i);
}
OUTPUT:1,2,3,4,5
```

### 🔹 while Loop

#### 🧩 Syntax
```bash
while (condition) {
  // code block to be executed
}
```
#### Example 
```
let i = 1;

while (i <= 5) {
  console.log("Number:", i);
  i++;
}
OUTPUT:1,2,3,4,5
```

### 🔹 do...while Loop

#### 🧩 Syntax
```bash
do {
  // code block
} while (condition);
```
#### Example 
```
let i = 1;

do {
  console.log("Iteration:", i);
  i++;
} while (i <= 5);
OUTPUT:1,2,3,4,5
```

### 🔹for...in Loop

#### 🧩 Syntax
```bash
for (key in object) {
  // code to execute
}
```
#### Example 
```
const user = { name: "John", age: 25, city: "Delhi" };

for (let key in user) {
  console.log(key + ":", user[key]);
OUTPUT:name: John
```

### 🔹for...of Loop

#### 🧩 Syntax
```bash
for (variable of iterable) {
  // code block
}
```
#### Example 
```
const fruits = ["Apple", "Banana", "Mango"];

for (let fruit of fruits) {
  console.log(fruit);
}
OUTPUT:name: Apple,Banana,Mango

```

### 🔹Nested Loops

#### Example 
```
for (let i = 1; i <= 3; i++) {
  for (let j = 1; j <= 2; j++) {
    console.log(`i=${i}, j=${j}`);
  }
}

```

### 🔹break and continue

#### Example (break) 
```
for (let i = 1; i <= 5; i++) {
  if (i === 3) break;
  console.log(i);
}
output- 1,2

```

#### Example (continue) 
```
for (let i = 1; i <= 5; i++) {
  if (i === 3) continue;
  console.log(i);
}
output- 1,2,4,5

```

## Functions

## 📚 Overview
Functions in JavaScript are blocks of code designed to perform a particular task.  
They help in **code reusability**, **modularity**, and **clean structure**.

JavaScript functions can be:
- Normal Function  
- Arrow Function  
- Pure Function  
- Impure Function   
- First Order Function  
- Higher Order Function
- Currying Function 

## 🔹 Normal Function

### 🧩 Syntax
```bash
function functionName(parameters) {
  // code to execute
  return value;
}
```
### Example
```bash
function greet(name) {
  return "Hello, " + name + "!";
}

console.log(greet("Shubham"));

`OUTPUT: Hello, Shubham! `
```

## 🔹 Arrow Function

### 🧩 Syntax
```bash
const functionName = (parameters) => {
  // code block
};
```
### Example
```bash
const add = (a, b) => a + b;

console.log(add(5, 10));

`OUTPUT:15 `
```


## 🔹 Pure Function
A Pure Function always returns the same output for the same input and has no side effects.

### Example
```bash
function add(a, b) {
  return a + b;
}

console.log(add(2, 3));  // Always 5
console.log(add(2, 3));  // Always 5 again
```

## 🔹 Impure Function
An Impure Function may change external variables or depend on external state.

### Example
```bash
let counter = 0;

function increment() {
  counter++;
  return counter;
}

console.log(increment()); //1
console.log(increment()); //2
```

## 🔹 First Order Function
A First Order Function does not take another function as an argument and does not return a function.

### Example
```bash
function square(num) {
  return num * num;
}

console.log(square(5)); //25

```

## 🔹 Higher Order Function
A Higher Order Function takes one or more functions as arguments or returns a function.

### Example
```bash
function greet(name) {
  return "Hello, " + name;
}

function processUserInput(callback) {
  let name = "Shubham";
  console.log(callback(name));
}

processUserInput(greet); // Hello Shubham
```

## 🔹 Currying Function
Currying transforms a function that takes multiple arguments into a sequence of functions,
each taking a single argument.

### Example
```bash
function multiply(a) {
  return function(b) {
    return function(c) {
      return a * b * c;
    };
  };
}

console.log(multiply(2)(3)(4)); // 25


```

##  Built-in Methods

## 📚 Overview
JavaScript provides many **built-in methods** that help developers manipulate data easily.  
Below are the most commonly used **Array**, **String**, **Date**, and **Math** methods — neatly formatted for quick reference.

## 🔹 Array Methods

| Method | Description | Example |
|--------|--------------|----------|
| `push()` | Adds one or more elements to the end of an array. | ```bash const fruits = ["Apple"]; fruits.push("Mango"); console.log(fruits); // ["Apple","Mango"] ``` |
| `pop()` | Removes the last element from an array. | ```bash const fruits = ["Apple","Mango"]; fruits.pop(); console.log(fruits); // ["Apple"] ``` |
| `shift()` | Removes the first element of an array. | ```bash const fruits = ["Apple","Banana"]; fruits.shift(); console.log(fruits); // ["Banana"] ``` |
| `unshift()` | Adds one or more elements to the beginning. | ```bash const fruits = ["Banana"]; fruits.unshift("Apple"); console.log(fruits); // ["Apple","Banana"] ``` |
| `slice()` | Extracts a section of an array without modifying it. | ```bash const arr = [1,2,3,4]; console.log(arr.slice(1,3)); // [2,3] ``` |
| `splice()` | Adds/removes items from an array. | ```bash const arr = ["A","B","D"]; arr.splice(2,0,"C"); console.log(arr); // ["A","B","C","D"] ``` |
| `map()` | Creates a new array by applying a function to each element. | ```bash const nums=[1,2,3]; console.log(nums.map(x=>x*2)); // [2,4,6] ``` |
| `filter()` | Creates a new array with elements that pass the test. | ```bash const nums=[1,2,3,4]; console.log(nums.filter(x=>x%2===0)); // [2,4] ``` |
| `reduce()` | Reduces an array to a single value. | ```bash const nums=[1,2,3]; console.log(nums.reduce((a,b)=>a+b)); // 6 ``` |
| `forEach()` | Executes a function for each array element. | ```bash ["A","B","C"].forEach(x=>console.log(x)); ``` |


## 🔹 String Methods

| Method | Description | Example |
|--------|--------------|----------|
| `length` | Returns the length of the string. | ```bash const str="JavaScript"; console.log(str.length); // 10 ``` |
| `toUpperCase()` | Converts to uppercase. | ```bash console.log("js".toUpperCase()); // "JS" ``` |
| `toLowerCase()` | Converts to lowercase. | ```bash console.log("JS".toLowerCase()); // "js" ``` |
| `includes()` | Checks if string contains a substring. | ```bash console.log("Hello JS".includes("JS")); // true ``` |
| `indexOf()` | Returns index of the first occurrence. | ```bash console.log("JavaScript".indexOf("Script")); // 4 ``` |
| `slice()` | Extracts part of a string. | ```bash console.log("JavaScript".slice(0,4)); // "Java" ``` |
| `replace()` | Replaces part of the string. | ```bash console.log("I like JS".replace("JS","JavaScript")); ``` |
| `split()` | Splits string into an array. | ```bash console.log("A,B,C".split(",")); // ["A","B","C"] ``` |
| `trim()` | Removes whitespace from both ends. | ```bash console.log(" JS ".trim()); // "JS" ``` |
| `charAt()` | Returns the character at given index. | ```bash console.log("Hello".charAt(1)); // "e" ``` |


## 🔹 Date Methods

| Method | Description | Example |
|--------|--------------|----------|
| `new Date()` | Creates a new date object. | ```bash const today=new Date(); console.log(today); ``` |
| `getFullYear()` | Returns the 4-digit year. | ```bash console.log(new Date().getFullYear()); ``` |
| `getMonth()` | Returns month (0–11). | ```bash console.log(new Date().getMonth()+1); ``` |
| `getDate()` | Returns day of the month. | ```bash console.log(new Date().getDate()); ``` |
| `getDay()` | Returns day of the week (0–6). | ```bash console.log(new Date().getDay()); ``` |
| `getHours()` | Returns the hour (0–23). | ```bash console.log(new Date().getHours()); ``` |
| `getMinutes()` | Returns the minutes (0–59). | ```bash console.log(new Date().getMinutes()); ``` |
| `getSeconds()` | Returns the seconds (0–59). | ```bash console.log(new Date().getSeconds()); ``` |
| `setFullYear()` | Sets the full year. | ```bash const d=new Date(); d.setFullYear(2030); console.log(d.getFullYear()); ``` |
| `toLocaleDateString()` | Returns a locale-based date string. | ```bash console.log(new Date().toLocaleDateString()); ``` |


## 🔹 Math Methods

| Method | Description | Example |
|--------|--------------|----------|
| `Math.PI` | Returns π (3.14159…). | ```bash console.log(Math.PI); ``` |
| `Math.sqrt(x)` | Returns the square root of x. | ```bash console.log(Math.sqrt(16)); // 4 ``` |
| `Math.pow(x,y)` | Returns x raised to y. | ```bash console.log(Math.pow(2,3)); // 8 ``` |
| `Math.floor(x)` | Rounds down to nearest integer. | ```bash console.log(Math.floor(4.9)); // 4 ``` |
| `Math.ceil(x)` | Rounds up to nearest integer. | ```bash console.log(Math.ceil(4.1)); // 5 ``` |
| `Math.round(x)` | Rounds to nearest integer. | ```bash console.log(Math.round(4.5)); // 5 ``` |
| `Math.abs(x)` | Returns absolute value. | ```bash console.log(Math.abs(-7)); // 7 ``` |
| `Math.max(...values)` | Returns largest number. | ```bash console.log(Math.max(1,5,3)); // 5 ``` |
| `Math.min(...values)` | Returns smallest number. | ```bash console.log(Math.min(1,5,3)); // 1 ``` |
| `Math.random()` | Returns random number (0–1). | ```bash console.log(Math.random()); ``` |

---

##  Hoisting

### 📚 Overview
**Hoisting** is a JavaScript mechanism where **variable and function declarations** are moved (or “hoisted”) to the **top of their scope** during the **compilation phase**, before the code executes.

> 🔹 Only **declarations** are hoisted — not **initializations**.


### 🧩 Hoisting in Different Cases

| Type | Description | Example |
|------|--------------|----------|
| **Variable Hoisting (`var`)** | Variables declared with `var` are hoisted to the top of their scope and initialized as `undefined`. | ```bash console.log(a); // undefined var a = 10; ``` |
| **Variable (`let` and `const`)** | Variables declared with `let` or `const` are hoisted but **not initialized**, leading to a **Temporal Dead Zone (TDZ)** error if accessed before declaration. | ```bash console.log(x); // ❌ ReferenceError let x = 5; ``` |
| **Function Declaration** | Function declarations are fully hoisted — both the name and body can be used before the definition. | ```bash greet(); // ✅ "Hello" function greet(){ console.log("Hello"); } ``` |
| **Function Expression (`var`)** | If a function is defined using a variable (`var`), only the variable declaration is hoisted, not the assignment. | ```bash greet(); // ❌ TypeError var greet = function(){ console.log("Hi"); } ``` |
| **Arrow Function (`let`/`const`)** | Arrow functions behave like variable expressions and are **not hoisted**. | ```bash greet(); // ❌ ReferenceError const greet = () => console.log("Hi"); ``` |

---

## Closure

### 📚 Overview
A **closure** is created when a **function retains access to variables** from its **outer (lexical) scope**,  
even after that outer function has **returned**.

> 💡 Closures allow **data privacy**, **state preservation**, and **function factories** in JavaScript.

---

### 🧩 Key Concept

| Term | Description |
|------|--------------|
| **Lexical Scope** | The scope determined by the **position** of functions in the source code. |
| **Closure** | A function that **remembers** variables from its outer scope, even after the outer function finishes execution. |

---

### ⚙️ Basic Example

```bash
function outer() {
  let counter = 0;

  function inner() {
    counter++;
    console.log(counter);
  }

  return inner;
}

const increment = outer(); 
increment(); // 1
increment(); // 2
increment(); // 3
```
---

## Promises

### 📚 Overview
A **Promise** in JavaScript is an **object** that represents the eventual **completion or failure** of an **asynchronous operation**.

> 💡 Promises make asynchronous code easier to manage and read compared to callback-based code.

### 🧩 Why Promises?
| Problem | Example | Issue |
|----------|----------|--------|
| **Callback Hell** | ```bash doTask1(() => { doTask2(() => { doTask3(() => { console.log("Done!"); }); }); }); ``` | Code becomes nested and hard to manage |
| ✅ **With Promise** | ```bash doTask1().then(doTask2).then(doTask3).then(() => console.log("Done!")); ``` | Clean, readable, chainable syntax |

### 🧠 Promise States
| State | Description | Triggered When |
|-------|-------------|----------------|
| **Pending** | Initial state, waiting for completion. | ```Promise just created``` |
|  **Fulfilled** | Operation completed successfully.| ```resolve() is called``` |
|  **Rejected** | Operation failed. | ```reject() is called``` |


### ⚙️ Promise Syntax

```bash
const promise = new Promise((resolve, reject) => {
  // Perform some async work
  const success = true;

  if (success) {
    resolve("Task completed successfully!");
  } else {
    reject("Task failed!");
  }
});

promise
  .then(result => console.log(result))     // Handles success
  .catch(error => console.log(error))      // Handles failure
  .finally(() => console.log("Done!"));    // Runs always
```

### Example

```bash
function getData() {
  return new Promise((resolve, reject) => {
    setTimeout(() => {
      resolve("Data fetched successfully!");
    }, 1000);
  });
}

getData()
  .then(data => console.log(data))
  .catch(err => console.error(err))
  .finally(() => console.log("Operation finished"));
```
---

## Sync, Async & Await

### 📚 Overview
JavaScript executes code **synchronously by default**, meaning **one line at a time** in sequence.  
However, real-world applications need to handle **asynchronous tasks** like:
- API calls
- File reads
- Timers
- Database queries

To handle this efficiently, JavaScript uses **Asynchronous Programming**, mainly via:
- **Callbacks**
- **Promises**
- **Async/Await**
  

### 🧩 1. Synchronous JavaScript

| Concept | Description |
|----------|--------------|
| **Definition** | Executes one statement **at a time** — blocking the next line until the current one finishes. |
| **Execution** | Line-by-line (single-threaded). |
| **Example Use Case** | Basic arithmetic, simple logic, synchronous loops. |

### 🧱 Example
```bash
console.log("Start");
console.log("Processing...");
console.log("End");
```

### 🧩 2. Asynchronous JavaScript

| Concept | Description |
|----------|--------------|
| **Definition** | Executes long-running operations without blocking the main thread. |
| **Execution** | Uses Web APIs, Event Loop, and Callback Queue. |
| **Example Use Case** | Fetching data, timers, file I/O, animations. |

### 🧱 Example
```bash
console.log("Start");

setTimeout(() => {
  console.log("Async Task Complete");
}, 2000);

console.log("End");

```

### 🧩 3. Async & Await (Modern Asynchronous Handling)

| Concept | Description |
|----------|--------------|
| **Async Function**  | Declared with async keyword — always returns a Promise. |
| **Await Keyword** | Pauses execution until the Promise resolves. |
| **Purpose** | Makes async code look synchronous and readable. |

### 🧱 Example
```bash
function fetchData() {
  return new Promise(resolve => {
    setTimeout(() => resolve("Data Loaded"), 2000);
  });
}

async function getData() {
  console.log("Start Fetching...");
  const result = await fetchData();
  console.log(result);
  console.log("End");
}

getData();


```

```
Start Fetching...
(Waits 2 seconds)
Data Loaded
End
```
---
## Timing Functions  
### `setTimeout`, `setInterval`, and `clearInterval`

## 📚 Overview
JavaScript provides **timing functions** that let you **schedule code execution** after a certain delay or repeatedly at specific intervals.  
These are **asynchronous** functions handled by the **browser’s Web APIs** (or Node.js event loop).

## 🧩 1. `setTimeout()`

| Feature | Description |
|----------|--------------|
| **Purpose** | Executes a function **once** after a specified delay (in milliseconds). |
| **Syntax** | `setTimeout(callback, delay, ...args)` |
| **Return Value** | A unique **timeout ID** (used to cancel it later). |

### 🧱 Example — Basic Usage
```bash
console.log("Start");

setTimeout(() => {
  console.log("Executed after 2 seconds");
}, 2000);

console.log("End");
```
```
**output**
Start
End
Executed after 2 seconds
```
## 🧩 2. `setInterval()`

| Feature | Description |
|----------|--------------|
| **Purpose** | Executes a function repeatedly at specified intervals.. |
| **Syntax** | `setInterval(callback, delay, ...args)` |
| **Return Value** | A unique interval ID (used to stop it using clearInterval).. |

### 🧱 Example — Basic Usage
```bash
let count = 1;

const intervalId = setInterval(() => {
  console.log(`Count: ${count}`);
  count++;
}, 1000);
```
```
**output**
Start
End
Executed after 2 seconds
```

## 🧩 3. `clearInterval()`

| Feature | Description |
|----------|--------------|
| **Purpose** | Stops a running interval created by setInterval()... |
| **Syntax** | `clearInterval(intervalID)` |


### 🧱 Example — Basic Usage
```bash
let count = 1;

const intervalId = setInterval(() => {
  console.log(`Count: ${count}`);
  count++;

  if (count > 5) {
    clearInterval(intervalId);
    console.log("Stopped!");
  }
}, 1000);
```
```
**output**
Output:

Count: 1
Count: 2
Count: 3
Count: 4
Count: 5
Stopped!
```
---

##  Debouncing & Throttling

### 📚 Overview
Both **Debouncing** and **Throttling** are **performance optimization techniques**  
used to control how frequently a function is executed — especially in response to  
frequent events like `scroll`, `resize`, `keypress`, or `mousemove`.

> 🧠 Goal: To **limit unnecessary function calls** and improve **app performance**.

### 🧩 1. Debouncing

| Feature | Description |
|----------|--------------|
| **Definition** | Ensures that a function is **executed only after a specified time** has passed **since the last event**. |
| **Purpose** | To delay execution until the event **stops firing**. |
| **Use Case** | Search box typing, window resizing, form validation. |

### 🧱 Example — Without Debounce

```bash
window.addEventListener('resize', () => {
  console.log('Resized!'); // Fires continuously while resizing
});
```

### 🧱 Example — With Debounce

```bash
function debounce(fn, delay) {
  let timer;
  return function (...args) {
    clearTimeout(timer);
    timer = setTimeout(() => fn.apply(this, args), delay);
  };
}

const handleResize = debounce(() => {
  console.log('Resized! (Debounced)');
}, 1000);

window.addEventListener('resize', handleResize);

```

### 🧩 2. Throttling

| Feature | Description |
|----------|--------------|
| **Definition** | Ensures that a function runs at most once every specified time interval, no matter how often the event occurs. |
| **Purpose** | To execute function at regular intervals, even if the event keeps firing.. |
| **Use Case** |scroll tracking, mouse movement, window resizing, API rate limiting. |

### 🧱 Example — Without Throttling

```bash
window.addEventListener('scroll', () => {
  console.log('Scrolling...'); // Fires on every scroll event (too frequent)
});
```

### 🧱 Example — With Throttling

```bash
function throttle(fn, limit) {
  let inThrottle;
  return function (...args) {
    if (!inThrottle) {
      fn.apply(this, args);
      inThrottle = true;
      setTimeout(() => (inThrottle = false), limit);
    }
  };
}

const handleScroll = throttle(() => {
  console.log('Scrolling... (Throttled)');
}, 1000);

window.addEventListener('scroll', handleScroll);


```
---

##  Lazy Loading

### 📚 Overview
**Lazy Loading** is a **performance optimization technique** that delays the **loading or execution** of resources (like images, scripts, or components) until **they are actually needed**.

> ⚙️ Goal: To **improve page load speed**, **reduce initial load time**, and **save bandwidth**.

### 🧩 Why Lazy Loading?

| Problem | Solution |
|----------|-----------|
| All images/scripts/components load at once, even if not visible | Load them only when needed (on-demand) |
| Slow initial page rendering | Faster initial rendering |
| Unnecessary data usage | Loads only relevant data |


### 🧠 How Lazy Loading Works
1. The resource (image/component) is **not loaded initially**.  
2. As the user **scrolls** or **interacts**, the resource is **loaded dynamically**.  
3. JavaScript detects when an element is **in or near the viewport** (visible area).
4. 
### 🧱 Example 1 — Lazy Loading Images (Manual Approach)

```bash
<img data-src="image.jpg" alt="Nature" class="lazy-image">

<script>
  const images = document.querySelectorAll('.lazy-image');

  const loadImage = (image) => {
    image.src = image.getAttribute('data-src');
  };

  const observer = new IntersectionObserver((entries, observer) => {
    entries.forEach(entry => {
      if (entry.isIntersecting) {
        loadImage(entry.target);
        observer.unobserve(entry.target);
      }
    });
  });

  images.forEach(img => observer.observe(img));
</script>
```
---

## Memoization

### 📚 Overview
**Memoization** is an **optimization technique** used to **speed up function execution**  
by **caching the results** of expensive function calls and **returning the cached result** when the same inputs occur again.

> ⚙️ It’s a **specific form of caching** that stores results based on **function arguments**.


### 🧩 Why Memoization?

| Problem | Solution |
|----------|-----------|
| Expensive or repetitive function calls slow down the app | Store previous results and reuse them |
| Recalculations for the same input | Fetch from cache instantly |
| High computational load | Reduce time complexity by avoiding repetition |


### 🧠 How Memoization Works

1. Function is called with an argument.  
2. Checks if the result for that input exists in the cache.  
3. If found → return cached result.  
4. If not → compute result, store it in cache, and return it.


### 🧱 Example 1 — Without Memoization

```bash
function slowSquare(n) {
  console.log('Calculating...');
  return n * n;
}

console.log(slowSquare(5)); // Calculating... → 25
console.log(slowSquare(5)); // Calculating... → 25 (recomputed)
```
### 🧱 Example 2 — With Memoization
```bash
function memoizedSquare() {
  const cache = {};

  return function (n) {
    if (cache[n]) {
      console.log('Fetching from cache...');
      return cache[n];
    } else {
      console.log('Calculating...');
      const result = n * n;
      cache[n] = result;
      return result;
    }
  };
}

const square = memoizedSquare();

console.log(square(5)); // Calculating... → 25
console.log(square(5)); // Fetching from cache... → 25
```
---
##  Code Splitting

### 📚 Overview
**Code Splitting** is a performance optimization technique that allows JavaScript applications to **split large bundles** into smaller chunks that are **loaded on demand**.  
It helps improve **page load time**, **performance**, and **user experience** by downloading only what’s necessary.

> 💡 In simple terms: *Load code only when you need it!*


### ⚙️ Why Use Code Splitting?

| Benefit | Description |
|----------|--------------|
| 🚀 Faster Load Time | Reduces initial bundle size — only critical code loads first. |
| 🧠 Better Performance | Non-essential modules load asynchronously when required. |
| 🔄 Efficient Caching | Only changed chunks are re-fetched, not the entire app. |
| ⚡ Ideal for SPA | Helps single-page applications load pages faster. |


### 🧱 How It Works

When you bundle your app (e.g., using **Webpack**, **Vite**, or **Parcel**), you can instruct the bundler to **split** your JavaScript files into separate bundles.

These bundles are **lazy-loaded** or **dynamically imported** when certain routes or features are used.


### 📘 Example — Dynamic Import

```bash
// main.js
console.log("Main file loaded");

// Dynamically import only when needed
document.getElementById("loadBtn").addEventListener("click", async () => {
  const module = await import("./math.js");
  console.log(module.add(5, 10)); // Loads math.js only when button clicked
});
```
---

## URL Encoding & Decoding

### 📚 Overview
**URL Encoding** and **Decoding** are techniques used to safely transmit data in URLs.  
URLs can only contain a limited set of ASCII characters, so other characters (like spaces, `#`, `%`, `@`, etc.) are **encoded** into a safe format.

> 💡 Encoding replaces unsafe characters with `%` followed by hexadecimal values.

---

### 🧩 Key Concepts

| Concept | Description |
|----------|--------------|
| **URL Encoding** | Converts special characters into a format that can be safely transmitted in URLs. |
| **URL Decoding** | Converts encoded URL strings back to their original readable form. |
| **Percent-Encoding** | Replaces characters using `%` followed by two hexadecimal digits (e.g., space → `%20`). |

---

### ⚙️ Common Encoding Examples

| Character | Encoded Value | Meaning |
|------------|----------------|----------|
| Space | `%20` | Blank space |
| `#` | `%23` | Hash |
| `@` | `%40` | At sign |
| `/` | `%2F` | Forward slash |
| `:` | `%3A` | Colon |
| `?` | `%3F` | Question mark |
| `&` | `%26` | Ampersand |
| `=` | `%3D` | Equal sign |

---

### 🧱 JavaScript Encoding & Decoding Functions

| Function | Description |
|-----------|--------------|
| `encodeURI()` | Encodes a full URI (does not encode `:`, `/`, `?`, `#`, `&`). |
| `encodeURIComponent()` | Encodes individual URI components (encodes all special characters). |
| `decodeURI()` | Decodes a full encoded URI string. |
| `decodeURIComponent()` | Decodes encoded URI components. |

---

### 🧠 Example — Using `encodeURI()` and `decodeURI()`

```bash
const url = "https://example.com/search?query=hello world&category=books";

const encoded = encodeURI(url);
console.log(encoded);
// Output: https://example.com/search?query=hello%20world&category=books

const decoded = decodeURI(encoded);
console.log(decoded);
// Output: https://example.com/search?query=hello world&category=books
```
---

## XSS Attack

> **Short:** Cross-Site Scripting (XSS) is a class of web vulnerability where untrusted input is injected into pages and executed by victims’ browsers. This guide explains types, safe (local) examples, detection, and strong prevention practices. **Only test in environments you own or have explicit permission for.**

### 📚 Overview
XSS happens when an application includes user-supplied data in a webpage **without proper validation, escaping, or sanitization**, allowing attackers to run arbitrary JavaScript in other users’ browsers. Consequences include session theft, account takeover, phishing, and data exfiltration.

### 🔺 Types of XSS

| Type | Where it happens | Typical flow |
|------|------------------|--------------|
| **Reflected XSS** | Server responds with attacker-supplied input (URL/form) | Victim clicks crafted link → payload reflected → executes |
| **Stored XSS** | Payload persisted (DB, comments, profile) | Attacker saves payload → other users view page → executes |
| **DOM-based XSS** | Vulnerable client-side JS manipulates DOM using untrusted data | Browser JS reads location/hash or element content and injects into DOM → executes |

### ⚠️ Safe testing warning
Only run vulnerable examples **locally** or in a lab (e.g., OWASP Juice Shop, WebGoat) or on systems you own/are authorized to test. **Never** attack other people's websites.


### 🧪 Minimal vulnerable examples (local testing only)

#### 1) Reflected XSS (vulnerable) — Express example
```bash
# server.js (run locally only)
const express = require('express');
const app = express();

app.get('/search', (req, res) => {
  const q = req.query.q || '';
  // VULNERABLE: directly inserts user input into HTML
  res.send(`<html><body>
    <h1>Search results for: ${q}</h1>
  </body></html>`);
});

app.listen(3000, () => console.log('listening on 3000'));
```
---
## Service Worker

### 📚 Overview
A **Service Worker** is a background script that runs **separately from the main browser thread**.  
It acts as a **network proxy layer** between your web app, the browser, and the network — allowing features like **offline access**, **push notifications**, **background sync**, and **caching assets** for better performance.

> 💡 Think of it as a smart, programmable *network middleman* for your web app.

### 🧩 Key Features

| Feature | Description |
|----------|--------------|
| 🕸️ **Offline Support** | Cache assets & data to make your site work offline. |
| ⚡ **Faster Loading** | Serve content from cache instead of the network. |
| 🔔 **Push Notifications** | Receive server push messages even when the app is closed. |
| 🔄 **Background Sync** | Sync data with the server when connectivity returns. |
| 🔐 **Secure Context** | Only works on HTTPS (or localhost). |


### ⚙️ Service Worker Lifecycle

| Stage | Description |
|--------|--------------|
| **Register** | The main JS file registers the Service Worker. |
| **Install** | Runs once when the Service Worker is first installed — good time to cache assets. |
| **Activate** | Cleans up old caches and takes control. |
| **Fetch** | Intercepts network requests to serve cached or network responses. |

### 🧱 Example — Basic Service Worker Setup

#### 1️⃣ Register the Service Worker (in your main JS file)
```bash
// main.js
if ("serviceWorker" in navigator) {
  window.addEventListener("load", () => {
    navigator.serviceWorker
      .register("/service-worker.js")
      .then(() => console.log("✅ Service Worker Registered"))
      .catch(err => console.error("❌ SW Registration Failed:", err));
  });
}
```
---
<p align="center">
  <b>💙 Powered by JavaScript — Logic. Magic. Performance. 💙</b>
</p>
