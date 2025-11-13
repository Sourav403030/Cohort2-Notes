# Functions

Created time: July 21, 2025 9:26 PM
Difficulty: Beginner
Last edited time: July 21, 2025 10:12 PM
Status: Done

## ❗️ What are Functions?

- Functions are blocks of reusable logic.
- Instead of repeating the same task again and again, wrap it in a function and reuse it with different inputs.

## ❗️Function Declarations

```jsx
function greet() {
	console.log("Welcome to Sheryians!");
}
greet();
```

- You define it once, then call it whenever needed.

## ❗️Parameters v/s Arguments

- `Parameter` - The variable listed in the function definition.
- `Argument` - The actual values you pass to a function when calling it.

```jsx
function greet(name) {
	console.log("Hello " + name);
}
greet("Roy");
```

- `name` is a parameter.
- `Roy` is an argument.

## ❗️Return values

- return sends back a result to wherever the function was called.
- After `return` , function exits.

```jsx
function sum(a, b) {
	return a + b;
}
let total = sum(5, 10); // total is 15
```

## ❗️Arrow function

- An arrow function is a shorter syntax for writing function expressions introduced in ES6.
- It uses the `⇒` arrow instead of the `function` keyword.

```jsx
// Traditional function
function add(a, b) {
  return a + b;
}

// Arrow function
const add = (a, b) => {
  return a + b;
};
```

## ❗️Default values and Rest operator

- Default parameters allow you to **assign a default value** to a function parameter **when no argument is passed** (or if the argument is `undefined`).

```jsx
function greet(name = "Guest") {
  console.log("Hello, " + name);
}

greet("John"); // "Hello, John"
greet();         // "Hello, Guest" → default value used
```

- Rest parameters allow you to **collect all remaining arguments** into an **array**.

```jsx
function sum(...numbers) {
  return numbers.reduce((total, num) => total + num, 0);
}

sum(1, 2, 3, 4); // 10
```

- You can only have **one rest parameter**, and it must be the **last one**.
- The rest parameter is always an **array**.

## ❗️Immediately Invoked Function Expression (IIFE)

- An **IIFE (Immediately Invoked Function Expression)** is a **function that is defined and immediately executed**.
- It creates its own **local scope** and runs **right after it's defined**, without needing to be explicitly called later.

```jsx
(function () {
  // code inside IIFE
})();

//OR

(() => {
  // code inside IIFE
})();

(function () {
  console.log("IIFE ran!");
})(); // Outputs: IIFE ran!

```

## ❗️First Class Functions

Functions can be:

- Assigned to variables
- Passed as arguments
- Returned from other functions
- Stored in data structures

In short: **functions are treated just like any other value (like strings, numbers, objects, etc.).**

### 🎯 Assigning Function to a Variable

```jsx
const greet = function () {
  return "Hello!";
};

console.log(greet()); // "Hello!"
```

### 🎯 Passing Function as an Argument (Higher Order Function)

```jsx
function greet(name) {
  return "Hello, " + name;
}

function processUser(callback) {
  console.log(callback("John"));
}

processUser(greet); // "Hello, John"

```

### 🎯 Returning a Function from another Function (Higher Order Function)

```jsx
function multiplier(x) {
  return function (y) {
    return x * y;
  };
}

const double = multiplier(2);
console.log(double(5)); // 10
```

### 🎯 Storing Functions in Data Structures

```jsx
const operations = [
  function (a, b) { return a + b; },
  function (a, b) { return a - b; }
];

console.log(operations[0](10, 5)); // 15
console.log(operations[1](10, 5)); // 5
```

## ❗️Recursion

- **Recursion** is when a function **calls itself** to solve a problem, breaking it down into **smaller subproblems** until it reaches a base case.
- It’s a technique where **a function solves a part of the problem**, and lets **itself handle the rest**.

```jsx
function factorial(n) {
  if (n === 0 || n === 1) {
    return 1; // base case
  } else {
    return n * factorial(n - 1); // recursive call
  }
}

console.log(factorial(5)); // 120
```

## ❗️Lexical Scoping

- **A variable’s scope is determined by its position in the source code** — specifically, **where it was defined**, not where it was called.

```jsx
function outer() {
  const a = 10;

  function inner() {
    console.log(a); // ✅ inner can access a
  }

  inner();
}

outer();
```

- The `inner()` function **remembers the scope in which it was defined** (inside `outer()`), so it can access `a`.

## ❗️Closures

- A function inside another function can access the outer function’s variables — even after the outer function has returned.
- A **closure** is created when a **function "remembers" the variables** from its **lexical scope**, even after the outer function has finished executing.

```jsx
function outer() {
  const message = "Hello from outer!";

  function inner() {
    console.log(message); // ✅ closure: inner remembers `message`
  }

  return inner;
}

const greet = outer(); // outer() has finished, but `message` is still remembered
greet(); // "Hello from outer!"
```

- Even though `outer()` is no longer running, `inner()` **remembers** `message` because of **closure**.

## ❗️Hoisting in Functions

- Declarations are hoisted.
- Expressions are not.

```jsx
hello(); // works
function hello() {
console.log("Hi");
}

greet(); // error
const greet = function () {
console.log("Hi");
};
```