# Python Advanced — Context Managers And Resources (RU)

> EN: [[Python Advanced - Context Managers And Resources]]

---

### В1: Что такое context manager?

**Типичный ответ:**  
Объект с `__enter__`/`__exit__` для `with` — гарантированный setup/teardown. Async: `__aenter__`/`__aexit__`.

**Источник:** [PEP 343](https://peps.python.org/pep-0343/)

---

### В2: Как работает `with`?

**Типичный ответ:**  
`__enter__` → блок → `__exit__(type, val, tb)`. True из `__exit__` подавляет исключение.

**Источник:** [with statement](https://docs.python.org/3/reference/compound_stmts.html#the-with-statement)

---

### В3: `@contextmanager`?

**Типичный ответ:**  
Generator → CM: до `yield` enter, после exit; `try/finally` вокруг yield.

**Источник:** [`contextlib.contextmanager`](https://docs.python.org/3/library/contextlib.html#contextlib.contextmanager)

---

### В4: Почему CM лучше `__del__` для ресурсов?

**Типичный ответ:**  
Детерминированный cleanup. Finalizers ненадёжны по времени.

**Источник:** [`contextlib`](https://docs.python.org/3/library/contextlib.html)

---

### В5: `ExitStack`?

**Типичный ответ:**  
Динамический стек CM/callback — когда число ресурсов заранее неизвестно.

**Источник:** [`ExitStack`](https://docs.python.org/3/library/contextlib.html#contextlib.ExitStack)

---

### В6: Locks как CM?

**Типичный ответ:**  
`with lock:` — acquire/release. `RLock` — reentrant. Документировать порядок lock.

**Источник:** [`threading.Lock`](https://docs.python.org/3/library/threading.html#lock-objects)

---

### В7: Async context managers?

**Типичный ответ:**  
`async with` для sessions, pools, `TaskGroup`, `timeout`.

**Источник:** [`asynccontextmanager`](https://docs.python.org/3/library/contextlib.html#contextlib.asynccontextmanager)

---

### В8: `suppress`?

**Типичный ответ:**  
Узкое подавление известных исключений (напр. cleanup FileNotFoundError).

**Источник:** [`suppress`](https://docs.python.org/3/library/contextlib.html#contextlib.suppress)

---

## Связанное

- [[Advanced Python Interview Index RU]]
