# Data Structures

Created time: July 20, 2025 10:03 PM
Difficulty: Intermediate
Last edited time: October 30, 2025 12:27 PM
Status: Done

## 👉 Keyed Data Structures

- It stores values associated with keys.
- You can retreive, update, or delete values by referencing with keys.

## 👉 Map

### ❗️ What is a Map?

- It is a collection of key-value pairs where keys can be of any type (Not just strings).
- Values are retreived using those keys.
- Insertion order is preserved.

### ❗️Why use Map over Object?

| Feature | `Object` | `Map` |
| --- | --- | --- |
| Key Types | Only strings & symbols | Any value (object, array, function, etc.) |
| Order of keys | Not guaranteed (before ES2015) | Preserved |
| Iteration | Manual (`for...in`, `Object.keys`) | Easy (`for...of`, `.entries()`) |
| Performance | Slower with frequent inserts/removes | Optimized for frequent operations |
| Size | No direct `.size` property | Has `.size` |

### ❗️Creating a Map

```tsx
const map = new Map();

//OR

const map = new Map([
  ["name", "Sourav"],
  ["age", 25]
]);
```

### ❗️Adding entries to Map

```tsx
const myFunction = function(){}

map.set("city", "New York");
map.set(1, "one");
map.set(true, "boolean");
map.set(myFunction, "function");
map.set({id: 1}, "object");
map.set([1,2,3,4,5], "array");
```

### ❗️Get Values

```jsx
map.get("city") // "New York"
```

### ❗️Check Existence

```jsx
map.has(1);  // true
```

### ❗️Delete Entries

```jsx
map.delete(myFunction); // myFunction will be deleted from the Map
```

### ❗️Size of Map

```jsx
console.log(map.size); // number of key-value pairs
```

### ❗️Clear all entries

```jsx
map.clear();
```

### ❗️Iterating through Map

```jsx
const myMap = new Map([
  ["name", "John"],
  ["role", "Developer"]
]);

for (let [key, value] of myMap) {
  console.log(key, value);
}

//OR

myMap.keys();     // iterator for keys
myMap.values();   // iterator for values
myMap.entries();  // iterator for [key, value] pairs
```

## 👉 Weak Map

### ❗️What is a Weak Map?

- It is a key-value data structure similar to Map, but the keys must be Objects.
- Keys are weakly held - they dont prevent garbage collection.

### ❗️Features of Weak Map

| Feature | Description |
| --- | --- |
| 🔐 **Only objects as keys** | No strings, numbers, or other primitives allowed |
| 🧠 **Weak references** | If no other references to the key object exist, it can be **garbage collected** |
| 🚫 **Not iterable** | You can't loop over a `WeakMap` |
| 🚫 **No size property** | You can’t count entries like `map.size` |

### ❗️Creating and using Weak Map

```jsx
const obj = { name: "John" };

const wm = new WeakMap();
wm.set(obj, "secret info");

console.log(wm.get(obj)); // "secret info"
```

### ❗️Basic Methods

| Method | Description |
| --- | --- |
| `set(key, value)` | Adds or updates the entry |
| `get(key)` | Retrieves the value |
| `has(key)` | Checks if the key exists |
| `delete(key)` | Removes the entry |

```jsx
wm.has(obj);       // true
wm.delete(obj);    // removes the key
```

### ❗️Why “Weak”?

- Because the keys are weakly referenced - If there’s no other reference to the key object outside the `WeakMap` , It can be garbage collected automatically, freeing memory.

```jsx
let user = { name: "John" };
const weakMap = new WeakMap();

weakMap.set(user, "metadata");

// Remove reference
user = null; // The { name: "John" } object is now garbage collectible
```

- In a regular `Map`, the object would still be strongly referenced and memory would not be freed.

### ❗️WeakMap v/s Map

| Feature | `Map` | `WeakMap` |
| --- | --- | --- |
| Keys can be | Any type | **Only objects** |
| Keys are held | Strongly | **Weakly** |
| Iterable | ✅ Yes | ❌ No |
| Size property | ✅ Yes | ❌ No |
| Garbage collection | ❌ Blocked | ✅ Allowed |
| Use case | General-purpose | Private data, memory-sensitive caching |

## 👉 Set

