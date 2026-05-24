1. Typescript is a superset of JavaScript that adds static typing to the language.

> JavaScript, on the other hand, is a dynamically typed language that does not have built-in support for static typing.
This means that in JavaScript, variables can hold values of any type, and type-related errors may only be caught at runtime.
JavaScript does not prevent change the type of a variable, while TypeScript does.

> TypeScript includes features such as interfaces, classes, and modules that are not present in JavaScript, making it a more powerful and flexible language for large-scale applications.

2. What is the difference between function declaration and function expression?
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

3. An arrow function is a shorter syntax for writing functions in JavaScript. It does not have its own `this` context, which means it inherits the `this` value from the enclosing scope. This can be useful when working with callbacks or methods that need to access the `this` value of the surrounding code. For example:
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

- 5. Types in JavaScript are divided in Primitives and Non Primitives
Primitives (7): `string`, `number`, `boolean`, `null`, `undefined`, `symbol`, `bigint`
Non primitives: `object`, `array`, `function`

-6