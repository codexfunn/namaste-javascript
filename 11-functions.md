# JavaScript Functions Explained - Namaste JavaScript Style 💡

## 🚀 Today's Topics Covered

1. **Function Statement / Function Declaration**
```js
function a(){
    console.log("a called");
}
a(); // ✅ Hoisted
```

2. **Function Expression**
```js
var b = function(){
    console.log("b called");
};
b(); // ❌ Not hoisted like declaration
```

3. **Anonymous Function**
- Functions without a name. Usually assigned to variables.
```js
var c = function(){
    console.log("c called");
};
c();
```

4. **Named Function Expression**
- Function has a name but still not accessible outside.
```js
var d = function xyz(){
    console.log("d called");
};
d();
// xyz(); ❌ ReferenceError: xyz is not defined (only accessible inside itself)
```

5. **Parameters vs Arguments**
```js
function e(param1, param2){
    console.log("function e called", param1, param2);
}
e(1, 2); // 1, 2 are arguments; param1, param2 are parameters
```

6. **First Class Functions**
- JavaScript treats functions as **first-class citizens**: you can pass them as arguments, return them, and assign them to variables.

```js
function greet(){
    return function(){
        console.log("Hello from first class function!");
    };
}
const greeter = greet();
greeter();
```

7. **Arrow Functions (ES6)**
```js
const arrowFunc = () => {
    console.log("Arrow function called");
};
arrowFunc();
```

---

## 💥 Key Differences
| Type                    | Hoisted | Can be Anonymous | Can be Named | Reference Name |
|-------------------------|---------|------------------|--------------|----------------|
| Function Declaration    | ✅ Yes  | ❌ No            | ✅ Yes       | Yes            |
| Function Expression     | ❌ No   | ✅ Yes           | ✅ Yes       | Variable name  |
| Arrow Function          | ❌ No   | ✅ Yes           | ❌ No        | Variable name  |

---

## 📌 Pro Tip for Interviews
> If an interviewer asks you about hoisting, *always* bring up the difference between declarations and expressions.

> And when asked about named function expressions — don't fall into the trap of calling the name outside the function. It ain't global!

---

### 🔥 That's a wrap for today's session! Next up: Closure 🔒 Madness!
