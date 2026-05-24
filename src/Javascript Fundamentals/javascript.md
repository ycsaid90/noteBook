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

- Math Methods
```javascript
console.log(Math.PI); // 3.141592653589793
console.log(Math.sqrt(16)); // 4 (square root of 16)
console.log(Math.pow(2, 3)); // 8  (2 raised to the power of 3)
console.log(Math.abs(-5)); // 5 (absolute value)
console.log(Math.floor(3.7)); // 3 (floor rounds down to the nearest integer)
console.log(Math.ceil(3.2)); // 4  (ceil rounds up to the nearest integer)
console.log(Math.round(3.5)); // 4  (round rounds to the nearest integer)
console.log(Math.max(1, 5, 3)); // 5 (max returns the largest of the given numbers)
console.log(Math.min(1, 5, 3)); // 1 (min returns the smallest of the given numbers)
console.log(Math.random()); // returns a random number between 0 (inclusive) and 1 (exclusive)
```
example:
```javascript
const randomInt = Math.floor(Math.random() * 10) + 1; // generates a random integer between 1 and 10
console.log(randomInt);
```

- Types in javascript

Primitives (7): `string`, `number`, `boolean`, `null`, `undefined`, `symbol`, `bigint`

Non primitives: `object`, `array`, `function`

- String Methods
```javascript
const str = " Hello, World!";
console.log(str.trim()); // "Hello, World!"  (removes whitespace from both ends)
console.log(str.length); // 13               (length of the string)
console.log(str.toUpperCase()); // "HELLO, WORLD!" (converts to uppercase)
console.log(str.toLowerCase()); // "hello, world!"  (converts to lowercase)
console.log(str.includes("World")); // true     (checks if "World" is in the string)
console.log(str.indexOf("o")); // 4        (returns the index of the first occurrence of "o" and is toLowerCase sensitive)
console.log(str.slice(0, 5)); // "Hello"    (slices the string from index 0 to 5)
console.log(str.replace("World", "JavaScript")); // "Hello, JavaScript!" (replaces "World" with "JavaScript")
```
> [!NOTE]
- Difference between concatenation and interpolation?

- Concatenation is the process of joining two or more strings together using the `+` operator. For example:
```javascript
const firstName = "Ana";
const lastName = "Smith";
```
```javascript
const fullName = firstName + " " + lastName; // "Ana Smith"
```
- Interpolation, on the other hand, is a way to embed expressions within a string using template literals (enclosed in backticks ``). It allows you to include variables and expressions directly within the string
```javascript
const fullName = `${firstName} ${lastName}`; // "Ana Smith"
```

> [!NOTE]
- When you use `typeof` operator on a variable, it will return the type of the variable as a string. For example:
```javascript
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
- Operators: Difference between `==` and `===`?

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

- What is the difference between `null` and `undefined`?

    `undefined` means a variable has been declared but has not been assigned a value. It is the default value of uninitialized variables and function parameters that are not provided.

    `null` means intentional absence of value.

### Cookies

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
```javascript
fruits.push("grape"); // adds "grape" to the end of the array
console.log(fruits); // ["apple", "banana", "orange", "grape"]
```
```javascript
fruits.pop(); // removes the last element ("grape") from the array
console.log(fruits); // ["apple", "banana", "orange"]
```

- Shift and Unshift
```javascript
fruits.unshift("grape"); // adds "grape" to the beginning of the array
console.log(fruits); // ["grape", "apple", "banana", "orange"]
```
```javascript
fruits.shift(); // removes the first element ("grape") from the array
console.log(fruits); // ["apple", "banana", "orange"]
```

### Functions
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
- Ternaty operator
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

### Microtask and Macrotask

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



---