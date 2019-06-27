# Собеседование в компанию Andersen

## Вопросы по JavaScript

---
##### 1. Как можно создать объект? В чем разница?

<details><summary><b>Ответ:</b></summary>
<p>

```javascript
let a = {}; 
```

```javascript
const obj = {};
let a = Object.create(obj); 
```
```javascript
function A() {}
let a = new A();
```

</p>
</details>

---
##### 2. Что выведет код? Почему?


```javascript
var a = {};

(function (a) {
  a.a = 10;
  a = null;
})(a);

console.log(a); // ?
```
<details><summary><b>Ответ:</b></summary>
<p>

```javascript
{a: 10}
```

</p>
</details>

---

##### 3. Что такое замыкание? Приведите пример.

<details><summary><b>Ответ:</b></summary>
<p>

```javascript
function makeCounter() {
  let counter = 0;

  return () => {
    counter++;
  }
}

let a = makeCounter();

console.log(a()); // 1
console.log(a()); // 2
```

</p>
</details>

---
##### 4. Что выведет код? Почему?


```javascript
var myVar = 'hello';
function myFunc() {
  console.log(myVar); // ?
  var myVar = 'goodbye';
  console.log(myVar); // ?
}

myFunc();
console.log(myVar); // ?

```
<details><summary><b>Ответ:</b></summary>
<p>

```
undefined
goodbye
hello
```

</p>
</details>