### ❗️What is a Set?

- A Set is a built-in data structure introduced in ES6 that lets you store a collection of unique values - meaning no duplicates are allowed.

### ❗️Key characteristics of Set

| Feature | Description |
| --- | --- |
| ✅ **No duplicates** | Automatically removes duplicates |
| ✅ **Any value type** | Can store numbers, strings, objects, functions |
| ✅ **Order is preserved** | Iterates in the order of insertion |
| ✅ **Iterable** | Can loop using `for...of` or `forEach` |

### ❗️Creating a Set

```jsx
const set = new Set();

//OR

const set = new Set([1, 2, 3, 3, 4]);
console.log(set); // Set(4) {1, 2, 3, 4}
```

### ❗️Basic Methods

| Method | Description |
| --- | --- |
| `add(value)` | Adds a value |
| `has(value)` | Checks if value exists |
| `delete(value)` | Removes a value |
| `clear()` | Removes all values |
| `size` | Number of elements |

```jsx
const set = new Set();

set.add(1);
set.add("hello");
set.add(1); // duplicate, won't be added

console.log(set.has(1));     // true
console.log(set.size);       // 2

set.delete("hello");
set.clear();                 // removes all values

```

### ❗️Iterating a Set

```jsx
const numbers = new Set([10, 20, 30]);

for (let num of numbers) {
  console.log(num);
}

numbers.forEach(val => console.log(val));
```

### ❗️Use Case - Removing duplicates from Array

```jsx
const nums = [1, 2, 2, 3, 4, 4, 5];
const unique = [...new Set(nums)];
console.log(unique); // [1, 2, 3, 4, 5]
```

### ❗️Set can store any type

```jsx
const set = new Set();

set.add(42);
set.add("hello");
set.add({ id: 1 });
set.add([1, 2]);

console.log(set.size); // 4 — all values are unique references
```

### ❗️Set v/s Array

| Feature | `Array` | `Set` |
| --- | --- | --- |
| Allows duplicates | ✅ Yes | ❌ No |
| Index-based | ✅ Yes | ❌ No |
| Order preserved | ✅ Yes | ✅ Yes |
| Performance (lookup) | Slower (O(n)) | Faster (O(1)) |

## 👉 Weak Set

### ❗️What is Weak Set?

- It is a collection of only objects where each objects appear only once.
- The object references are weakly held.
- It is not iterable and doesnot expose its contents.

### ❗️Key features of Weak Set

| Feature | Description |
| --- | --- |
| ✅ **Only stores objects** | No strings, numbers, arrays, or functions |
| ✅ **No duplicates** | Just like `Set`, values are unique |
| ✅ **Weak references** | If no other references to an object exist, it can be garbage collected |
| ❌ **Not iterable** | Cannot loop over a `WeakSet` |
| ❌ **No size or entries** | No `.size`, `.keys()`, or `.values()` |

### ❗️Creating a Weak Set

```jsx
const ws = new WeakSet();

//OR

const obj1 = { name: "obj1" };
const obj2 = { name: "obj2" };

const ws = new WeakSet([obj1, obj2]);
```

### ❗️Basic Methods

| Method | Description |
| --- | --- |
| `add(obj)` | Adds an object |
| `has(obj)` | Checks if an object is in the set |
| `delete(obj)` | Removes the object |

```jsx
const ws = new WeakSet();

const user = { name: "Sourav" };
ws.add(user);

console.log(ws.has(user)); // true

ws.delete(user);
console.log(ws.has(user)); // false
```

### ❗️Garbage Collection

```jsx
let person = { name: "Sourav" };

const ws = new WeakSet();
ws.add(person);

// Remove the only reference to the object
person = null;

// Now the object is eligible for garbage collection
```

- Since `WeakSet` holds a weak reference, the object will be cleaned up automatically by the Javascript engine when no other reference exist.

### ❗️WeakSet v/s Set

| Feature | `Set` | `WeakSet` |
| --- | --- | --- |
| Value types allowed | Any | Objects only |
| Iterable? | ✅ Yes | ❌ No |
| Can check `.size`? | ✅ Yes | ❌ No |
| Garbage-collected keys? | ❌ No | ✅ Yes |
| Use Case | General-purpose | Memory-efficient object tracking |

