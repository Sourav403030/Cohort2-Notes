# Equality Comparisons

Created time: July 20, 2025 11:30 PM
Difficulty: Beginner
Last edited time: July 21, 2025 6:51 PM
Status: Done

## 👉 `==` (Loose Equality)

- Checks for equality after doing type coercion.
- Javascript will convert the values to the same type before comparing.

```jsx
"5" == 5        // true → string "5" is coerced to number 5
true == 1       // true → true becomes 1
null == undefined // true → considered equal
```

- `==` can lead to confusing bugs. Avoid it unless you really know what you are doing.

## 👉 `===` (Strict Equality)

- Checks for equality without type coercion.
- Both type and value must match exactly.

```jsx
5 === 5           // true
"5" === 5         // false
true === 1        // false
null === undefined // false
```

- This is the recommended operator in many cases.

## 👉 `Object.is()` (Same value Equality)

- It is like `===` but with two subtle differences.
- It treats `NaN` as equal to `NaN`.
- It distinguishes `+0` and `-0` .

```jsx
Object.is(5, 5);           // true
Object.is("hello", "hello"); // true
Object.is(NaN, NaN);       // true ✅ (Unlike `===`)
Object.is(+0, -0);         // false ✅ (Unlike `===`)
```