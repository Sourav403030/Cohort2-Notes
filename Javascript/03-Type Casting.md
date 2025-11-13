# Type Casting

Created time: July 20, 2025 7:46 PM
Difficulty: Beginner
Last edited time: July 20, 2025 7:59 PM
Status: Done

## 👉 Type Conversion (Explicit Type Casting)

- The user converts from one data type to another explicitly.

```tsx
String(123);      // "123"
Number("42");     // 42
Boolean(1);     // true
Boolean(0);     // false
```

## 👉 Type Coercion (Implicit Type Casting)

- The Javascript itself converts one data type to another when performing some operations.

```tsx
"5" + 1    // "51" → number is coerced to string
"5" - 1    // 4    → string is coerced to number

true + 1   // 2 → true is coerced to 1
false * 10 // 0

'5' == 5       // true → '5' is coerced to number
'5' === 5      // false → no coercion (strict equality)
```

## 👉 Truthy and Falsy values

### ❗️ Truthy values

- All objects
- Non-zero numbers
- Non-empty strings (`"hello"`)
- `[]`, `{}`, `function() {}`

### ❗️ Falsy values

- `false`
- `0`, `0`
- `""` (empty string)
- `null`, `undefined`
- `NaN`

## 👉 NaN - Not a Number

```tsx
typeof NaN // "number"
```

- Even though it means “Not a Number”, NaN is actually of time `number`.
- This is because operations like `0/0` or `parseInt(”abc”)` still produce a numeric result - just an invalid one.