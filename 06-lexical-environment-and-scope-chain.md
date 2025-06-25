# 🧠 JavaScript: Lexical Environment & Scope Chain – Diamond Notes

---

## 📌 What is a Lexical Environment?

> A **Lexical Environment** is the structure that holds **variable/function identifiers** and their references, created every time a function is executed or a block is entered.

* Think of it as a **backpack** attached to every execution context.
* It contains:

  * The current local memory (variables/functions inside the function or block)
  * A reference to its **outer Lexical Environment**

### 🧠 Example:

```js
function outer() {
  var a = 10;
  function inner() {
    console.log(a); // a is not in inner's scope but in its outer lexical environment
  }
  inner();
}
outer();
```

Here:

* `inner()` doesn’t have `a`.
* It looks outside — into `outer()`'s backpack — and finds it.

✅ That’s Lexical Environment in action!

---

## 🔗 What is Scope Chain?

> The **Scope Chain** is the chain of Lexical Environments used to **resolve identifiers** (variable/function names).

When JS can't find a variable in the current scope:

* It climbs up the chain (outer → outer → global) until it finds it or hits the top.

### 🧠 Example:

```js
var a = "global";
function outer() {
  var b = "outer";
  function inner() {
    var c = "inner";
    console.log(a, b, c); // accessible through scope chaining
  }
  inner();
}
outer();
```

✅ Output: `global outer inner`

Each level **looks upward** until it finds what it needs. This is **Lexical Scope**, not dynamic!

---

## 📌 Lexical Scope vs Dynamic Scope

* JavaScript uses **Lexical Scoping** (determined by the position of code when written).
* It does **NOT** use Dynamic Scoping (which depends on the call stack).

```js
function a() {
  var x = 10;
  function b() {
    console.log(x); // Lexically scoped
  }
  return b;
}
var fn = a();
fn(); // still remembers x = 10
```

Even when `fn` runs in global scope, it still knows `x` because of its **lexical environment**.

---

## 🔥 Mind-Blowing: Functions Carry Their Scope!

> When you return a function, it **remembers the scope it was born in**, not where it’s called from. 🔥

This leads to powerful concepts like:

* ✅ **Closures** (functions holding on to variables from outer scopes)
* ✅ **Data privacy**
* ✅ **Callback behavior** in async programming

---

## 🌀 Memory Visualization

```text
Execution Context of inner()
→ Lexical Env:
  c: "inner"
  Outer: LexicalEnv of outer()

Execution Context of outer()
→ Lexical Env:
  b: "outer"
  Outer: Global Lexical Env

Global Lexical Env:
  a: "global"
```

---

## ✅ TL;DR Summary

* **Lexical Environment** = local memory + reference to outer environment
* **Scope Chain** = chain of environments JS climbs to resolve variables
* JS uses **Lexical Scope**, not dynamic
* Functions always carry the scope in which they were defined

---

✨ Understanding how lexical environments and scope chains work is 🔑 to debugging, closures, and async logic in JavaScript. This is core JS magic — master it and you're halfway to wizardry. 🪄💻
