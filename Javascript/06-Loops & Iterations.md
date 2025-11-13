# Loops and Iterations

Created time: July 21, 2025 6:51 PM
Difficulty: Beginner
Last edited time: July 21, 2025 8:04 PM
Status: Done

## 👉 Loops

- Loops help us repeat code without rewriting it.
- If a task needs to be done multiple times(eg: printing 1-10, going through an array, or checking each character in a string), loops are the backbone.

## 👉 For loop

```jsx
for (let i = 0; i < 5; i++) {
	console.log(i);
}
```

- Start from `i = 0`
- Run till  `i < 5`
- Increase `i` each time

## 👉 While loop

```jsx
let i = 0;
while (i < 5) {
	console.log(i);
	i++;
}
```

- Condition is checked before running.

## 👉 do-while loop

```jsx
let i = 0;
do {
	console.log(i);
	i++;
} while (i < 5);
```

- Run at least once even if condition is false.

## 👉 `break` and `continue`

- `break` : Exit loop completely.
- `continue` : Skip current iteration and move to next.

```jsx
for (let i = 1; i <= 5; i++) {
	if (i === 3) continue;
	console.log(i); // Skips 3
}
```

## 👉 `for-of` - Strings and Arrays

```jsx
for (let char of "Sheryians") {
	console.log(char);
}
```

- Works on anything iterable(arrays, strings)

## 👉 `forEach` - Arrays

```jsx
let nums = [10, 20, 30];
	nums.forEach((num) => {
	console.log(num);
});
```

- Cleaner than `for` for arrays, but you can’t `break` or `return`.

## 👉 `for-in` - Objects (and Arrays if needed)

```jsx
let user = { name: "Harsh", age: 26 };
for (let key in user) {
	console.log(key, user[key]);
}
```

- Goes over keys in objects