### 👉Javascript Object Notation (JSON)

### ❗️What is JSON?

- It is a light-weight, text-based format used to represent structured data in a readable and machine parsable way.
- Store data in a file or database.
- Exchange data between server and client (API).

### ❗️JSON is based on Javascript Objects

```jsx
// JavaScript Object
const obj = {
  name: "Sourav",
  age: 25,
  isStudent: false
};

// JSON (as a string)
const json = `{
  "name": "Sourav",
  "age": 25,
  "isStudent": false
}`;
```

### ❗️Key rules of JSON syntax

| Rule | Example |
| --- | --- |
| Data is in key-value pairs | `"name": "Sourav"` |
| Keys **must be strings** (in double quotes) | ✅ `"age": 25`, ❌ `age: 25` |
| Values can be string, number, boolean, array, object, or null | `"active": true` |
| No functions, comments, or undefined allowed | ❌ `"greet": function() {}` |

### ❗️Common JSON data types

```jsx
{
  "string": "hello",
  "number": 42,
  "boolean": true,
  "null": null,
  "array": [1, 2, 3],
  "object": { "key": "value" }
}
```

### ❗️Convert JS object into JSON

```jsx
const obj = { name: "John", age: 25 };
const jsonStr = JSON.stringify(obj);
console.log(jsonStr); // '{"name":"John","age":25}'

```

### ❗️Convert JSON into JS object

```jsx
const jsonStr = '{"name":"John","age":25}';
const obj = JSON.parse(jsonStr);
console.log(obj.name); // John
```

## 👉 Arrays

### ❗️What is an Array?

- An Array is like a row of boxes, where each box holds a value and has an index `(0,1,2…)`
- Array helps you store multiple values in a single variable - numbers, strings or even objects/functions.

```jsx
let fruits = ["apple", "banana", "mango"];
```

### ❗️Key Characteristics

| Feature | Value |
| --- | --- |
| ✅ Ordered | Elements maintain their insertion order |
| ✅ Indexed | Starts from `0` (zero-based index) |
| ✅ Dynamic | Can grow or shrink in size |
| ✅ Heterogeneous | Can store mixed data types |
| ✅ Iterable | Can be looped using `for`, `for...of`, etc. |

### ❗️Creating and Accessing Arrays

```jsx
let marks = [90, 85, 78];
console.log(marks[1]); // 85
marks[2] = 80; // Update index 2
```

### ❗️Common Methods

- Modifiers (Change the original array)

```jsx
let arr = [1, 2, 3, 4];
arr.push(5); // Add to end
arr.pop(); // Remove last
arr.shift(); // Remove first
arr.unshift(0); // Add to start
arr.splice(1, 2); // Remove 2 items starting at index 1
arr.reverse(); // Reverse order
```

- Extractors (Don’t modify original array)

```jsx
let newArr = arr.slice(1, 3); // Copy from index 1 to 2
arr.sort(); // Lexical sort by default
```

### ❗️Common Iteration methods

- `map()`  : Returns a new array with modified values.

```jsx
let prices = [100, 200, 300];
let taxed = prices.map(p => p * 1.18);
```

- `filter()`  : Filter out elements based on a condition.

```jsx
let nums = [1, 2, 3, 4];
let even = nums.filter(n => n % 2 === 0);
```

- `reduce()`  : Reduces the array to a single value

```jsx
let total = nums.reduce((acc, val) => acc + val, 0);
```

- `forEach()` : Performs an action for each element (but returns undefined)

```jsx
nums.forEach(n => console.log(n));
```

- `find()`, `some()`, `every()`

```jsx
nums.find(n => n > 2);   //First match
nums.some(n => n > 5);   // At least one true
nums.every(n => n > 0);  // All true
```

### ❗️Destructuring and Spread

- **Destructuring** is a syntax that lets you **unpack values from arrays or properties from objects** into individual variables.

```jsx
const arr = [1, 2, 3];

const [a, b, c] = arr;

console.log(a); // 1
console.log(b); // 2
console.log(c); // 3
```

- The **spread operator (`...`)** is used to **expand** arrays or objects.

```jsx
const arr1 = [1, 2];
const arr2 = [...arr1, 3, 4];

console.log(arr2); // [1, 2, 3, 4]
```