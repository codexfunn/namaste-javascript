# 💎 JavaScript Hoisting & How Functions Work – Diamond Notes

---

## 🪄 1. What is Hoisting?

### 📖 Definition:

Hoisting is JavaScript's behavior of **moving declarations to the top** of their scope during the **Memory Creation Phase**.

### 🔍 Key Points:

1. `var` declarations are hoisted and initialized with `undefined`.
2. `let` and `const` are hoisted too, but they stay in a **Temporal Dead Zone (TDZ)** and throw a `ReferenceError` if accessed before declaration.
3. **Function declarations** are fully hoisted — you can call them before they appear in the code.

```js
console.log(x); // undefined
var x = 5;

console.log(y); // ReferenceError
let y = 10;

sayHello(); // ✅ Works
function sayHello() {
  console.log("Hello!");
}

sayHi(); // ❌ TypeError: sayHi is not a function
var sayHi = () => console.log("Hi!");
```

---

## ❗ Why is the Arrow Function Undefined?

Because `sayHi` is declared with `var`, it’s hoisted and initialized as `undefined`.
When you try to call it before the assignment, JS says:

> "You’re trying to call **undefined** like it’s a function... how dare you." 😤

🧠 **Remember**:

* `undefined` is a **value** (assigned during hoisting).
* `not defined` means the variable **doesn't exist** in any scope.

---

## 💎 Bonus Section: Hidden Truths & Must-Know Nuggets

### 🔥 Temporal Dead Zone (TDZ)

Any `let` or `const` variable is in the **TDZ** from the **start of the block** until its **declaration**.

```js
console.log(foo); // ❌ ReferenceError
let foo = 42;
```

Accessing it early throws a `ReferenceError` — like trying to grab something that **exists but isn’t ready yet**.

---

### 🧠 Interview Tip:

> **Always remember:**

* ✅ Declaration is hoisted.
* ❌ Initialization is NOT hoisted (unless it’s a function declaration).

---

## ✅ TL;DR Summary

1. **Hoisting** = JS lifting declarations up in memory phase.
2. **Arrow functions** are treated like variables — so they get `undefined` on hoisting.
3. `undefined` = declared but not initialized.
4. `not defined` = variable doesn’t exist at all.
5. **TDZ** is real. Avoid accessing `let`/`const` before they're declared.

---

## 🔍 How Functions Work in JavaScript

### 🧠 Key Concepts:

* Each function call creates a **new Execution Context**.
* Functions have **local scope** — variables inside are isolated.
* **Global variables** are accessible inside any function unless shadowed.
* Function declarations are hoisted entirely.

```js
var x = 1;
a();
b();
console.log(x);

function a() {
  var x = 10; 
  console.log(x);
}

function b() {
  var x = 100; 
  console.log(x);
}
```

### 🧠 What Happens:

* Global `x = 1`.
* `a()` creates its own local `x = 10` → logs `10`.
* `b()` creates its own local `x = 100` → logs `100`.
* `console.log(x)` (global scope) → logs `1`.

**Output:**

```
10
100
1
```

Each function has its **own private memory**, and variables inside don’t mess with others unless explicitly referenced.

---

## 🌀 Memory Visualization:

```text
Global EC:
  x: 1
  a: function a()
  b: function b()

Call Stack:
  1. Global EC
  2. a EC → x: 10
  3. b EC → x: 100
```

---

## 💥 Mind-Blowing Function Concepts:

### 🔄 Functions Are First-Class Citizens

* Can be **assigned to variables**
* Can be **passed as arguments**
* Can be **returned from other functions**

### 🔒 Functions Create Their Own Scope

```js
function outer() {
  var name = "GOAT";
  function inner() {
    console.log(name);
  }
  inner();
}
outer(); // logs: GOAT
```

This is the beginning of **Closures** — one of the deepest JS concepts.

### 🧠 JS Functions = Object + Code

* A function in JS is an **object** with hidden properties (`[[Scopes]]`, `prototype`, etc.).
* JS engine internally attaches **lexical scope** to function objects.

---

## ✅ TL;DR – Functions in JS

* Each function gets its own **Execution Context**.
* Functions can access **global variables** but not each other’s local variables.
* `var` inside a function **does not leak** outside.
* Functions are **hoisted** completely.
* Arrow functions behave differently with `this` and hoisting.
* Functions are the building blocks of JS magic — from callbacks to closures, async to currying.

---

✨ Mastering how functions work means unlocking the **true power of JavaScript**. Wrap your mind around these concepts and you’re already above 80% of devs out there. Keep building the diamond vault! 💎💻
