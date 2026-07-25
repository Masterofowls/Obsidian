# Python Advanced — Iterators And Generators (RU)

> EN: [[Python Advanced - Iterators Generators]]

---

### В1: Iterator vs iterable?

**Типичный ответ:**  
Iterable — `__iter__` (или sequence `__getitem__`). Iterator — `__next__` + `__iter__` (self).

**Источник:** [Glossary](https://docs.python.org/3/glossary.html#term-iterable)

---

### В2: Что такое generator?

**Типичный ответ:**  
Функция с `yield` / genexp — ленивый iterator с сохранённым состоянием. Экономит память на потоках данных.

**Источник:** [yield](https://docs.python.org/3/reference/expressions.html#yieldexpr)

---

### В3: `yield from`?

**Типичный ответ:**  
Делегирование subgenerator/iterator: прокидывает yield/send/throw, возвращает return value subgen.

**Источник:** [PEP 380](https://peps.python.org/pep-0380/)

---

### В4: `.send()` / `.throw()` / `.close()`?

**Типичный ответ:**  
Классические coroutine-методы generator. Для concurrent I/O предпочтительнее `async`/`await`.

**Источник:** [Generator methods](https://docs.python.org/3/reference/expressions.html#generator-iterator-methods)

---

### В5: Genexp vs listcomp?

**Типичный ответ:**  
`[]` — eager list; `()` — lazy, one-shot.

**Источник:** [Generator expressions](https://docs.python.org/3/reference/expressions.html#generator-expressions)

---

### В6: Как работает `for`?

**Типичный ответ:**  
`iter(obj)` затем `next` до `StopIteration`.

**Источник:** [for statement](https://docs.python.org/3/reference/compound_stmts.html#the-for-statement)

---

### В7: `itertools` — что знать senior?

**Типичный ответ:**  
`chain`, `islice`, `groupby`, `product`, `tee`… композиция без больших intermediate list.

**Источник:** [`itertools`](https://docs.python.org/3/library/itertools.html)

---

### В8: Исчерпание / reuse?

**Типичный ответ:**  
Iterator/generator обычно single-pass. Список — multi-pass (новый `iter` каждый раз).

**Источник:** [Iterator types](https://docs.python.org/3/library/stdtypes.html#iterator-types)

---

### В9: Async iterators?

**Типичный ответ:**  
`__aiter__`/`__anext__`, `async for`; async generators: `async def` + `yield`.

**Источник:** [PEP 525](https://peps.python.org/pep-0525/)

---

## Связанное

- [[Advanced Python Interview Index RU]]
