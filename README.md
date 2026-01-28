# 📘 JavaScript MCQ Cheat Sheet & Tricky Output Questions

This repository contains **high-frequency JavaScript MCQs**, **output-based questions**, and **one-line rules** commonly asked in:
- University exams
- MCQs
- Interviews
- Competitive programming tests

---

## 📌 Topics Covered
- Hoisting
- Scope (`var`, `let`, `const`)
- Function declarations vs expressions
- Closures & loops
- `this` keyword
- Equality operators
- Type coercion
- Tricky JavaScript outputs
- Common JavaScript bugs

---

## 🔥 Hoisting Rules (Must Memorize)

### `var`
- Hoisted ✔
- Initialized as `undefined`
- Function scoped
- Can be redeclared

### `let`
- Hoisted ✔
- In **Temporal Dead Zone (TDZ)**
- Block scoped
- Cannot be redeclared

### `const`
- Hoisted ✔
- In **TDZ**
- Block scoped
- Cannot be reassigned

```js
console.log(a);
var a = 10; // undefined

console.log(b);
let b = 10; // ReferenceError
```

---

## 🔥 Function Hoisting

### Function Declaration
```js
foo();
function foo() {
  console.log("Hello");
}
```
✔ Works (fully hoisted)

### Function Expression
```js
foo();
var foo = function() {
  console.log("Hi");
};
```
❌ TypeError

---

## 🔥 Scope Shadowing

```js
var a = 10;
(function() {
  console.log(a);
  var a = 20;
})();
```

**Output:**
```
undefined
```

---

## 🔥 `let` vs `var` in Loops

```js
for (var i = 0; i < 3; i++) {
  setTimeout(() => console.log(i), 0);
}
```
Output:
```
3 3 3
```

```js
for (let i = 0; i < 3; i++) {
  setTimeout(() => console.log(i), 0);
}
```
Output:
```
0 1 2
```

---

## 🔥 `typeof` Traps

```js
typeof null        // "object"
typeof []          // "object"
typeof undefined   // "undefined"
typeof NaN         // "number"
```

📌 `typeof null === "object"` is a JavaScript bug

---

## 🔥 Equality Operators

```js
'5' == 5    // true
'5' === 5   // false
null == undefined  // true
null === undefined // false
```

---

## 🔥 Tricky Output Questions

```js
console.log([] + []);      // ""
console.log([] + {});      // "[object Object]"
console.log({} + []);      // 0
console.log(true + true);  // 2
console.log("2" - 1);      // 1
console.log(1 + "2" + 3);  // "123"
```

---

## 🔥 Falsy Values in JavaScript

```text
false
0
""
null
undefined
NaN
```

---

## 🔥 Object Comparison Trap

```js
const a = {};
const b = {};
a == b;  // false
```

---

## ⚡ Quick MCQ Rules

- `var` → undefined
- `let / const` → ReferenceError
- Function declaration → callable before definition
- Function expression → not callable before assignment
- `typeof null` → "object"
- `==` converts types
- `===` does not convert types

---

## 🧠 Memory Tricks

> **var lies, let dies, const cries**  
> **== cheats, === judges**
