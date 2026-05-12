# Javascript

### Variables and Types
- What is the difference between var, let and const?

| Feature      | `var`           | `let`        |    `const`   |
|--------------|-----------------|--------------|--------------|
| Scope        | Function-scoped | Block-scoped | Block-scoped |
| Reassignable |     ✅ Yes      |    ✅ Yes    |    ❌ No    |
| Redeclarable |     ✅ Yes      |    ❌ No     |    ❌ No    |

Examples:
```javascript
var x = 10;
var x = 20; // allowed
console.log(x); // 20

if (true) {
  var a = 5; //ignored by the block scope
}
console.log(a); // 5
```
```javascript
let x = 10;
x = 20; // allowed
console.log(x); // 20

if (true) {
  let a = 5;
}
console.log(a); // ReferenceError
```
```javascript
const x = 10;
x = 20; // Error
const user = { name: "Ana" };
user.name = "Luis"; // allowed
user = {};         // Error
```

- Types in javascript

Primitives (7): `string`, `number`, `boolean`, `null`, `undefined`, `symbol`, `bigint`

Non primitives: `object`, `array`, `function`
> [!NOTE]
- When you use `typeof` operator on a variable, it will return the type of the variable as a string. For example:
```
console.log(typeof "Hello"); // "string"
console.log(typeof 42); // "number"
console.log(typeof 9007199254740991n); // "bigint"
console.log(typeof true); // "boolean"
console.log(typeof Symbol("id")); // "symbol"
console.log(typeof undefined); // "undefined"
console.log(typeof { name: "Ana" }); // "object"
console.log(typeof [1, 2, 3]); // "object"
console.log(typeof null); // "object"
console.log(typeof function() {}); // "function"
```

- What is the difference between `null` and `undefined`?

    `undefined` means a variable has been declared but has not been assigned a value. It is the default value of uninitialized variables and function parameters that are not provided.

    `null` means intentional absence of value.

- What is the difference between session storage, local storage and cookies?

| Feature           | Session Storage                                   |                   Local Storage                    |                                            Cookies                                        |
|-------------------|---------------------------------------------------|----------------------------------------------------|-------------------------------------------------------------------------------------------|
| Scope             | Per session                                       | Persistent                                         | Persistent                                                                                |
| Expiration        | When the browser is closed                        | Never                                              | Set by the server or client, can have an expiration date                                  |
| Storage Limit     | 5-10 MB                                           | 5-10 MB                                            | 4 KB                                                                                      |
| Accessibility     | Accessible only within the same session           | Accessible across sessions                         | Accessible across sessions and can be sent to the server with each HTTP request           |
| Use Cases         | Data that should be cleared when the session ends | Persistent data that should remain across sessions | Data that needs to be sent to the server with each request, such as authentication tokens |

### Arrays
```javascript const fruits = ["apple", "banana", "orange"];
const numbers = [1, 2, 3, 4, 5];
const mixed = ["hello", 42, true
];
```
- Push and Pop
```javascript fruits.push("grape"); // adds "grape" to the end of the array
console.log(fruits); // ["apple", "banana", "orange", "grape"]
fruits.pop(); // removes the last element ("grape") from the array
console.log(fruits); // ["apple", "banana", "orange"]
```

- Shift and Unshift
```javascript fruits.unshift("grape"); // adds "grape" to the beginning of the array
console.log(fruits); // ["grape", "apple", "banana", "orange"]
fruits.shift(); // removes the first element ("grape") from the array
console.log(fruits); // ["apple", "banana", "orange"]
```

###Functions
- What is the difference between function declaration and function expression?

A function declaration is a named function that is defined using the `function` keyword. It is hoisted to the top of its scope, which means it can be called before it is defined in the code. For example:
```javascript
function greet() {
  console.log("Hello!");
}
greet(); // "Hello!"
```
A function expression is an anonymous function that is assigned to a variable. It is not hoisted, which means it cannot be called before it is defined in the code. For example:
```javascript
const greet = function() {
  console.log("Hello!");
};
greet(); // "Hello!"
```
- What is the difference between arrow function and regular function?

An arrow function is a shorter syntax for writing functions in JavaScript. It does not have its own `this` context, which means it inherits the `this` value from the enclosing scope. This can be useful when working with callbacks or methods that need to access the `this` value of the surrounding code. For example:
```javascript
const person = {
  name: "Ana",
  greet: function() {
    console.log("Hello, " + this.name);
  }
};
person.greet(); // "Hello, Ana"
```
In contrast, a regular function has its own `this` context, which can lead to different behavior when used in certain situations. For example:
```javascript
const person = {
  name: "Ana",
  greet: function() {
    console.log("Hello, " + this.name);
  }
};
const greetFunction = person.greet;
greetFunction(); // "Hello, undefined"
```

