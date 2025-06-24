# 🧩 JavaScript: `undefined` vs `not defined` – Deep Dive Diamond Notes

---

## 🧠 1. What is `undefined`?

> `undefined` means a variable has been declared but **has not been assigned any value**.

### ✅ Example:

```js
var a;
console.log(a); // undefined
```

* `a` exists in memory, but no value was assigned, so JS returns `undefined`.

### ✅ Another Example (functions):

```js
function test() {}
console.log(test()); // undefined
```

If a function doesn’t return anything, it returns `undefined` by default.

---

## 🚫 2. What is `not defined`?

> A variable that has **never been declared** in any accessible scope.

### ❌ Example:

```js
console.log(x); // ❌ ReferenceError: x is not defined
```

* JavaScript looks for `x` in memory.
* Doesn’t find any reference — not in local or global memory.
* Boom: **ReferenceError**.

---

## 🔄 Side-by-Side Comparison

| Aspect      | `undefined`                  | `not defined`           |
| ----------- | ---------------------------- | ----------------------- |
| Declaration | Declared but not assigned    | Never declared          |
| Error?      | ❌ No                         | ✅ ReferenceError        |
| Type        | `undefined` (primitive type) | Error — no type         |
| Scope       | Exists in memory             | Doesn't exist in memory |

---

## 🎯 3. Why is JS Called Loosely Typed?

> JavaScript allows variables to **hold any type** and change type at runtime — no type declaration needed.

### 🌀 Example:

```js
var data = 42;     // number
data = "GOAT";     // now string
```

* You never declared `data` as a number or string.
* JS doesn’t care — it’s **dynamically typed**.

This flexibility is why JS is **loosely typed**:

* No need to specify data types.
* Types are determined at runtime.
* Easy to write, but can cause bugs if not careful.

---

## ⚠️ 4. Why is `var a = undefined;` Bad Practice?

### It’s discouraged because:

1. It’s **hard to distinguish** between something JS set to `undefined` and something you set manually.
2. JS uses `undefined` internally to signal **missing values**.
3. Setting it yourself can **mask bugs** or lead to false assumptions.

### 👎 Example:

```js
var a = undefined;
// Later someone checks:
if (a === undefined) {
  // Did the dev forget to assign?
  // Or was it deliberately undefined?
}
```

Instead, use:

* `null` to indicate intentional absence of value.
* Avoid assigning `undefined` manually — let JavaScript handle it.

---

## 💎 5. Bonus: Interview Nuggets

### 🔥 Pro Tips:

* `undefined` is a **value** and a **type**.
* `not defined` is a **runtime error**.
* JavaScript's loose typing = freedom + responsibility ⚖️
* Always initialize variables properly!

### ✅ Safer Alternatives:

```js
var user = null;      // Good: clearly shows intentional absence
let count;            // Let JS assign undefined naturally
```

---

## ✅ TL;DR Summary

* `undefined` = declared but not assigned.
* `not defined` = doesn’t exist at all.
* JS is **loosely typed**, so variables can change type freely.
* Don’t assign `undefined` manually — use `null` instead.
* Always check if variables are initialized before accessing them.

---
