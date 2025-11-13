# Using (this) Keyword/

Created time: July 21, 2025 10:52 PM
Difficulty: Intermediate
Last edited time: July 21, 2025 10:55 PM
Status: Done

- The `this` keyword refers to the **object that is executing the current function**.
- It changes based on **how a function is called**, not where it's defined.

### ❗️Common scenarios of `this` keyword

```jsx
//1. Global scope :- Window

console.log(this);

//2. Function :- Window

function abcd(){
	console.log(this);
}

//3. Method :- Object

var obj1 = {
	name : function(){
			console.log(this);
		}
}
obj1.name();

//4. Function inside method (es5) :- Window

var obj1 = {
	name: function(){
		function name(){
			console.log(this);
		}
	}
	name();
}

//5. Function inside method (es6) :- Object

var obj1 = {
	name : function(){
		const name = () => {
			console.log(this);
		}
		name();
	}
}

//6. Constructor :- new blank object

function abcd(){
	console.log(this);
}
const name = new abcd();
console.log(name);

//7. Event Listener :- The element in which the event listener is applied to.

btn = document.querySelector("button");
btn.addEventListener("click", function(){
	console.log(this);
})
```