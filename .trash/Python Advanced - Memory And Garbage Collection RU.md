# Python Advanced — Memory And Garbage Collection (RU)

> EN: [[Python Advanced - Memory And Garbage Collection]]

---

### В1: Как CPython управляет памятью?

**Типичный ответ:**  
В основном **reference counting**; **cyclic GC** собирает циклы, которые refcount не освободит.

**Источник:** [`gc`](https://docs.python.org/3/library/gc.html)

---

### В2: Зачем cyclic GC при refcount?

**Типичный ответ:**  
Циклы (`a.b=b; b.a=a`) держат refcount > 0, хотя объект недостижим.

**Источник:** [`gc`](https://docs.python.org/3/library/gc.html)

---

### В3: Поколения GC?

**Типичный ответ:**  
3 generations; молодые собираются чаще (большинство объектов короткоживущие).

**Источник:** [`gc.get_threshold`](https://docs.python.org/3/library/gc.html#gc.get_threshold)

---

### В4: Weak reference?

**Типичный ответ:**  
Ссылка без увеличения refcount — кэши, observers; объект может быть собран.

**Источник:** [`weakref`](https://docs.python.org/3/library/weakref.html)

---

### В5: Опасности `__del__`?

**Типичный ответ:**  
Время не гарантировано (циклы, shutdown). Лучше context managers / explicit close.

**Источник:** [`__del__`](https://docs.python.org/3/reference/datamodel.html#object.__del__)

---

### В6: Как дебажить рост памяти?

**Типичный ответ:**  
`tracemalloc`, `gc.get_objects()`, метрики RSS; искать безграничные кэши и unclosed resources.

**Источник:** [`tracemalloc`](https://docs.python.org/3/library/tracemalloc.html)

---

### В7: Interning / small int cache?

**Типичный ответ:**  
Деталь реализации; `is` ≠ `==`. Для identity — только `None`/`True`/`False` как синглтоны.

**Источник:** [PEP 8 comparisons](https://peps.python.org/pep-0008/#programming-recommendations)

---

### В8: GIL и память?

**Типичный ответ:**  
GIL упрощал refcount; free-threading меняет модель атомарности.

**Источник:** [PEP 703](https://peps.python.org/pep-0703/)

---

## Связанное

- [[Python Advanced - Practical Experience RU]]
- [[Advanced Python Interview Index RU]]
