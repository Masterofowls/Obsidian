# Python Advanced — Descriptors And Properties (RU)

> EN: [[Python Advanced - Descriptors And Properties]]

---

### В1: Что такое descriptor?

**Типичный ответ:**  
Объект с `__get__`/`__set__`/`__delete__` на классе. Через него работают `property`, methods, `classmethod`, `staticmethod`.

**Источник:** [Descriptor HowTo](https://docs.python.org/3/howto/descriptor.html)

---

### В2: Data vs non-data descriptor?

**Типичный ответ:**  
Data: есть `__set__`/`__delete__` — приоритет над instance `__dict__`. Non-data: только `__get__` — instance attr может переопределить.

**Источник:** [Descriptor protocol](https://docs.python.org/3/howto/descriptor.html#descriptor-protocol)

---

### В3: Как работает `property`?

**Типичный ответ:**  
Data descriptor: get/set/delete через функции. Валидация, computed fields, lazy API без смены публичного интерфейса.

**Источник:** [`property`](https://docs.python.org/3/library/functions.html#property)

---

### В4: Почему method становится bound method?

**Типичный ответ:**  
Function — non-data descriptor; `__get__` на instance возвращает bound method с `self`.

**Источник:** [Functions and methods](https://docs.python.org/3/howto/descriptor.html#functions-and-methods)

---

### В5: `__slots__`?

**Типичный ответ:**  
Фиксированный набор атрибутов, часто без `__dict__` → меньше памяти. Минусы: меньше динамики, нюансы наследования.

**Источник:** [`__slots__`](https://docs.python.org/3/reference/datamodel.html#slots)

---

### В6: Порядок lookup атрибутов (упрощённо)?

**Типичный ответ:**  
Data descriptor → instance dict → non-data/class attr → `__getattr__`.

**Источник:** [Customizing attribute access](https://docs.python.org/3/reference/datamodel.html#customizing-attribute-access)

---

### В7: `__getattr__` vs `__getattribute__`?

**Типичный ответ:**  
`__getattribute__` — на каждый доступ. `__getattr__` — только если обычный lookup не нашёл.

**Источник:** [`__getattribute__`](https://docs.python.org/3/reference/datamodel.html#object.__getattribute__)

---

### В8: PEP 487 / `__set_name__`?

**Типичный ответ:**  
Descriptor узнаёт имя атрибута на owner-классе; плюс `__init_subclass__`.

**Источник:** [PEP 487](https://peps.python.org/pep-0487/)

---

## Связанное

- [[Advanced Python Interview Index RU]]
