# Event Handling

Created time: July 23, 2025 8:20 PM
Difficulty: Intermediate
Last edited time: November 3, 2025 11:38 AM
Status: Done

## 👉 `addEventListener()`

- Attaches an event handler to an element **without overwriting existing event handlers**.

```jsx
element.addEventListener(eventType, callbackFunction, useCapture);
```

- `eventType`: A string like `"click"`, `"mouseover"`, `"input"`, etc.
- `callbackFunction`: The function to run when the event happens
- `useCapture` (optional): `true` for capturing phase, `false` for bubbling (default)

## 👉 `removeEventListener()`

- Detaches a previously attached event listener.

```jsx
function sayHi() {
  alert("Hi!");
}

button.addEventListener("click", sayHi);

// Later...
button.removeEventListener("click", sayHi);
```

## 👉 Key Events

### ❗️`click`

- Triggered when an element is **clicked**.

```jsx
button.addEventListener("click", () => {
  console.log("Button clicked");
});
```

### ❗️`input`

- Triggered whenever the **value of an input field** changes (on each keystroke).

```jsx
input.addEventListener("input", () => {
  console.log(input.value);
});
```

### ❗️`change`

- Triggered when the **input value is changed and focus is lost** (blur).

```jsx
input.addEventListener("change", () => {
  console.log("Final value:", input.value);
});
```

### ❗️`submit`

- Triggered when a **form is submitted**.

```jsx
form.addEventListener("submit", (e) => {
  e.preventDefault(); // Stops form from reloading the page
  console.log("Form submitted");
});
```

### ❗️`mouseover`

- Triggered when the mouse **enters** an element.

```jsx
element.addEventListener("mouseover", () => {
  element.style.backgroundColor = "lightblue";
});
```

### ❗️`mouseout`

- Triggered when the mouse **leaves** an element.

```jsx
element.addEventListener("mouseout", () => {
  element.style.backgroundColor = "white";
});
```

### ❗️`mousemove`

- Triggered **continuously** as the mouse moves over an element.

```jsx
element.addEventListener("mousemove", (e) => {
  console.log(`X: ${e.clientX}, Y: ${e.clientY}`);
});
```

### ❗️`keyup`

- Triggered when a **key is released**.

```jsx
document.addEventListener("keyup", (e) => {
  console.log("Key released:", e.key);
});
```

### ❗️`keydown`

- Triggered when a **key is pressed down**.

```jsx
document.addEventListener("keydown", (e) => {
  console.log("Key down:", e.key);
});
```

### ❗️Summary Table

| Event | Triggered When... | Common Uses |
| --- | --- | --- |
| `click` | Element is clicked | Buttons, links, toggles |
| `input` | Value changes (each keystroke) | Live form updates |
| `change` | Value changes (after blur) | Dropdowns, checkboxes, inputs |
| `submit` | Form is submitted | Prevent default behavior, validate |
| `mouseover` | Mouse enters element | Tooltips, hover styles |
| `mouseout` | Mouse leaves element | Hover out effect |
| `mousemove` | Mouse moves over an element | Drawing apps, custom cursors |
| `keydown` | Key is pressed down | Keyboard shortcuts, game controls |
| `keyup` | Key is released | Input validation, detect Enter key |

## 👉 Event Object

### ❗️`event.target`

- Returns the **actual element** that triggered the event.

```jsx
element.addEventListener("click", function (event) {
  console.log(event.target); // The clicked element
});
```

### ❗️`event.type`

- Returns the **type of event** that occurred (e.g. `"click"`, `"keydown"`).

```jsx
element.addEventListener("click", function (e) {
  console.log(e.type); // "click"
});
```

### ❗️`event.preventDefault()`

- **Prevents the default behavior** of the element when the event occurs.

```jsx
element.addEventListener("submit", function (e) {
  e.preventDefault(); // Stop form from reloading the page
});
```

## 👉 Event Bubbling and Capturing

When an event occurs (like a click), it **travels through the DOM in 3 phases**:

1. **Capturing Phase** (Trickling Down)
2. **Target Phase** (Event reaches the target element)
3. **Bubbling Phase** (Event bubbles up back to the root)

```jsx
<div id="parent">
  <button id="child">Click Me</button>
</div>
```

When you click the button:

1. The event starts from `document` → goes down to `#child` (**capturing**)
2. Event hits `#child` (**target phase**)
3. Then it goes back up to `#parent`, `document`, etc. (**bubbling**)

| Phase | Description | Used With `addEventListener()` |
| --- | --- | --- |
| Capturing | Top → Down (document → target) | `{ capture: true }` |
| Target | Event reaches the element itself | - |
| Bubbling | Bottom → Up (target → document) (default) | Default (`capture: false`) |

## 👉 Event Delegation

- **Event delegation** is a technique where you **attach a single event listener to a parent element** and handle events triggered by its **child elements** using the `event.target`.
- Instead of adding individual event listeners to multiple children, you **delegate** the event handling to the parent.

```jsx
<ul>
  <li>Item 1</li>
  <li>Item 2</li>
  <li>Item 3</li>
</ul>

const ul = document.querySelector("ul");

ul.addEventListener("click", function (e) {
  if (e.target.tagName === "LI") {
    console.log("Clicked", e.target.textContent);
  }
});
```