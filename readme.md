# Учебный проект

https://github.com/AnastasiyaDev/components

# Заметки

можно добавлять [метки на циклы](https://learn.javascript.ru/while-for#метки-для-break-continue), а потом делать breake или continue по ним



`/` в строке позволяет написать с новой строки, в выводе не виден  
`/` - экранирует  
`/ + n, t, ..` - вывод спец символов

### Преобрзовние к булеву типу 
`!!` перед переменной

### Преобразование к числу
* строгое `+`: 
```
var a = '443';
+a
```
* мягкое 

`parseInt(number , system)` -  преобразует строку в целое число до первого не числового символа

`parseFloat()` - аналогично, только с дробным, ошибка на второй точке

### Проверка на число 

`NaN !== NaN`

`isNaN()` - проверка  на NaN, `isFinite()` - проверка на infyity и NaN  

### Проверка на тип данных

1.  `typeof` - подходит для примитивов, кроме `null` и функций  
2.  `[[Class]]` - использование `{}.toString.call(obj).slice(8, -1);` возвращает подходит только только для встроенных объектов  
3.  `Array.isArray(arr)` - возвращает `true` только если `arr` – массив  
4.  `instanceof` - использование `user instanceof User`, возвращает `true || false`, даже учитывает наследование  
5.  "Утиная типизация" `«If it looks like a duck, swims like a duck and quacks like a duck, then it probably is a duck (who cares what it really is)».`

### Округление числа 
Округления числа побитовым оператором:  
`(12.34^0) = 12` - скобки нужны, т.к. приоритет у `^` маленький  

`Math.floor` - Округляет вниз  
`Math.ceil` -  Округляет вверх  
`Math.round` - Округляет до ближайшего целого  

--------------

`**` - возведение в степень `( 2 ** 3 == 8)`

Для поиска подстроки использовать:

`substr(start, [ ,length])`  
`slice(stast, [ , end])`

**Удобно для преобразования цветов:**
```
var n = 255;
alert( n.toString(16) ); // ff
```

**Случайное число в интервале:**  
`Math.random() * (max - min) + min` - дробное  
`Math.round(Math.random() * (max - min) + min)` - целое  

---------------  

## Объекты

`Object.assign(name, karma)` - копирует данные из объекта `name` в объект `karma`  
`Object.keys(user)` - массив ключей объекта `user`  
`Object.values(user)` - массив значений ключей объекта `user`  
`Object.entries(user)` - массив массивов полей `user` 

Можно удалить поле из объекта: `delete obj.name`  

Проверить существует ли поле в объекте:  
*оператор `in`: `'age' in obj`  
*прировнять к `undefined`  
*самое простое: `if(obj.age)`  

Проверка на объект: `typeof 'object' && !== null`, т.к. null выдает на `typeof => 'object'`


**Если имя свойства хранится в переменной, то обратиться к нему можно только через `[]`, не через точку.**  

**Массивы**
`Array.isArray(arr);` - проверка на массив

`arr.length=0` - очистка массива, так же можно задать длинну и укоротить его  

Метоты массивов:
![](/assets/img/methods.png)

**Функции**

Есть встроенные методы у функций `foo`, например имеет `foo.name` - имя `foo` `foo.length` - количество параметров  

Замыкание - функция и ее лексическое окруженние  


`function foo (arg1, arg2, ...rest){}` - `...rest` - массив оставшихся незаданных параметров `rest` - название массива, может быть любым  

**Декоратор**

Принемает функцию и то что должно быть до и поле нее, возвращает до + результат функции + после  

```

function wrapperDecorator(f, before, after) {
	return function() {
		return before + f.apply(this, arguments) + end; // apply - для уневерсальности вызова
	};	
}

wrapperDecorator(getDay, '<div>', '</div>') // обернуть результат функции в div

```

**Преобразование объектов: `toString` и `valueOf`**

* Любой объект в логическом контексте – `true`, даже если это пустой массив `[]` или объект `{}`
* У большинства объектов нет `valueOf`, за исключением объекта Data, поэтому преобразование идет к строке  
* если есть + перед выражением (например +room), или операции с числами(-, /, *) берется преобразование `valueOf`, если его нет, то `toString`  
* Массивы - они же объекты имеют только строковое преобразование 
* Два объекта равны только тогда, когда это один и тот же объект  

**bing**

Вызов `bind` также позволяет фиксировать первые аргументы функции (**«каррировать»** её), и таким образом из общей функции получить её «частные» варианты – чтобы использовать их многократно без повтора одних и тех же аргументов каждый раз.  

```
function mul(a, b) {
  return a * b;
};

// double умножает только на два
var double = mul.bind(null, 2); // контекст фиксируем null, он не используется
```
 
**Время**

`Date.now()` - секунды c 1970
`performance.now()` - cчитает доли секунды 

### JSON

**`JSON.parse(str, reviver)`** из **JSON -> JavaScript-объект/массив/значение**

`reviver` - второй параметр для интеллектуального восстановления из строки, который является функцией `function(key, value)`.  
Пример использования: 
```
var str = '{"title":"Конференция","date":"2014-11-30T12:00:00.000Z"}';`
var event = JSON.parse(str, function(key, value) {
  if (key == 'date') return new Date(value);
  return value;
});
alert( event.date.getDate() );
```

**`JSON.stringify`**

`JSON.stringify(value, replacer, space)` из **JS-объект -> JSON**

`value` - сам объект, который надо превратить в JSON  

необязательные параметры:  
`replacer` - можно указать массив свойств, которые подлежат сериализации. Или написать в функции `if (key == 'window') return undefined;` - св-во `windows` будет пропущено  
  
`space` - отвечает за форматирование, если он является числом – то уровни вложенности в JSON оформляются указанным количеством пробелов, если строкой – вставляется эта строка.

Серелизовать объекты ссылающиеся друг на друга не выйдет!!!

### Прототипы  

obj.__proto__ - прототип `obj.__proto__ = { name: 'obj', ...}` - запись в __proto__
аналогичная запись Oblect.setPrototypeOf(obj, {}); - ее и надо использовать
Oblect.getPrototypeOf(obj);

`.prototype` - у функций конструкторов


`obj.hasOwnProperty(prop)` возвращает `true`, если свойство prop принадлежит самому объекту `obj`, иначе `false`.  

**Протипное наследование**

для общих методов всех объектов есть ссылка `Array.prototype.__proto__`, равная `Object.prototype`  
![](/assets/img/extend.png)

* В явном виде new String, new Number и new Boolean никогда не вызываются  
* Значения null и undefined не имеют свойств  

** Процесс наследования **  

`Child.prototype = Object.create(Parent.prototype);` `Child` и `Parent` - конструкторы  
`Child.prototype.constructor = Child;` - чтобы не потерять свойство `constructor` (есть в `prototype` по умолчанию), указывающее на функцию-конструктор  

Добавить свой метод в прототип, чтобы он был общим для всех элементов класса (экономия ресурсов)  
```
Child.prototype.jump = function() {
  ...
}
```  
Если свойства и/или методы внутри конструктора ребенка и роителя соввпадают, то можно упростить код и в ребенке использовать:  
```
function Child(name) {
  Parent.apply(this, arguments);
}
```  
Вызов метода родителя внутри своего:
```
Child.prototype.run = function() {
   // вызвать метод родителя, передав ему текущие аргументы
   Parent.prototype.run.apply(this, arguments);
   this.jump();
}
```
# Ресурсы 

* [доки по Markdown](https://github.com/OlgaVlasova/markdown-doc/blob/master/README.md#Lines) и [еще](http://paulradzkov.com/2014/markdown_cheatsheet/)
* [доки по emmet(ускореное написание)](https://docs.emmet.io/cheat-sheet/)
* [как писать документацию к коду](http://usejsdoc.org/)
* [доки по Веб-технологим(в частности JS)](https://developer.mozilla.org/ru/docs/Web/JavaScript)
