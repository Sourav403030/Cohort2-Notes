# Asynchronous JS

Created time: July 21, 2025 11:52 PM
Difficulty: Intermediate
Last edited time: July 22, 2025 12:06 AM
Status: Done

## 👉 setTimeout

- `setTimeout()` is a function that **executes code once after a specified delay** (in milliseconds).

```jsx
setTimeout(() => {
  console.log("Executed after 2 seconds");
}, 2000);
```

## 👉 setInterval

- `setInterval()` is a function that **repeatedly executes code at fixed intervals**.

```jsx
setInterval(() => {
  console.log("Repeats every 1 second");
}, 1000);
```

## 👉 Difference between setTimeout and setInterval

| Feature | `setTimeout()` | `setInterval()` |
| --- | --- | --- |
| Runs | Once after delay | Repeats at fixed intervals |
| Use for | Delay before executing code | Repeating tasks (polling, timers) |
| Can be stopped? | Yes, using `clearTimeout()` | Yes, using `clearInterval()` |
| Returns | Timeout ID | Interval ID |

## 👉 Callbacks

- A **callback** is a **function passed as an argument to another function**, which is then **executed later** — either **after an operation completes** or **when a condition is met**.

```jsx
function greet(name, callback) {
  console.log("Hello, " + name);
  callback(); // function is called later
}

function afterGreet() {
  console.log("Welcome to JavaScript!");
}

greet("John", afterGreet);

// Output:
// Hello, John
// Welcome to JavaScript!

```

- Here, `afterGreet` is a **callback function** — it runs **after** the main action.

## 👉 Callback Hell

- **Callback hell** refers to a situation in JavaScript where **callbacks are nested within callbacks** many levels deep, making the code **hard to read, hard to debug, and hard to maintain**.

Problem:

- Indentation gets deeper and deeper
- Code becomes unreadable
- Error handling becomes messy
- Logic becomes tightly coupled

```jsx
doTask1(function (res1) {
  doTask2(res1, function (res2) {
    doTask3(res2, function (res3) {
      doTask4(res3, function (res4) {
        console.log("All tasks done!");
      });
    });
  });
});
```

## 👉 Promise

- A **Promise** is an object in JavaScript that represents the **eventual completion (or failure)** of an asynchronous operation and its **result value**.

### ❗️States of a Promise

| State | Meaning |
| --- | --- |
| `pending` | Operation is still in progress |
| `fulfilled` | Operation completed successfully |
| `rejected` | Operation failed with an error |

### ❗️Creating a Promise

```jsx
const promise = new Promise((resolve, reject) => {
  // async operation
  const success = true;

  if (success) {
    resolve("✅ Operation successful");
  } else {
    reject("❌ Something went wrong");
  }
});

//OR

promise
  .then((result) => {
    console.log(result); // if resolved
  })
  .catch((error) => {
    console.log(error);  // if rejected
  });

```

- `resolve(value)` — marks promise as **fulfilled**
- `reject(error)` — marks promise as **rejected**

## 👉Async-Await

### `async` keyword

- Marks a function as **asynchronous**.
- It **always returns a Promise**.
- You can use `await` inside it.

```jsx
async function greet() {
  return "Hello";
}

greet().then(console.log); // Hello
```

### `await` keyword

- Can only be used **inside an `async` function**.
- It **waits for the Promise to resolve**.
- It pauses execution until the result is available.

```jsx
async function getData() {
  const result = await Promise.resolve("Done!");
  console.log(result); // Done!
}

getData();
```