# Все операции с объектами в JavaScript

## Создание объектов
1. **Литерал объекта** — `{ key: value }`.
2. **Конструктор Object()** — `new Object()` или `Object()`.
3. **Object.create(proto, propertiesObject)** — создаёт объект с указанным прототипом.
4. **Object.assign(target, ...sources)** — копирует свойства из источников в целевой объект.
5. **Spread-оператор (`...`)** — `{ ...obj }` создаёт поверхностную копию.
6. **Класс (ES6)** — `new ClassName()`.
7. **Функция-конструктор** — `new ConstructorFunction()`.
8. **Object.fromEntries(iterable)** — создаёт объект из массива пар [ключ, значение].

## Свойства и дескрипторы
9. **Object.defineProperty(obj, prop, descriptor)** — определяет или изменяет свойство с дескриптором.
10. **Object.defineProperties(obj, props)** — определяет или изменяет несколько свойств.
11. **Object.getOwnPropertyDescriptor(obj, prop)** — возвращает дескриптор свойства.
12. **Object.getOwnPropertyDescriptors(obj)** — возвращает все дескрипторы свойств.
13. **Дескрипторы данных** — `value`, `writable`, `enumerable`, `configurable`.
14. **Дескрипторы доступа** — `get`, `set`, `enumerable`, `configurable`.
15. **Object.seal(obj)** — делает объект нерасширяемым, все свойства configurable: false.
16. **Object.freeze(obj)** — замораживает объект (нельзя изменять, добавлять, удалять).
17. **Object.preventExtensions(obj)** — запрещает добавление новых свойств.
18. **Object.isSealed(obj)** — проверяет, запечатан ли объект.
19. **Object.isFrozen(obj)** — проверяет, заморожен ли объект.
20. **Object.isExtensible(obj)** — проверяет, можно ли добавлять свойства.

## Доступ к свойствам
21. **Точечная нотация** — `obj.property`.
22. **Скобочная нотация** — `obj["property"]` (поддерживает вычисляемые имена).
23. **Опциональная цепочка** — `obj?.property` или `obj?.["property"]` (безопасный доступ).
24. **Вычисляемые имена** — `{ [expression]: value }`.
25. **Object.getOwnPropertyNames(obj)** — возвращает массив имён собственных свойств (включая неперечисляемые).
26. **Object.getOwnPropertySymbols(obj)** — возвращает массив собственных Symbol-свойств.
27. **Object.keys(obj)** — возвращает массив перечисляемых собственных ключей (строки).
28. **Object.values(obj)** — возвращает массив перечисляемых собственных значений.
29. **Object.entries(obj)** — возвращает массив пар [ключ, значение] для перечисляемых свойств.
30. **Reflect.ownKeys(obj)** — возвращает все собственные ключи (строки и символы).
31. **`in` оператор** — проверяет наличие свойства (включая унаследованные): `"key" in obj`.
32. **obj.hasOwnProperty(key)** — проверяет собственное свойство (не унаследованное).
33. **Object.hasOwn(obj, key)** — статический аналог `hasOwnProperty` (ES2022).
34. **`for...in` цикл** — перебирает перечисляемые свойства (включая унаследованные).
35. **`for...of` с Object.keys/values/entries** — перебор собственных свойств.

## Удаление свойств
36. **`delete obj.property`** — удаляет свойство. Возвращает true/false.
37. **`delete obj["property"]`** — удаляет через скобочную нотацию.
38. **Удаление всех свойств** — `Object.keys(obj).forEach(key => delete obj[key])`.
39. **Очистка объекта** — `Object.assign(obj, {})` (замена) или цикл с `delete`.

## Копирование объектов
40. **Поверхностное копирование (shallow)** — `{ ...obj }`, `Object.assign({}, obj)`.
41. **Глубокое копирование (deep)** — `JSON.parse(JSON.stringify(obj))` (только JSON-безопасное).
42. **Структурированное клонирование** — `structuredClone(obj)` (ES2022).
43. **Копирование с прототипом** — `Object.create(Object.getPrototypeOf(obj), Object.getOwnPropertyDescriptors(obj))`.
44. **Object.assign(target, ...sources)** — копирует перечисляемые собственные свойства.

## Сравнение объектов
45. **`obj1 === obj2`** — строгое сравнение ссылок (не содержимого).
46. **`obj1 == obj2`** — нестрогое сравнение ссылок.
47. **`Object.is(obj1, obj2)`** — сравнивает ссылки (отличается для NaN и -0).
48. **Сравнение содержимого** — `JSON.stringify(obj1) === JSON.stringify(obj2)` (не для циклических).
49. **Глубокое сравнение** — рекурсивная проверка всех свойств.
50. **Поверхностное сравнение** — `Object.keys(obj1).every(key => obj1[key] === obj2[key]) && Object.keys(obj1).length === Object.keys(obj2).length`.

## Прототипы и наследование
51. **Object.getPrototypeOf(obj)** — возвращает прототип объекта.
52. **Object.setPrototypeOf(obj, proto)** — устанавливает прототип (медленно, не рекомендуется).
53. **obj.__proto__** — устаревший геттер/сеттер прототипа (не использовать).
54. **Object.create(proto, props)** — создаёт объект с указанным прототипом.
55. **obj.isPrototypeOf(anotherObj)** — проверяет, является ли obj прототипом другого объекта.
56. **Object.prototype.isPrototypeOf(obj)** — проверяет прототипную цепочку.
57. **`instanceof` оператор** — проверяет, является ли объект экземпляром класса.
58. **`Object.prototype.constructor`** — ссылка на функцию-конструктор.

