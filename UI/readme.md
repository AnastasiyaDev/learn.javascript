# Документ, события, интерфейсы

### Окружение

![](../assets/img/window.png)

`window.navigator` - содержит общую информацию о браузере и операционной системе  
`window.location.href` - содержит информацию о текущем URL  

### Навигация

Включает текстовые узлы:  
![](../assets/img/navigation.png)  

Только по элементам  
![](../assets/img/elementNavigation.png) 
 
![](../assets/img/searchElements.png)

* `elem.matches(css)` - проверяет, удовлетворяет ли элемент CSS-селектору  
* `elem.closest(css)` - ближайший вверх по DOM  

**Особая навигация у таблиц и форм**

### Коллекции  

DOM-коллекции, такие как `childNodes` не являются JavaScript-массивами.  
Можно для перебора коллекции использовать обычный цикл `for(var i=0; i<elems.length; i++)`  

или сделать из коллекции массив:  
```
var elems = document.documentElement.childNodes;

[].forEach.call(elems, function(elem) {
  alert( elem ); // HEAD, текст, BODY
});
```
or   
```
var elems = document.documentElement.childNodes;
elems = Array.prototype.slice.call(elems); // теперь elems - массив
```  

### Атрибуты и DOM-свойства

![](../assets/img/attr.png)  

Для классов  

* `className` - возвращает классы в виде строки  
* `classList` - объект (IE+, для IE8+ библиотека [classList.js](https://github.com/eligrey/classList.js))  
* `elem.classList.contains("class")` – возвращает true/false, в зависимости от того, есть ли у элемента класс `class`  
* `elem.classList.add/remove("class")` – добавляет/удаляет класс `class`  
* `elem.classList.toggle("class")` – если класса `class` нет, добавляет его, если есть – удаляет.  

Есть поддержка (IE10+) особенного обращения к `data`-атрибутам:  
* `data-user-location="street"` - атрибут, доступ к нему: `elem.dataset.userLocation`  


В отличие от свойств, атрибуты:  
* Всегда являются строками.  
* Их имя нечувствительно к регистру (ведь это HTML)  
* Видны в innerHTML (за исключением старых IE)  

**Всегда пользуемся свойствами, кроме:**  
1. Кастомные атрибуты  
2. Когда нужно получить «оригинальное значение» стандартного HTML-атрибута, например, `<input value="...">`  
3. Когда нужно получить список всех атрибутов, включая пользовательские. Для этого используется коллекция `attributes`  


______________________________________________

id создает в глобальной области видимости объект


# Ресурсы 

* [Шпаргалка по работе с DOM от Мезина](https://github.com/AnastasiyaDev/learn.javascript/blob/master/assets/dom.pdf)