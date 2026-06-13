# JavaScript Fundamentals

## Key Concepts Map

| Area | Main Concept | Why It Matters |
|---|---|---|
| Variables | `var`, `let`, `const` | Prevent scope bugs and accidental reassignment |
| Types | Primitive vs non-primitive | Helps with comparisons and debugging |
| Strings | Concatenation vs template literals | Cleaner and safer string building |
| Operators | `==` vs `===` | Avoids unexpected type coercion |
| Arrays | Push/pop/shift/unshift | Core list operations |
| Functions | Declaration, expression, arrow, params | Reusable and readable logic |
| Control Flow | Loops, conditions, ternary | Decision-making and iteration |
| Async Model | Event loop, microtask, macrotask | Understand execution order |
| Browser Storage | Session Storage, Local Storage, Cookies | Choose correct persistence mechanism |


## Variables and Types

### `var` vs `let` vs `const`
| Feature      | `var`           | `let`        |    `const`   |
|--------------|-----------------|--------------|--------------|
| Scope        | Function-scoped | Block-scoped | Block-scoped |
| Reassignable |     ✅ Yes      |    ✅ Yes    |    ❌ No    |
| Redeclarable |     ✅ Yes      |    ❌ No     |    ❌ No    |

```javascript
var x = 10;
var x = 20; // allowed
console.log(x); // 20

if (true) {
  var a = 5; // ignores block scope
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
// x = 20; // Error

const user = { name: "Ana" };
user.name = "Luis"; // allowed (mutating object content)
// user = {}; // Error
```

### JavaScript Types

- Primitive types: `string`, `number`, `boolean`, `null`, `undefined`, `symbol`, `bigint`
- Non-primitive types: `object`, `array`, `function`

### `typeof` quick examples

```javascript
console.log(typeof "Hello"); // "string"
console.log(typeof 42); // "number"
console.log(typeof 9007199254740991n); // "bigint"
console.log(typeof true); // "boolean"
console.log(typeof Symbol("id")); // "symbol"
console.log(typeof undefined); // "undefined"
console.log(typeof { name: "Ana" }); // "object"
console.log(typeof [1, 2, 3]); // "object"
console.log(typeof null); // "object" (historical JavaScript behavior)
console.log(typeof function () {}); // "function"
```

### `null` vs `undefined`

- `undefined`: declared, but no value assigned yet.
- `null`: intentional absence of value.

## Strings

### Common string methods

```javascript
const str = " Hello, World!";

console.log(str.trim()); // "Hello, World!"
console.log(str.length); // 13
console.log(str.toUpperCase()); // "HELLO, WORLD!"
console.log(str.toLowerCase()); // "hello, world!"
console.log(str.includes("World")); // true
console.log(str.indexOf("o")); // 4
console.log(str.slice(0, 5)); // "Hello"
console.log(str.replace("World", "JavaScript")); // "Hello, JavaScript!"
```

### Concatenation vs interpolation

```javascript
const firstName = "Ana";
const lastName = "Smith";

const fullName1 = firstName + " " + lastName; // concatenation
const fullName2 = `${firstName} ${lastName}`; // interpolation
```

## Operators

### `==` vs `===`

- `==` compares values after type coercion.
- `===` compares value and type (strict comparison).

```javascript
console.log(5 == "5"); // true
console.log(0 == false); // true
console.log(null == undefined); // true

console.log(5 === "5"); // false
console.log(0 === false); // false
console.log(null === undefined); // false
```

## Math Utilities

```javascript
console.log(Math.PI);
console.log(Math.sqrt(16));
console.log(Math.pow(2, 3));
console.log(Math.abs(-5));
console.log(Math.floor(3.7));
console.log(Math.ceil(3.2));
console.log(Math.round(3.5));
console.log(Math.max(1, 5, 3));
console.log(Math.min(1, 5, 3));
console.log(Math.random());
```

```javascript
const randomInt = Math.floor(Math.random() * 10) + 1;
console.log(randomInt); // 1..10
```

## Arrays

```javascript
const fruits = ["apple", "banana", "orange"];
const numbers = [1, 2, 3, 4, 5];
const mixed = ["hello", 42, true];
```

### Common array operations

```javascript
fruits.push("grape"); // add at end
fruits.pop(); // remove from end

fruits.unshift("grape"); // add at start
fruits.shift(); // remove from start
```

## Functions

