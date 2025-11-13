# Control Flow

Created time: July 21, 2025 8:04 PM
Difficulty: Beginner
Last edited time: July 21, 2025 8:42 PM
Status: Done

## 👉 Conditional Statements

- Control flow decides which code to run, when it runs and how many times it runs.
- It is like decision-making + direction in your Javascript programme.
- If operators are the verbs then control flow is the traffic signal.

### ❗️`if-else`

```jsx
if (condition) {
// runs if condition is true
} else if (anotherCondition) {
// runs if first was false, second is true
} else {
// runs if none are true
}
```

- Example

```jsx
let marks = 78;
if (marks >= 90) {
	console.log("A");
} else if (marks >= 75) {
	console.log("B");
} else {
	console.log("C");
}
```

### ❗️`switch`

- Great for checking one variable against many values.

```jsx
switch (value) {
case value1:
// code
break;
case value2:
// code
break;
default:
// fallback
}
```

- Example

```jsx
let fruit = "apple";
switch (fruit) {
	case "banana":
		console.log("Yellow");
		break;
	case "apple":
		console.log("Red");
		break;
	default:
		console.log("Unknown");
}
```

### ❗️Early `return` pattern

- Used in functions to exit early if some condition fails.

```jsx
function checkAge(age) {
if (age < 18) return "Denied";
return "Allowed";
}
```

- This allows deep nesting and makes logic cleaner.

## 👉 Exception Handling

- It is the process of detecting and dealing with errors that occur during the execution of a program.

```jsx
try {
  // code that might throw an error
} catch (err) {
  // handle the error
} finally {
  // optional: always runs
}
```

### ❗️`throw` statement

- It lets you create a custom `error` and stop code execution at that point. The error is then caught by the nearest `catch` block (if exisits).

```jsx
throw new Error("Invalid input!");
```

### ❗️Error Object

- An **Error Object** in JavaScript is a built-in object that represents **an error that occurred during code execution**. It contains **information about the error**, such as its type, message, and location in the code.

```jsx
const error = new Error("Something went wrong!");
console.log(error.name);    // "Error"
console.log(error.message); // "Something went wrong!"
console.log(error.stack);   // Stack trace of where error occurred
```

### ❗️Built in Error types

| Error Type | Use Case Example |
| --- | --- |
| `Error` | Generic errors |
| `TypeError` | Wrong data type (e.g., calling a non-function) |
| `ReferenceError` | Using a variable that’s not declared |
| `SyntaxError` | Invalid code syntax (usually at compile time) |
| `RangeError` | Value out of expected range |
| `URIError` | Invalid URI encoding/decoding |
| `EvalError` | (Rare) Problems with `eval()` function |