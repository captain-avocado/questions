**Прототип**  - резервное хранилище свойств и методов объекта, которое автоматически используется при поиске. Ссылка на прототип хранится в специальном свойстве объекта ``__proto__``. 

Прототипы – механизм, с помощью которого объекты наследуют свойства друг друга.

JavaScript – язык прототипного наследования, потому что каждый объект имеет объект-прототип, а он в свою очередь может иметь свой прототип и так далее. Это называется цепочкой прототипов.

Пример:

```js
function Person(first, last) {
  this.first = first;
  this.last = last;
}

var person = new Person('Bob', 'Smith');
console.log(person.first + person.last); //выводит заданные свойства
console.log(person.valueOf()); //метод valueOf не определен в функции-конструкторе, браузер обращается к прототипу объекта – Object, у которого есть данный метод

```

Цепочка прототипов из примера: 

``person -> Person -> Object``

Каждая функция-конструктор имеет свойство prototype - это объект, который содержит в себе свойство constructor, указывающее на исходную функцию-конструктор. Существующие свойства прототипа можно проверить, обратившись в этому объекту.

Пример:

```js
console.log(Person.prototype); //только {constructor: f}
console.log(Object.prototype); //множество определенных в прототипе свойств, например, toString(), valueOf()
```

Можно вынести методы функции-конструктора в прототип. Таким образом при создании новых объектов не будет выделяться дополнительная память для методов, ведь они одинаковы, и не требуется хранить их в каждом объекте – достаточно вынести их в прототип. 

```js
Person.prototype.getFullname = function() {
  return this.first + ' ' + this.last';
}

console.log(person.getFullname()); // Bob Smith
```

Создадим новую функцию-конструктор, описывающую рабочего. И установим наследование методов Person для новой функции.

```js
function Worker(first, last, company) {
  Person.call(this, first, last); //используем функцию-конструктор Person, чтобы передать одинаковые свойства с привязкой текущего контекста 
  
  this.company = company; //добавляем новое свойство
}

Worker.prototype = Object.create(Person.prototype); //создаем новый объект с прототипом Person.prototype. Он становится прототипом Worker
Worker.prototype.constructor = Worker; //чтобы свойство constructor нового прототипа не указывало на Person, сохраняем в него ссылку на Worker

//добавляем новые методы ПОСЛЕ установки наследования, тк там создается новый пустой объект и если добавим до – свойства не будут записаны
Worker.prototype.getInfo = function() {
  return 'Worker ' + this.getFullname() + ' from company ' + this.company;
}

var worker = new Worker('Bob', 'Smith 2', 'Microsoft');
console.log(worker.getFullname());
console.log(worker.getInfo());
```

Весь исходный код:
```js
function Person(first, last) {
  this.first = first;
  this.last = last;
}

var person = new Person('Bob', 'Smith');
console.log(person.first + person.last); //выводит заданные свойства
console.log(person.valueOf()); //метод valueOf не определен в функции-конструкторе, браузер обращается к прототипу объекта – Object, у которого есть данный метод

//

console.log(Person.prototype); //только {constructor: f}
console.log(Object.prototype); //множество определенных в прототипе свойств, например, toString(), valueOf()

//

Person.prototype.getFullname = function() {
  return this.first + ' ' + this.last';
}

console.log(person.getFullname()); // Bob Smith

//

function Worker(first, last, company) {
  Person.call(this, first, last); //используем функцию-конструктор Person, чтобы передать одинаковые свойства с привязкой текущего контекста 
  
  this.company = company; //добавляем новое свойство
}

Worker.prototype = Object.create(Person.prototype); //создаем новый объект с прототипом Person.prototype. Он становится прототипом Worker
Worker.prototype.constructor = Worker; //чтобы свойство constructor нового прототипа не указывало на Person, сохраняем в него ссылку на Worker

//добавляем новые методы ПОСЛЕ установки наследования, тк там создается новый пустой объект и если добавим до – свойства не будут записаны
Worker.prototype.getInfo = function() {
  return 'Worker ' + this.getFullname() + ' from company ' + this.company;
}

var worker = new Worker('Bob', 'Smith 2', 'Microsoft');
console.log(worker.getFullname());
console.log(worker.getInfo());
```

Источники:

- https://developer.mozilla.org/ru/docs/Learn/JavaScript/%D0%9E%D0%B1%D1%8A%D0%B5%D0%BA%D1%82%D1%8B/Object_prototypes
- https://developer.mozilla.org/ru/docs/Learn/JavaScript/%D0%9E%D0%B1%D1%8A%D0%B5%D0%BA%D1%82%D1%8B/Inheritance
- https://learn.javascript.ru/prototypes