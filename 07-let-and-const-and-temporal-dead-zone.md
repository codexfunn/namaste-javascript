# 🧠 Advanced Insights into `let`, `const`, `var` & Temporal Dead Zone – Diamond Notes

---

## 🔍 1. Why Are `var` Variables Attached to the `window` Object?

### 🧬 In Browsers:

* Global variables declared with `var` become properties of the `window` object.
* This is a **legacy feature** for compatibility with older JS code.

```js
var x = 10;
console.log(window.x); // ✅ 10
```

### ❌ Not the Case with `let` & `const`

* Variables declared with `let` or `const` in the global scope **do not attach** to the `window` object.

```js
let y = 20;
console.log(window.y); // ❌ undefined
```

> `let` and `const` live in a **separate declarative environment** during the memory phase — isolated from `var`.

---

## 🕳️ 2. What is the Temporal Dead Zone (TDZ)?

> The time between entering a scope and the actual declaration of `let` or `const` variable, during which the variable **cannot be accessed**.

### 🔥 Example:

```js
console.log(a); // ❌ ReferenceError
let a = 5;
```

### Why TDZ Exists:

* Prevents usage before proper initialization
* Promotes cleaner, more predictable code

### TDZ Timeline:

```text
Memory Phase:
  - let a;  ❌ (not initialized)
Execution Phase:
  - Access 'a' → ReferenceError (TDZ)
  - let a = 5; ✅ Initialized
```

---

## 🌐 3. Why Only `var` is Accessible via `window.variableName`

### Reason:

* `var` variables are added to the **Global Object** during the memory phase.
* `let` and `const` are **not properties** of the global object.

```js
var a = 1;
let b = 2;
console.log(window.a); // ✅ 1
console.log(window.b); // ❌ undefined
```

> This makes `let`/`const` safer in global environments — **no accidental overrides**.

---

## ⚠️ 4. TypeError vs ReferenceError vs SyntaxError

| Error Type         | When it Occurs                                          | Example                         |
| ------------------ | ------------------------------------------------------- | ------------------------------- |
| **ReferenceError** | Accessing variable not in any scope (TDZ or undeclared) | `console.log(x);`               |
| **TypeError**      | Performing invalid operation on a value                 | `null.f();` or reassign `const` |
| **SyntaxError**    | Code doesn't follow proper JS syntax rules              | `let = 5 let;`                  |

### 🔥 Quick Examples:

```js
console.log(x); // ❌ ReferenceError
const y = 10;
y = 20;          // ❌ TypeError
let let = 5;     // ❌ SyntaxError
```

---

## 💪 5. Strictness of `let` vs `const` vs `var`

| Feature          | `var`          | `let`         | `const`       |
| ---------------- | -------------- | ------------- | ------------- |
| Scope            | Function       | Block         | Block         |
| Re-declaration   | ✅ Allowed      | ❌ Not allowed | ❌ Not allowed |
| Re-assignment    | ✅ Allowed      | ✅ Allowed     | ❌ Not allowed |
| TDZ Protection   | ❌ No           | ✅ Yes         | ✅ Yes         |
| Global Pollution | ✅ Yes (window) | ❌ No          | ❌ No          |

### Best Practice:

> 🔐 **Use `const` by default**, and switch to `let` only when mutation is needed.

Avoid `var` unless you're deep into legacy projects or polyfills.

---

## ✅ TL;DR Summary

* `var` binds to `window`, `let` and `const` don’t — they’re scoped safely.
* TDZ ensures variables aren’t accessed before they’re declared.
* `const` locks binding, not value.
* Errors in JS tell you *exactly* what’s wrong — learn the difference.
* `const` is the most strict, `var` is the loosest — use wisely!

---

✨ Master these deep internals and you're not just writing JavaScript — you're commanding it. 🧙‍♂️🔥
