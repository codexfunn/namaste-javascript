# 🧱 Block, Scope & Shadowing in JavaScript – Diamond Notes 💎

---

## 🔳 1. What is a Block in JavaScript?

> A **block** is a chunk of code enclosed in `{}` braces. It defines a **block scope** for variables declared using `let` and `const`.

### ✅ Example:

```js
{
  let x = 10;
  const y = 20;
  var z = 30;
}

console.log(z); // ✅ 30
console.log(x); // ❌ ReferenceError
```

* `x` and `y` are block-scoped → not accessible outside
* `z` is function-scoped (because of `var`) → leaks out of block

---

## 🧠 2. What is Scope?

> Scope determines the **visibility** and **lifetime** of variables.

### 🧭 Types of Scope in JS:

| Scope Type     | Description                                      |
| -------------- | ------------------------------------------------ |
| Global Scope   | Accessible from anywhere                         |
| Function Scope | Exists inside a function; accessible within only |
| Block Scope    | Defined using `{}` and `let`/`const`             |

### 🧠 Scope Hierarchy:

* Inner scopes can access outer scope variables
* Outer scopes **cannot** access inner scope variables

```js
let a = 100;
function outer() {
  let b = 200;
  function inner() {
    console.log(a, b); // ✅ Accessible
  }
  inner();
}
outer();
```

---

## 🌗 3. What is Shadowing?

> When a variable declared in an **inner scope** has the same name as one in an **outer scope**, the inner one **shadows** the outer.

```js
let a = "outer";
{
  let a = "inner";
  console.log(a); // "inner"
}
console.log(a);   // "outer"
```

The outer `a` still exists — it's just **temporarily hidden** inside the block.

---

## 💥 4. Shadowing with `var`, `let`, and `const`

### ✅ Legal Shadowing:

```js
let x = 1;
{
  let x = 2; // ✅ allowed
  console.log(x); // 2
}
console.log(x); // 1
```

### ❌ Illegal Shadowing (Same name with `var` after `let`/`const`):

```js
let y = 10;
{
  var y = 20; // ❌ SyntaxError
}
```

> JS doesn’t allow **less strict `var` to shadow more strict `let`/`const`**

### ✅ Opposite Works:

```js
var z = 30;
{
  let z = 40; // ✅ allowed
  console.log(z); // 40
}
console.log(z); // 30
```

---

## 🧬 5. Function Scope vs Block Scope

```js
function test() {
  if (true) {
    var a = 10;
    let b = 20;
    const c = 30;
  }
  console.log(a); // ✅ 10
  console.log(b); // ❌ ReferenceError
  console.log(c); // ❌ ReferenceError
}
test();
```

* `var` → leaks outside block, survives inside the function
* `let`/`const` → trapped within the `{}` block

---

## 🎯 Best Practices & Bonus Nuggets

* 🧼 Avoid reusing variable names across scopes — reduces confusion
* 🔐 Use `const` by default, `let` when needed, and avoid `var`
* 🧪 Shadowing is powerful in closures but dangerous if misused
* 🧠 Always know **which variable you’re talking to** — outer or inner

---

## ✅ TL;DR Summary

* `{}` creates a **block** — `let` & `const` are block-scoped
* `var` is function-scoped and leaks out of blocks
* **Scope** controls where a variable is accessible
* **Shadowing** hides outer variables temporarily
* Illegal shadowing happens when `var` tries to override `let`/`const`

---

💡 Understanding blocks, scope, and shadowing gives you **surgical control** over your variables. No more accidental overwrites or mystery bugs — just clean, scoped, predictable code. 🧠🧼💻
