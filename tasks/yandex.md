# Задачи

## Автомат выдачи денег

Дана сумма. Необходимо выдать ее имеющимися купюрами.

1. Первая итерация: массив купюр

```js
const moneyTypes = [5000, 1000, 500, 100, 50];

function getMoney(amount) {
  const obj = {};
  let value = amount;

  for (let i = 0; i < moneyTypes.length; i++) {
    obj[moneyTypes[i]] = Math.floor(value / moneyTypes[i]);
    value = value % moneyTypes[i];
  }
  if (value !== 0) {
    throw new Error('Сумма не может быть получена');
  }
  return obj;
}
```

2. Вторая итерация: лимиты кол-ва купюр

```js
const limits = {
  5000: 10,
  1000: 5,
  500: 10,
  100: 12,
  50: 5,
};

function getMoney(amount, limits) {
  let limitsNew = {...limits};
  const keys = Object.keys(limits).reverse();
  let obj = {};
  let value = amount;

  for (let i = 0; i < keys.length; i++) {
    let res = Math.floor(value / keys[i]);
    if (res > limitsNew[keys[i]]) {
      res = limitsNew[keys[i]];
    }
    obj[keys[i]] = res;
    limitsNew[keys[i]] -= res;
    value = value % keys[i];
  }

  if (value !== 0) {
    obj = 'warn';
  }

  return {obj, limitsNew};
}

```

3. Третья итерация: обновленные лимиты 

```js
const limits = {
  5000: 10,
  1000: 5,
  500: 10,
  100: 12,
  50: 5,
  30: 10
};
```

//TODO: Как выдать 120? Жадный алгоритм не подходит


## Сжатие массива

Дан массив целых чисел. Если в массиве встречаются перечисления вида [1, 2, 3, 4] - представить их в виде строки 1-4.

```js
function arrCompress(originalArray) {
  if (originalArray.length < 2) return originalArray;
  let array = [...originalArray]
    .sort((a, b) => a - b)
    .filter((item, pos, arr) => !pos || item !== arr[pos - 1]);
  
  const result = [];
  let range = 1;
  for (let i = 0; i < array.length; i++) {
    if (array[i + 1] - array[i] === 1) {
      range++;
    } else {
      if (range > 1) {
        result.push(`${array[i - range + 1]}-${array[i]}`);
      } else {
        result.push(array[i]);
      }
      range = 1;
    }
  }

  return result;
};

```

## Палиндром

Проверка с дополнительными условиями

```js
// Примеры: 
// ("Ш4л4ш") => true
// ("Eva, can I see bees in a cave?") => true
// ("Яндекс") => false

function palindrome(str) {
  const string = str.toLowerCase().replace(/[^\w\dа-яА-ЯЁё]/g, '');
  return string === string.split('').reverse().join('');
}
```

## Скобки

Проверка на правильно расставленные скобки

```js
// Примеры:
// check("{()}[]") // true
// check("{[}]") // false

function checkBrackets(str) {
  const open  = ['(', '[', '{'];
  const close = [')', ']', '}'];
  let stack = [];

  for (let i = 0; i < str.length; i++) {
    if (open.includes(str[i])) {
      stack.push(str[i]);
    } else if (close.includes(str[i])) {
      const el = stack.pop();
      if (close[open.indexOf(el)] !== str[i]) {
        return false;
      }
    } else {
      throw new Error('Symbol is not defined');
    }
  }
  return true;
}
```

## Анаграммы

```js
// Пример:
// [“нос”, “сон”, “снедь”, “днесь”] => [
//   ["нос", "сон"],
//   ["днесь", "снедь"]
// ]

function checkAnagrams(a, b) {
  if (a.length !== b.length) return false;
  for (let i = 0; i < a.length; i++) {
    if (!a.includes(b[i])) return false;
  }
  return true;
}

function getAnagrams(arr) {
  let anagrams = [];
  let pairs = [];
  for (let i = 0; i < arr.length; i++) {
    for (let j = 0; j < arr.length; j++) {
      if (i === j || anagrams.includes(arr[j])) continue;
      if (checkAnagrams(arr[i], arr[j])) {
        pairs.push([arr[i], arr[j]]);
        anagrams.push(arr[i]);
      }
    }
  }
  return pairs;
}
```