# Python Advanced — Metaclasses And ABC (RU)

> EN: [[Python Advanced - Metaclasses And ABC]]

---

### В1: Что такое metaclass?

**Типичный ответ:**  
«Класс класса». По умолчанию `type`. Кастомизация создания классов. Часто достаточно `__init_subclass__` / декораторов.

**Источник:** [Metaclasses](https://docs.python.org/3/reference/datamodel.html#metaclasses)

---

### В2: Что происходит при определении class body?

**Типичный ответ:**  
Тело → namespace dict → `Metaclass(name, bases, namespace)`. Хуки: `__prepare__`, `__set_name__`, `__init_subclass__`.

**Источник:** [PEP 3115](https://peps.python.org/pep-3115/) · [PEP 487](https://peps.python.org/pep-0487/)

---

### В3: `type` как metaclass?

**Типичный ответ:**  
`type(name, bases, dict)` строит класс динамически. ORM/declarative API часто так устроены.

**Источник:** [`type`](https://docs.python.org/3/library/functions.html#type)

---

### В4: Когда `__init_subclass__` вместо metaclass?

**Типичный ответ:**  
Регистрация/валидация subclasses без сложности metaclass — современный default для плагинов.

**Источник:** [PEP 487](https://peps.python.org/pep-0487/)

---

### В5: Что такое ABC?

**Типичный ответ:**  
Abstract Base Class: abstract methods, `isinstance`/`issubclass`, virtual subclass через `register()`.

**Источник:** [`abc`](https://docs.python.org/3/library/abc.html)

---

### В6: `@abstractmethod`?

**Типичный ответ:**  
Нельзя инстанцировать, пока не переопределены все abstract members.

**Источник:** [`abstractmethod`](https://docs.python.org/3/library/abc.html#abc.abstractmethod)

---

### В7: Protocol vs ABC?

**Типичный ответ:**  
Protocol — structural typing (duck) для type checkers. ABC — nominal + runtime. См. PEP 544.

**Источник:** [PEP 544](https://peps.python.org/pep-0544/)

---

### В8: `collections.abc`?

**Типичный ответ:**  
Стандартные интерфейсы Iterable/Sequence/Mapping/… — контракты и `isinstance`.

**Источник:** [`collections.abc`](https://docs.python.org/3/library/collections.abc.html)

---

### В9: Грабли metaclasses?

**Типичный ответ:**  
Конфликт metaclass при multiple inheritance; overuse; сложный debug. Проще — decorator / `__init_subclass__`.

**Источник:** [Metaclasses](https://docs.python.org/3/reference/datamodel.html#metaclasses)

---

## Связанное

- [[Advanced Python Interview Index RU]]
