# Python Advanced — Closures, Decorators, Scopes (RU)

> Формат: **Вопрос** → **Типичный ответ** → **Источник**  
> EN: [[Python Advanced - Closures Decorators Scopes]]

---

### В1: Что такое правило LEGB?

**Типичный ответ:**  
Порядок поиска имён: **L**ocal → **E**nclosing → **G**lobal → **B**uilt-in. `global` привязывает к модулю; `nonlocal` — к ближайшей внешней функции (не к global).

**Источник:**  
[Scopes and Namespaces](https://docs.python.org/3/tutorial/classes.html#python-scopes-and-namespaces)

---

### В2: Что такое замыкание (closure)?

**Типичный ответ:**  
Функция, которая «помнит» переменные из enclosing scope через cell, даже после выхода из внешней функции. Видно в `__closure__`. Применение: фабрики, декораторы, колбэки с конфигом.

**Источник:**  
[Naming and binding](https://docs.python.org/3/reference/executionmodel.html#naming-and-binding)

---

### В3: Классический баг late-binding в замыканиях?

**Типичный ответ:**  
```python
funcs = [lambda: i for i in range(3)]  # все вернут 2
```
Замыкание держит *переменную*, не значение. Фикс: `lambda i=i: i` или `partial`.

**Источник:**  
[FAQ — lambdas in a loop](https://docs.python.org/3/faq/programming.html#why-do-lambdas-defined-in-a-loop-with-different-values-all-return-the-same-result)

---

### В4: Что такое декоратор?

**Типичный ответ:**  
Callable, принимающий функцию/класс и возвращающий замену (обычно wrapper). `@dec` ≡ `f = dec(f)`. Сквозная логика: лог, тайминг, retry, auth, cache, metrics.

**Источник:**  
[Glossary — decorator](https://docs.python.org/3/glossary.html#term-decorator) · [`functools.wraps`](https://docs.python.org/3/library/functools.html#functools.wraps)

---

### В5: Зачем `functools.wraps`?

**Типичный ответ:**  
Копирует `__name__`, `__doc__`, signature на wrapper — иначе ломаются отладка, OpenAPI, тесты.

**Источник:**  
[`functools.wraps`](https://docs.python.org/3/library/functools.html#functools.wraps)

---

### В6: Декоратор с аргументами — как?

**Типичный ответ:**  
Фабрика: внешняя функция принимает параметры декоратора и возвращает сам декоратор, который возвращает wrapper. Паттерн `@retry(times=3)`.

**Источник:**  
[Function definitions](https://docs.python.org/3/reference/compound_stmts.html#function)

---

### В7: Класс-декоратор vs функция-декоратор?

**Типичный ответ:**  
Класс: `__init__(func)` + `__call__` для stateful-обёртки. Функция — легче. Декоратор класса получает class object после тела класса.

**Источник:**  
[`__call__`](https://docs.python.org/3/reference/datamodel.html#object.__call__)

---

### В8: `staticmethod` / `classmethod` / `property`?

**Типичный ответ:**  
Instance — `self`. Classmethod — `cls` (альт. конструкторы). Staticmethod — без авто-аргумента. Property — managed attribute через descriptor.

**Источник:**  
[`classmethod`](https://docs.python.org/3/library/functions.html#classmethod) · [`property`](https://docs.python.org/3/library/functions.html#property)

---

### В9: Что делает `lru_cache`?

**Типичный ответ:**  
Мемоизация с LRU-вытеснением для hashable args. Для чистых дорогих функций. Осторожно с methods (`self` в ключе) и side effects.

**Источник:**  
[`lru_cache`](https://docs.python.org/3/library/functools.html#functools.lru_cache)

---

### В10: Когда декораторы использовать на проекте?

**Типичный ответ:**  
Повторяющаяся обёртка (auth, retry, metrics). Не использовать, если прячут бизнес-логику или достаточно одного явного вызова. См. практический блок: [[Python Advanced - Practical Experience RU]].

**Источник:**  
[PEP 20](https://peps.python.org/pep-0020/)

---

## Связанное

- [[Python Advanced - Closures Decorators Scopes]]
- [[Python Advanced - Practical Experience RU]]
- [[Advanced Python Interview Index RU]]