## Методы объекта (Object.prototype)
59. **obj.toString()** — возвращает строковое представление (`[object Object]`).
60. **obj.valueOf()** — возвращает примитив объекта (обычно сам объект).
61. **obj.hasOwnProperty(key)** — проверяет собственное свойство.
62. **obj.propertyIsEnumerable(key)** — проверяет, является ли свойство перечисляемым.
63. **obj.isPrototypeOf(anotherObj)** — проверяет прототипную связь.
64. **obj.toLocaleString(locales, options)** — локализованное строковое представление.

## Статические методы Object
65. **Object.keys(obj)** — массив перечисляемых собственных ключей.
66. **Object.values(obj)** — массив перечисляемых собственных значений.
67. **Object.entries(obj)** — массив пар [ключ, значение].
68. **Object.fromEntries(iterable)** — создаёт объект из пар.
69. **Object.assign(target, ...sources)** — копирует свойства.
70. **Object.create(proto, props)** — создаёт объект с прототипом.
71. **Object.defineProperty(obj, prop, descriptor)** — определяет свойство.
72. **Object.defineProperties(obj, props)** — определяет несколько свойств.
73. **Object.getOwnPropertyDescriptor(obj, prop)** — возвращает дескриптор.
74. **Object.getOwnPropertyDescriptors(obj)** — все дескрипторы.
75. **Object.getOwnPropertyNames(obj)** — все собственные строковые ключи.
76. **Object.getOwnPropertySymbols(obj)** — все собственные Symbol-ключи.
77. **Object.getPrototypeOf(obj)** — возвращает прототип.
78. **Object.setPrototypeOf(obj, proto)** — устанавливает прототип.
79. **Object.is(obj1, obj2)** — строгое сравнение (SameValue).
80. **Object.isExtensible(obj)** — проверяет расширяемость.
81. **Object.isFrozen(obj)** — проверяет заморозку.
82. **Object.isSealed(obj)** — проверяет запечатывание.
83. **Object.preventExtensions(obj)** — запрещает добавление свойств.
84. **Object.seal(obj)** — запечатывает объект.
85. **Object.freeze(obj)** — замораживает объект.
86. **Object.hasOwn(obj, key)** — проверяет собственное свойство (ES2022).
87. **Object.groupBy(items, callback)** — группирует элементы (ES2024).

## Операторы с объектами
88. **`new` оператор** — создаёт экземпляр через конструктор.
89. **`delete` оператор** — удаляет свойство.
90. **`in` оператор** — проверяет наличие свойства.
91. **`instanceof` оператор** — проверяет экземпляр класса.
92. **`typeof obj`** — возвращает `"object"` (или `"function"` для функций).
93. **Spread-оператор (`...`)** — копирует и расширяет объекты.
94. **Rest-оператор (`...`)** — собирает оставшиеся свойства.
95. **`??` (нулевое слияние)** — работает с объектами (не путать с `||`).
96. **`?.` (опциональная цепочка)** — безопасный доступ к свойствам.

## Продвинутые операции
97. **Деструктуризация объекта** — `const { a, b } = obj`.
98. **Деструктуризация с переименованием** — `const { a: newName } = obj`.
99. **Деструктуризация со значением по умолчанию** — `const { a = 10 } = obj`.
100. **Деструктуризация вложенных объектов** — `const { a: { b } } = obj`.
101. **Rest в деструктуризации** — `const { a, ...rest } = obj`.
102. **Сокращённые свойства** — `{ a, b }` (эквивалентно `{ a: a, b: b }`).
103. **Сокращённые методы** — `{ method() {} }` (эквивалентно `{ method: function() {} }`).
104. **Геттеры и сеттеры** — `{ get prop() {}, set prop(val) {} }`.
105. **Вычисляемые имена методов** — `{ [propName]() {} }`.
106. **Свойства-аксессоры** — `Object.defineProperty(obj, 'prop', { get() {}, set(val) {} })`.
107. **Приватные поля (классы)** — `#privateField`.
108. **Статические поля (классы)** — `static staticField`.
109. **Обработка циклических ссылок** — библиотека `flatted` или ручной обход.
110. **Проверка на пустой объект** — `Object.keys(obj).length === 0 && obj.constructor === Object`.
111. **Преобразование объекта в Map** — `new Map(Object.entries(obj))`.
112. **Преобразование Map в объект** — `Object.fromEntries(map)`.
113. **Фильтрация объекта** — `Object.fromEntries(Object.entries(obj).filter(([k, v]) => condition))`.
114. **Маппинг значений объекта** — `Object.fromEntries(Object.entries(obj).map(([k, v]) => [k, transform(v)]))`.
115. **Объединение объектов (с перезаписью)** — `{ ...obj1, ...obj2 }` или `Object.assign({}, obj1, obj2)`.
116. **Объединение объектов (без перезаписи)** — `{ ...obj2, ...obj1 }` (obj1 перезаписывает obj2).
117. **Удаление свойства из объекта (возврат нового)** — `{ ...obj, [key]: undefined }` (поверхностно).
118. **Удаление через деструктуризацию** — `const { [key]: _, ...rest } = obj`.
119. **Проверка на NaN в объекте** — `Object.values(obj).some(Number.isNaN)`.
120. **Глубокое объединение** — рекурсивный `Object.assign` или библиотека `lodash.merge`.