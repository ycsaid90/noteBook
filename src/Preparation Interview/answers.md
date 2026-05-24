# Interview Answers

This page keeps detailed answers for questions listed in `interview.md`.

## Q2 TypeScript vs JavaScript

TypeScript is a superset of JavaScript that adds static typing.

JavaScript is dynamically typed, so type-related errors are often discovered at runtime. JavaScript lets variables change type freely, while TypeScript helps enforce type consistency during development.

TypeScript also adds features and tooling support that are very useful in large codebases (for example, interfaces and stronger IDE feedback).

## Q4 Function declaration vs function expression

A function declaration is named and hoisted, so it can be called before its definition in source order.

```javascript
function greet() {
  console.log("Hello!");
}

greet(); // "Hello!"
```

A function expression is assigned to a variable and is not usable before initialization.

```javascript
const greet = function () {
  console.log("Hello!");
};

greet(); // "Hello!"
```

## Q5 Arrow function vs regular function

An arrow function has shorter syntax and does not bind its own `this`; it inherits `this` from the surrounding scope.

A regular function has its own `this` depending on how it is called.

```javascript
const person = {
  name: "Ana",
  greet: function () {
    console.log("Hello, " + this.name);
  },
};

person.greet(); // "Hello, Ana"

const greetFunction = person.greet;
greetFunction(); // "Hello, undefined" (or global value in non-strict environments)
```

## Q6 JavaScript types

Types in JavaScript are divided into primitives and non-primitives.

- Primitives (7): `string`, `number`, `boolean`, `null`, `undefined`, `symbol`, `bigint`
- Non-primitives: `object`, `array`, `function`

