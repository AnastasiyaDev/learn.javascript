**`JSON.parse(str)`**

`JSON.parse(str)` из **JSON -> JavaScript-объект/массив/значение**

Для интеллектуального восстановления из строки у `JSON.parse(str, reviver)` есть второй параметр reviver, который является функцией `function(key, value)`. Пример использования: 

`var str = '{"title":"Конференция","date":"2014-11-30T12:00:00.000Z"}';`

`var event = JSON.parse(str, function(key, value) {
  if (key == 'date') return new Date(value);
  return value;
});`

`alert( event.date.getDate() );`

**`JSON.stringify`**

`JSON.stringify(value, replacer, space)` пеобразует **JS-объект -> JSON**

Cоздаем объект `var obj = {...}`, передаем его в `JSON.stringify(obj)`

Во втором параметре `JSON.stringify(value, replacer)` можно указать массив свойств, которые подлежат сериализации. Или написать в функции `if (key == 'window') return undefined;` - св-во `windows` будет пропущено


`JSON.stringify(value, replacer, space)` третий параметр `space` отвечает за форматирование, если он является числом – то уровни вложенности в JSON оформляются указанным количеством пробелов, если строкой – вставляется эта строка.

Серелизовать объекты ссылающиеся друг  на друга не выйдет!!!
