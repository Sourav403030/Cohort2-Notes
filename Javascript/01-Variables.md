# All about Variables

## 👉 Variable Declarations

- Variables are containers that hold the data.
- They help us store, reuse and update information in Javascript - from simple values like numbers to complex data like arrays and objects.
- Think of variable as a box with a name on it. You can put something inside it (a value) & later check or change whats inside.
- In Javascript, you can create these boxes using keyword :- `var` `let` `const`

## 👉 var, let, const

- `var` - Old and risky.
    - Scoped to functions, not blocks.
    - Can be re-declared and re-assigned.
    - Hoisted to the top with `undefined` value.
    
    ```jsx
    var code = 20;
    var code = 10 // ✅ OK
    ```
    
- `let` - Modern and safe.
    - Scoped to blocks `({ })`
    - Can be reassigned but not redeclared.
    - Hoisted but stays in the Temporal Dead Zone(TDZ).
    
    ```jsx
    let age = 30;
    age = 40;     // ✅ OK
    let age = 50; // ❌ Error (same block)
    ```
    
- `const` - Constant values.
    - Scoped to block `({ })`
    - Cannot be re-assigned or re-declared.
    - Value must be assigned at declaration.
    - TDZ applies here too.
    
    ```jsx
    const PI = 3.14;
    PI = 3.14159; // ❌ Error
    ```
    
    - But if const holds an object/array, you can still change its contents.
    
    ```tsx
    const student = {name: "Rahul"};
    student.name = "Raj"; // ✅ OK
    student = {};         // ❌ Error
    ```
    

## 👉 Hoisting

- Javascript prepares memory before running code.
- It moves all the declaration to the top - this is called Hoisiting.
- But :-
    - `var` is hoisted and set to `undefined` .
    - let and const are hoisted but not initialised. So accessing them earlier gives `ReferenceError`.
    
    ```tsx
    console.log(a); // undefined
    var a = 10;
    
    console.log(b); // ❌ ReferenceError
    let b = 20;
    ```
    

## 👉 Temporal Dead Zone (TDZ)

- A variable declared with `let` or `const` cannot be accessed before the line where it is declared.

```jsx
console.log(x); // ❌ ReferenceError: Cannot access 'x' before initialization
let x = 5;
```

- Whats happening here :-
    - `x` is hoisted to the top of the scope.
    - But it stays uninitialised unit `let x = 5;` is executed.
    - Trying to access it before initialisation → causes a Reference Error.

## 👉 Variable Naming Rules

- Variable names can only contain alpha-numeric characters `A-Z, a-z, 0-9` and the `_` (underscore) and the `$` (dollar) symbol.
- Names cannot begin with a digit.
- Names cannot contain spaces inbetween.
- Names cannot be reserved keywords.

## 👉 Variable Scopes

- Block Scope :- Code inside `{}` like in loops, if, etc.
- Function Scope :- Code inside a function.
- `let` and `const` follow block scope.
- `var` ignores block scope - which leads to bugs.

```tsx
{
var x = 5;
let y = 10;
const z = 15;
}
console.log(x); // ✅ 5
console.log(y); // ❌ ReferenceError
console.log(z); // ❌ ReferenceError
```