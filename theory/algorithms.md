# Алгоритмы

## Сортировка пузырьком

```js
// сортировка пузырьком
    const bubbleSort = (arr) => {
      let copyArr = [...arr];
      if (arr.length <= 1) return arr;
      for (let i = 1; i < arr.length; i++) {
        for (let j = 0; j < arr.length; j++) {
          if (copyArr[j] > copyArr[i]) {
            const tmp = copyArr[i];
            copyArr[i] = copyArr[j];
            copyArr[j] = tmp;
          }
        }
      }
      return copyArr;
    }
    console.log(bubbleSort(arr));

```

## Квиксорт

```js
// //квиксорт
    const partion = (array, low, high) => {
      const pivot = array[Math.floor(((low + high) / 2))];

      while (high >= low) {
        while (array[high] > pivot) {
          high--;
        }
        while (array[low] < pivot) {
          low++;
        }
        if (high >= low) {
          const tmp = array[low];
          array[low] = array[high];
          array[high] = tmp;
          high--;
          low++;
        }
      }
      return low;
    }

    const quickSort = (array, low = 0, high = array.length - 1) => {
      if (low < high) {
        const index = partion(array, low, high);
        quickSort(array, low, index - 1);
        quickSort(array, index, high);
      }
      return array;
    }

    console.log(arr);
    console.log(quickSort([5, 6, 9, 0, 1, 2]));
```

## Бинарный поиск

```js
// бинарный поиск
    const binarySearch = (arr, value) => {
      let low = 0;
      let high = arr.length - 1;

      while (low <= high) {
        let mid = Math.floor((low + high) / 2);
        if (value === arr[mid]) {
          return mid;
        } else if (value > arr[mid]) {
          low = mid + 1;
        } else {
          high = mid - 1;
        }
      }

      return -1;
    }

```