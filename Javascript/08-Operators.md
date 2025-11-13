# Operators

Created time: July 21, 2025 8:43 PM
Difficulty: Beginner
Last edited time: July 21, 2025 8:48 PM
Status: Done

## 👉 Operators

- Operators are special symbols or keywords in Javascript used to perform operations on values(operands).
- You’ll use them in calculations, comparisons, logic, assignments and even type checks.
- Think of them as verbs of your code - they act on data.

### ❗️Arithmetic Operators

- Used for basic maths.

```jsx
+ // addition
- // subtraction
* // multiplication
/ // division
% // modulus (remainder)
** // exponentiation (power)
```

- Example

```jsx
let a = 10, b = 3;
console.log(a + b); // 13
console.log(a % b); // 1
console.log(2 ** 3); // 8
```

### ❗️Assignment Operators

- Assigns values to variables

```jsx
= // assigns value
+= // a += b => a = a + b
-= // a -= b
*=, /=, %=
```

- Example

```jsx
let score = 5;
score += 2; // score = 7
```

### ❗️Comparison Operators

- Used in condition checks.

```jsx
== // equal (loose)
=== // equal (strict – value + type)
!= // not equal (loose)
!== // not equal (strict)
> < >= <=
```

- Example

```jsx
console.log(5 == "5"); // true
console.log(5 === "5"); // false
```

### ❗️Logical Operators

- Used to combine multiple conditions

```jsx
&& // AND – both must be true
|| // OR – either one true
! // NOT – negates truthiness
```

- Example

```jsx
let age = 20, hasID = true;
if (age >= 18 && hasID) {
console.log("Allowed");
}
```

### ❗️Unary Operators

- Used on a single operand

```jsx
+ // tries to convert to number
- // negates
++ // increment
-- // decrement
typeof // returns data type
```

- Example

```jsx
let x = "5";
console.log(+x); // 5 (converted to number)
```

### ❗️Ternary Operator

- Short hand for `if…else`

```jsx
condition ? valueIfTrue : valueIfFalse
```

- Example

```jsx
let score = 80;
let grade = score > 50 ? "Pass" : "Fail";
```

### ❗️`typeof` Operator

```jsx
typeof 123 // "number"
typeof "hi" // "string"
typeof null // "object" (JS bug)
typeof [] // "object"
typeof {} // "object"
typeof function(){} // "function"
```