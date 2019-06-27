# Собеседование в компанию Andersen

##Вопросы по JavaScript

###### 1. Как можно создать объект? В чем разница?

**Ответ:**

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


###### 2. Что выведет код?


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

**Ответ:**
```javascript
{a: 10}
```

</p>
</details>
