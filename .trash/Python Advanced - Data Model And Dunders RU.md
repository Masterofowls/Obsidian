# Python Advanced — Data Model And Dunders (RU)

> EN: [[Python Advanced - Data Model And Dunders]]

---

### В1: Что такое data model в Python?

**Типичный ответ:**  
Набор правил и special methods (`__…__`), определяющих поведение объектов: атрибуты, операторы, итерация, context managers, hash/eq и т.д.

**Источник:** [Data model](https://docs.python.org/3/reference/datamodel.html)

---

### В2: `__repr__` vs `__str__`?

**Типичный ответ:**  
`__repr__` — однозначное dev-представление; `__str__` — читаемое для пользователя. `print`/`str` → `__str__` (fallback `__repr__`). Контейнеры берут `__repr__` элементов.

**Источник:** [`__repr__` / `__str__`](https://docs.python.org/3/reference/datamodel.html#object.__repr__)

---

### В3: Equality и hashing?

**Типичный ответ:**  
Равные объекты → одинаковый hash (если hashable). Мутабельные с value-eq часто `__hash__ = None`.

**Источник:** [`__hash__`](https://docs.python.org/3/reference/datamodel.html#object.__hash__)

---

### В4: `__new__` vs `__init__`?

**Типичный ответ:**  
`__new__` создаёт экземпляр; `__init__` инициализирует. `__new__` — immutables, singletons, subclass built-ins.

**Источник:** [`__new__`](https://docs.python.org/3/reference/datamodel.html#object.__new__)

---

### В5: Sequence protocol (`__getitem__`, `__len__`)?

**Типичный ответ:**  
Индексация/slice; без `__iter__` возможен fallback iteration по индексам до `IndexError`.

**Источник:** [Emulating container types](https://docs.python.org/3/reference/datamodel.html#emulating-container-types)

---

### В6: `__call__`?

**Типичный ответ:**  
Объект вызывается как функция. Классы-декораторы, stateful callables.

**Источник:** [`__call__`](https://docs.python.org/3/reference/datamodel.html#object.__call__)

---

### В7: `__add__` vs `__radd__`?

**Типичный ответ:**  
Сначала left; если `NotImplemented` — reflected right. Для interop типов.

**Источник:** [Emulating numeric types](https://docs.python.org/3/reference/datamodel.html#emulating-numeric-types)

---

### В8: Truthiness / `__bool__`?

**Типичный ответ:**  
`__bool__`, иначе `__len__` (0 = false), иначе True по умолчанию.

**Источник:** [`__bool__`](https://docs.python.org/3/reference/datamodel.html#object.__bool__)

---

## Связанное

- [[Advanced Python Interview Index RU]]