In this example, the `greetFunction` does not have access to the `this` value of the `person` object, so it returns `undefined`. However, if we use an arrow function, it will inherit the `this` value from the surrounding scope, which is the `person` object:
```javascript
const person = {
  name: "Ana",
  greet: () => {
    console.log("Hello, " + this.name);
  }
};
person.greet(); // "Hello, Ana"
```


### Loops and Conditionals:

- What is `event loop`?
The event loop is what allows JavaScript, despite being single-threaded, to handle asynchronous tasks without blocking, executing them at the right time.

JavaScript runs code on a single main thread, but it can still handle asynchronous operations through the event loop.
The event loop is what allows JavaScript to:
-run synchronous code first
-wait for async tasks in the background
-execute their callbacks later when the stack is free

- What is the difference between `for`, `while` and `do while` loops?

The `for` loop is typically used when the number of iterations is known beforehand. It consists of three parts: initialization, condition, and increment/decrement. For example:
```javascript
for (let i = 0; i < 5; i++) {
  console.log(i);
}
```
The `while` loop is used when the number of iterations is not known and the loop needs to continue until a certain condition is met. The condition is evaluated before each iteration. For example:
```javascript
let i = 0;
while (i < 5) {
  console.log(i);
  i++;
}
```
The `do while` loop is similar to the `while` loop, but the condition is evaluated after the loop body is executed. This means that the loop body will always be executed at least once, even if the condition is false. For example:
```javascript
let i = 0;
do {
  console.log(i);
  i++;
} while (i < 5);
```

- What is the difference between `if`, `else if` and `else` statements?

The `if` statement is used to execute a block of code if a specified condition is true. For example:
```javascript
if (x > 10) {
  console.log("x is greater than 10");
}
```
The `else if` statement is used to specify a new condition to test if the previous `if` condition is false. You can have multiple `else if` statements to check for different conditions. For example:
```javascript
if (x > 10) {
  console.log("x is greater than 10");
} else if (x === 10) {
  console.log("x is equal to 10");
} else {
  console.log("x is less than 10");
}
```
The `else` statement is used to execute a block of code if all the previous conditions are false. It is optional and can be omitted if not needed. For example:
```javascript
if (x > 10) {
  console.log("x is greater than 10");
} else {
  console.log("x is less than or equal to 10");
}
```
### Ternaty operator
The ternary operator is a shorthand way of writing an `if-else` statement.

The syntax is:
```javascript
condition ? expressionIfTrue : expressionIfFalse
```

For example:
```javascript  const age = 18;
const canVote = age >= 18 ? "Yes" : "No";
console.log(canVote); // "Yes"
```

```javascript status = 'offline';
let color = status === 'offline' ? 'red' : 'blue';
console.log(color); // Output: 'red'
```

### Operators
- What is the difference between `==` and `===`?

The `==` operator compares two values for equality after performing type coercion if necessary. It will convert the operands to a common type before making the comparison. For example:
```javascript
console.log(5 == "5");   // true
console.log(0 == false); // true
console.log(null == undefined); // true
```
The `===` operator, also known as the strict equality operator, compares two values for equality without performing type coercion. It checks both the value and the type of the operands. For example:
```javascript
console.log(5 === "5"); // false
console.log(0 === false); // false
console.log(null === undefined); // false
```

### What is the difference between microtask and macrotask?

- Microtask
A microtask has higher priority.
It runs right after the current synchronous code finishes, before the event loop moves to the next macrotask.

Common examples:
```javascript
Promise.then()
Promise.catch()
Promise.finally()
queueMicrotask()
```

- Macrotask
A macrotask has lower priority.
It runs after all microtasks have been processed and the event loop is ready to handle the next macrotask.

Common examples:
```javascript
setTimeout()
setInterval()
DOM events like clicks
setImmediate() in Node.js
```
The order is usually:

Run synchronous code
Run all microtasks
Run the next macrotask

```javascript
console.log("start");
setTimeout(() => {
  console.log("macrotask");
}, 0);

Promise.resolve().then(() => {
  console.log("microtask");
});

console.log("end");
Output:
> start
> end
> microtask
> macrotask
```

- Difference between Typescript and Javascript?
- What is the difference between function declaration and function expression?
- What is the difference between arrow function and regular function?
- What is the difference between call, apply and bind?
- What is the difference between synchronous and asynchronous code?
- What is the difference between callback and promise?
- What is the difference between promise and async/await?
- What is the difference between event loop and call stack?
- What is the difference between hoisting and scoping?
- What is the difference between closure and scope?
- What is the difference between prototype and class?
- What is the difference between object and class?
- What is the difference between object and array?
- What is the difference between object and function?
- What is the difference between object and primitive?
- What is the difference between object and reference?
- What is the difference between object and value?
- What is the difference between object and type?
- What is the difference between object and instance?
- What is the difference between object and property?
- What is the difference between object and method?
- What is the difference between object and constructor?

---