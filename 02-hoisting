# 💎 JavaScript Hoisting – Diamond Notes

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
