# Python Advanced — Performance And Internals (RU)

> EN: [[Python Advanced - Performance And Internals]]

---

### В1: Как искать bottleneck?

**Типичный ответ:**  
Сначала measure: `cProfile`/pyinstrument/scalene. Оптимизировать hotspots: алгоритм, аллокации, vectorize, cache, native, правильная concurrency model.

**Источник:** [Profilers](https://docs.python.org/3/library/profile.html)

---

### В2: Bytecode / `dis`?

**Типичный ответ:**  
CPython компилирует в bytecode; `dis.dis(f)` — дизассемблер. Не переносимо на другие implementations.

**Источник:** [`dis`](https://docs.python.org/3/library/dis.html)

---

### В3: Почему listcomp часто быстрее manual loop?

**Типичный ответ:**  
Меньше Python-overhead в простых transform; но важнее алгоритм. Читаемость важна.

**Источник:** [Comprehensions](https://docs.python.org/3/reference/expressions.html#displays-for-lists-sets-and-dictionaries)

---

### В4: Производительность `dict`?

**Типичный ответ:**  
Avg O(1) lookup; insertion-ordered (гарантия с 3.7); memory overhead hash table.

**Источник:** [dict](https://docs.python.org/3/library/stdtypes.html#mapping-types-dict) · [3.6 dict](https://docs.python.org/3/whatsnew/3.6.html#new-dict-implementation)

---

### В5: Конкатенация строк?

**Типичный ответ:**  
`''.join(parts)` / StringIO; не `s +=` в больших циклах как идиома.

**Источник:** [FAQ strings](https://docs.python.org/3/faq/programming.html#what-is-the-most-efficient-way-to-concatenate-many-strings-together)

---

### В6: `__slots__` для perf?

**Типичный ответ:**  
Много мелких объектов — меньше RAM. Не default на все классы; measure.

**Источник:** [`__slots__`](https://docs.python.org/3/reference/datamodel.html#slots)

---

### В7: Specializing interpreter (3.11+)?

**Типичный ответ:**  
PEP 659 adaptive specializing bytecode — ускорения «из коробки» на CPython 3.11+.

**Источник:** [PEP 659](https://peps.python.org/pep-0659/)

---

### В8: Threads / processes / asyncio — выбор под perf?

**Типичный ответ:**  
I/O many conn → asyncio/threads. CPU pure Python → processes/native. NumPy часто отпускает GIL.

**Источник:** [[Python Advanced - GIL Concurrency Multiprocessing RU]]

---

### В9: Memory vs speed trade-offs?

**Типичный ответ:**  
Caches, preallocation, generators vs lists, layout данных, native libs. Язык trade-off важнее микробенчмарков.

**Источник:** [`lru_cache`](https://docs.python.org/3/library/functools.html#functools.lru_cache)

---

## Связанное

- [[Python Advanced - Practical Experience RU]]
- [[Advanced Python Interview Index RU]]
