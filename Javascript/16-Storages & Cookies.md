# Storages & Cookies

Created time: July 23, 2025 9:41 PM
Difficulty: Intermediate
Last edited time: July 23, 2025 9:49 PM
Status: Done

## 👉 `localStorage`

`localStorage` is part of the **Web Storage API** that allows you to store **key-value pairs** in the **browser** with **no expiration time**.

- Data stored in `localStorage` **persists even after page reload or browser restart**.
- Only strings can be stored.

```jsx
localStorage.setItem('key', 'value');        // Save data
localStorage.getItem('key');                 // Retrieve data
localStorage.removeItem('key');              // Remove specific item
localStorage.clear();                        // Remove all items
localStorage.length                          // Number of stored items
localStorage.key(index);                     // Get key by index
```

- If you try to store an object or array directly, it will be converted to `[object Object]`.
- Use `JSON.stringify()` to store

```jsx
const user = {
  name: 'John',
  age: 22
};

localStorage.setItem('user', JSON.stringify(user));
```

- Use `JSON.parse()` to retrieve.

```jsx
const userData = JSON.parse(localStorage.getItem('user')); //{name: John, age:22}
console.log(userData.name); // "John"
```

## 👉 `sessionStorage`

`sessionStorage` is part of the **Web Storage API**, just like `localStorage`, but it stores data **only for the duration of the page session**.

- Data is cleared **when the tab or browser is closed**.
- Stores **key-value pairs** as **strings only**.
- It’s **tab-specific** — data **is not shared between tabs**.

```jsx
sessionStorage.setItem('key', 'value');       // Save data
sessionStorage.getItem('key');                // Get data
sessionStorage.removeItem('key');             // Remove one item
sessionStorage.clear();                       // Clear all
sessionStorage.length                         // Get number of items
sessionStorage.key(index);                    // Get key by index
```

## 👉 Cookies

Cookies are **small pieces of data** stored on the user's computer by the browser. They are mostly used for:

- **Session tracking** (like logged-in users)
- **User preferences**
- **Analytics and ads**

| Property | Cookie |
| --- | --- |
| Size limit | ~4 KB per cookie |
| Expiration | You can set a manual expiration time |
| Sent with requests | Automatically sent with every HTTP request |
| Scope | Can be limited by **path** or **domain** |

```jsx
document.cookie = "username=John";
```