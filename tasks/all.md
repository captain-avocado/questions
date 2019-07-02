# Задачи. Продолжение

Фибоначчи. Факториал. Простое число: проверка

```js
    function fib(i) {
        if (i === 0 || i === 1) return i;
        return fib(i - 2) + fib(i - 1);
      }

      console.log(fib(8))

    function factorial(num) {
      let value = 1;
      for (let i = 2; i <= num; i++) {
        value *= i;
      }
      return value;
    }

    function factorialRec(num) {
      if (num < 2) return 1;
      else return num * factorialRec(num - 1);
    }

    console.log(factorial(-1));

    function isPrime(num) {
        if (num === 1 || num === 2) return true;
        for (let i = num - 1; i > 1; i--) {
          if (num % i === 0) return false;
        }
        return true;
      }

      console.log(isPrime(7));
```

Реализация функций filter и reduce

```js
    function filter(arr, cb) {
        const res = [];
        for (let i = 0; i < arr.length; i++) {
          if (cb(arr[i])) res.push(arr[i]);
        }
        return res;
      }

      console.log(filter([1, 11, 111, 111, 111], n => n > 11))


    function reduce(arr, cb, value) {
        let val = value;
        for (let i = 0; i < arr.length; i++) {
          val = cb(arr[i], val);
        }
        return val;
      }

      console.log(reduce([1, 4, 1], (a, b) => a + b, 0));

```

Конвертация десятичного числа в двоичное

```js
function decimalToBinary(num) {
  if (num === 0) return 0;
  let decimal = num;
  let binary = "";
  while (decimal > 0) {
    binary = (decimal % 2) + binary;
    decimal = Math.floor(decimal / 2);
  }
  return binary;
}
```

Конвертировать строку в соотвествии с условием

```js
// Примеры: 
// АААА => А4
// BBBCC => B3C2
// B => B1

function convertString(str) {
  if (str.length < 1) return str;
  let counter = 1;
  let res = '';
  for (let i = 1; i < str.length + 1; i++) {
    if (str[i] === str[i - 1]) {
      counter++
    } else {
      res += str[i - 1] + counter;
      counter = 1;
    }
  }
  return res;
}
```

