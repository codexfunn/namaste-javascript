## 💎 JavaScript Execution Context & Call Stack – Diamond Notes

---

### 🚀 JavaScript Runs in Two Magical Phases:

1️⃣ **Memory Creation Phase** *(aka Variable Environment)*

* JavaScript scans the code.
* Memory is allocated for **variables** and **functions**.
* `var` declarations are hoisted and initialized as `undefined`.
* `let` and `const` are also hoisted but not initialized — they reside in the **Temporal Dead Zone (TDZ)**.
* Function declarations are fully hoisted with their entire body.

2️⃣ **Code Execution Phase** *(aka Thread of Execution)*

* JavaScript executes code **line-by-line**.
* Variables are assigned actual values.
* Functions are invoked, and new execution contexts are created for each.

---

### 🌍 Global Execution Context (GEC)

* Created by default when the JavaScript engine starts.
* Divided into:

  * 🧠 **Memory Component** – stores variables and function references
  * ⚙️ **Code Component** – executes code line-by-line

📌 There is **only one GEC** at any time.

---

### 📦 Function Execution Context (FEC)

* Created **each time** a function is invoked.
* Has its own:

  * Memory Creation Phase (local variables, arguments)
  * Code Execution Phase (line-by-line)
* When execution ends, FEC is **popped** from the Call Stack.

---

### 📚 The Call Stack – JS's Brain

* Works on **LIFO (Last In, First Out)** principle.
* Each function call creates a new execution context and pushes it on top.
* When function execution completes, it’s popped off.

```js
function one() {
  console.log("One");
  two();
}
function two() {
  console.log("Two");
}
one();
```

🧱 Call Stack Flow:

```
[one Execution Context]
[two Execution Context]
```

➡️ After `two()` ends:

```
[one Execution Context]
```

➡️ After `one()` ends:

```
[Empty Call Stack]
```

---

### 🎯 Hoisting in JavaScript

#### 📌 Variable Hoisting

| Keyword | Hoisted? | Initialized?  | Result if Accessed Early |
| ------- | -------- | ------------- | ------------------------ |
| `var`   | ✅ Yes    | ✅ `undefined` | Returns `undefined`      |
| `let`   | ✅ Yes    | ❌ No          | ❌ ReferenceError         |
| `const` | ✅ Yes    | ❌ No          | ❌ ReferenceError         |

```js
console.log(a); // undefined
var a = 10;

console.log(b); // ReferenceError
let b = 20;
```

#### 📌 Function Hoisting

| Type               | Hoisted?   | Can Call Before Declaration? | Notes                            |
| ------------------ | ---------- | ---------------------------- | -------------------------------- |
| `function`         | ✅ Yes      | ✅ Yes                        | Fully hoisted                    |
| `var = function`   | ⚠️ Partial | ❌ No                         | Only name hoisted as `undefined` |
| `const = () => {}` | ❌ No       | ❌ No                         | Lives in TDZ                     |

```js
greet(); // ✅ Works
function greet() {
  console.log("Hello!");
}

sayHi(); // ❌ TypeError
var sayHi = () => console.log("Hi");
```

🧠 **Why are arrow functions not hoisted?**
Because they’re treated like **variables**, not function declarations. So the variable gets hoisted (as `undefined` if declared with `var`), but the function body doesn’t.

---

### 🌀 `undefined` vs `not defined`

| Term          | Meaning                      | Example                 | Error? |
| ------------- | ---------------------------- | ----------------------- | ------ |
| `undefined`   | Declared but not initialized | `var x; console.log(x)` | ❌ No   |
| `not defined` | Never declared in any scope  | `console.log(y)`        | ✅ Yes  |

---

### 🧠 Extra Gems 💎

* JS is **single-threaded**, runs one thing at a time.
* All async magic (Promises, `setTimeout`, etc.) is managed by the **event loop**, **Web APIs**, and **callback queue**.
* Execution Context = Lexical Environment + Scope Chain + `this` binding.
* Arrow functions do **not** have their own `this`, `arguments`, or `super`.

---

### ✅ TL;DR Cheat Sheet

* **Hoisting** lifts declarations to the top.
* **Execution Contexts** are created for each function call.
* **Call Stack** tracks function flow using LIFO.
* `let` and `const` live in **TDZ**.
* Arrow functions ≠ hoisted like normal functions.

---