| Function Type | Example | Notes |
|---|---|---|
| Declarative Function | `function greet(name) { return \`Hello, ${name}!\`; }` | Named function declaration; can be hoisted |
| Anonymous Function | `const greet = function(name) { return \`Hello, ${name}!\`; };` | Function expression assigned to a variable |
| Arrow Function | `const greet = (name) => { return \`Hello, ${name}!\`; };` | Short syntax; lexical `this` |
| Arrow Function (short) | `const greet = name => \`Hello, ${name}!\`;` | Implicit return |
| Default Parameter | `function greet(name = "Guest") { return \`Hello, ${name}!\`; }` | Uses fallback when arg is missing |
| Rest Parameters | `function sum(...numbers) { return numbers.reduce((t, n) => t + n, 0); }` | Collects arguments into an array |
| Import Function | `import { greet } from "./greet.js";` | Imports named export |

## Loops and Conditionals

### Event loop (main idea)

JavaScript runs on a single main thread. The event loop allows async callbacks to run when the call stack is free.

- Run synchronous code first
- Wait for async tasks
- Execute queued callbacks when possible

### `for`, `while`, `do...while`

```javascript
for (let i = 0; i < 5; i++) {
  console.log(i);
}
```

```javascript
let i = 0;
while (i < 5) {
  console.log(i);
  i++;
}
```

```javascript
let i = 0;
do {
  console.log(i);
  i++;
} while (i < 5);
```

### `if`, `else if`, `else`

```javascript
if (x > 10) {
  console.log("x is greater than 10");
} else if (x === 10) {
  console.log("x is equal to 10");
} else {
  console.log("x is less than 10");
}
```

### Ternary operator

```javascript
const age = 18;
const canVote = age >= 18 ? "Yes" : "No";
console.log(canVote);
```

```javascript
const status = "offline";
const color = status === "offline" ? "red" : "blue";
console.log(color); // "red"
```

## Microtask vs Macrotask

- **Microtask**: runs right after current sync code, before next macrotask.
  - Examples: `Promise.then`, `Promise.catch`, `Promise.finally`, `queueMicrotask`
- **Macrotask**: runs after microtasks are drained.
  - Examples: `setTimeout`, `setInterval`, DOM events, `setImmediate` (Node.js)

```javascript
console.log("start");

setTimeout(() => {
  console.log("macrotask");
}, 0);

Promise.resolve().then(() => {
  console.log("microtask");
});

console.log("end");

// Output:
// start
// end
// microtask
// macrotask
```

## Cookies vs Session Storage vs Local Storage

| Feature | Session Storage | Local Storage | Cookies |
|---|---|---|---|
| Scope | Per tab/session | Persistent | Persistent |
| Expiration | Browser/tab close | Never (unless cleared) | Defined by expiration/max-age |
| Storage Limit | ~5-10 MB | ~5-10 MB | ~4 KB |
| Sent to server automatically | No | No | Yes |
| Common Use Case | Temporary page/session state | Long-lived UI preferences | Auth/session tokens and server needs |


````javascript
let date = new Date();
const formattedDate = date.toISOString().split('T')[0];
console.log(`Formatted date: ${formattedDate}`);  2026-06-12
````

####
> [!IMPORTANT]
> API
```javascript
response = await page.request.get('https://example.com/api/data');
response.json() -> Parses the response body as JSON and returns a JavaScript object.
response.text() -> Parses the response body as text and returns a string.
response.status() -> Returns the HTTP status code of the response.
response.ok() -> Returns true if the status code is in the range 200-299, otherwise false.
JSON.stringify(object) -> Converts a JavaScript object to a JSON string.
JSON.parse(string) -> Parses a JSON string and returns a JavaScript object.
````
> [!IMPORTANT]
> Desestructurar en JavaScript
````javascript
  const {status, body} = response; - Desestructuración para extraer el status y el body de la respuesta.
  const {status, body: { data: { meta: { message } } }} = response; - Desestructuración anidada para extraer el mensaje del meta dentro del data del body de la respuesta.
  const { status, body: {data, data: { meta: { message } } } } = response;

````

````javascript
if (![200, 201].includes(status))  - Verifica si el status de la respuesta no es 200 o 201, lo que indica un error en la solicitud.

````

> [!IMPORTANT]
> List and Dropdown
```javascript
await page.getByRole('list')        //When the List has a UL tag
await page.getByRole('listitem');   //When the List has a LI tag
````