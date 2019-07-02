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
let a = new Object();
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


---
##### 5. Что выведет код? Почему?


```javascript

function foo() {
  function x() { }
  var x;
  return typeof x;
}
foo(); // ?

function boo() {
  var x;
  return typeof x;
  function x() { }
}
boo(); // ?


function goo() {
  var x = 10;
  return typeof x;
  function x() { }
}
goo(); // ?

```
<details><summary><b>Ответ:</b></summary>
<p>

```
function
function
number
```

</p>
</details>

---
##### 6. Что выведет код? Почему?


```javascript
console.log(1 + '2') //?
console.log('1' + 2) //? 
console.log('b' + 'a' + +'a') //? 
console.log(1 + '1' - '1') //? 
console.log(1 > 2 > 3) //? 
console.log(3 < 2 < 1) //? 
```
<details><summary><b>Ответ:</b></summary>
<p>

```
'12'
'12'
'baNaN'
10
false
true
```

</p>
</details>

---
##### 7. ООП в JavaScript? Что такое прототипное наследование?

<details><summary><b>Ответ:</b></summary>
<p>

```
Тут будет ответ
```

</p>
</details>


---
##### 8. Что выведет код? Почему?


```javascript
var obj = {
  prop: 'Hi',
  fncA: function () {
    return this.prop;
  },
  fncB: () => this.prop
};
var var1 = obj.fncA();  // ?
var fnc = obj.fncA;
var val2 = fnc(); // ?
```
<details><summary><b>Ответ:</b></summary>
<p>

```
'Hi'
undefined
```

</p>
</details>
