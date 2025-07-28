# Namaste JavaScript: Episode 14 Notes
---

## 🔁 JavaScript: Synchronous & Single-threaded

JavaScript executes **one line at a time** in a sequence — this is called **synchronous execution**. Being **single-threaded** means it has **only one call stack**, handling **one thing at a time**.

```js
console.log("Start");
alert("Blocking Code");
console.log("End");
```

> When alert() blocks, nothing else runs — main thread is frozen.

---

## ⚡️ Callback Functions

A **callback function** is a function passed as an argument to another function. It allows **async handling** and **extensibility**.

```js
function greet(callback) {
  console.log("Hi there!");
  callback();
}

greet(function () {
  console.log("Callback Executed");
});
```

### 🤔 Why Are Callbacks Powerful?

* Help in **async code** (like APIs, setTimeout)
* Enable **reusability**
* Important part of **event-driven programming**

---

## 🧠 Event Listeners and the Callback Queue

```js
document.getElementById("btn").addEventListener("click", function handleClick() {
  console.log("Button clicked");
});
```

* The above function is **registered** in memory.
* When the button is clicked, the callback is **sent to the callback queue**.
* **Event loop** picks it only when the **call stack is empty**.

### 🔒 Closures with Event Listeners

Closures preserve **scope** even after the outer function has run. This makes Event Listeners **retain** access to outer variables.

```js
function attachEvent() {
  let count = 0;
  document.getElementById("clickMe").addEventListener("click", function () {
    console.log("Clicked", ++count);
  });
}
attachEvent();
```

Even after `attachEvent` is finished, the callback has access to `count` — thanks to closures.

---

## 🧹 Garbage Collection

JavaScript engine removes **unused or unreachable memory**.

> But if we don't remove unused event listeners, memory leaks can happen.

---

## ❌ Removing Event Listeners

Always clean up listeners to avoid **memory leaks**:

```js
function print() {
  console.log("Scroll detected");
}

window.addEventListener("scroll", print);

// Later on
window.removeEventListener("scroll", print);
```

Make sure to pass **same function reference** to remove it.

---

## 🧠 Key Takeaways:

* JavaScript is **single-threaded** but can handle async via **callbacks**
* **Callback functions** are core to JS async behavior
* **Closures** make callbacks even more powerful
* **Event Listeners** register callbacks and retain context via closures
* Use `removeEventListener` to prevent memory leaks

---

## 💬 Interview Questions

1. What is the role of callback functions in JavaScript?
2. How do closures work in event listeners?
3. Why do we remove event listeners?
4. How is JavaScript single-threaded but handles async code?
5. Explain event loop and callback queue.

---

> **"Callbacks, closures, and the call stack — the holy trinity of JS power."**

This episode digs deep into how JS runs behind the scenes. Master these concepts, and you're not just writing JS — you're *commanding* it.
