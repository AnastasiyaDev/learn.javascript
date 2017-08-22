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

### Объекты

`Array.isArray(arr);` - проверка на массив

`Object.assign(name, karma)` - копирует данные из объекта `name` в объект `karma`
`Object.keys(user)` - массив ключей объекта `user`
`Object.values(user)` - массив значений ключей объекта `user`
`Object.entries(user)` - массив массивов полей `user`

Есть встроенные методы у функций `foo`, например имеет `foo.name` - имя `foo` `foo.length` - количество параметров

# Ресурсы 

* [доки по Markdown](https://github.com/OlgaVlasova/markdown-doc/blob/master/README.md#Lines)
* [доки по emmet(ускореное написание)](https://docs.emmet.io/cheat-sheet/)
* [как писать документацию к коду](http://usejsdoc.org/)
* [доки по Веб-технологим(в частности JS)](https://developer.mozilla.org/ru/docs/Web/JavaScript)
