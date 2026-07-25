# Python Advanced — Context Managers And Resources

> Interview format: **Question** → **Common answer** → **Reference**

---

### Q1: What is a context manager?

**Common answer:**  
An object that defines `__enter__` and `__exit__` for use with `with`. It guarantees setup/teardown (files, locks, transactions, temp state) even if exceptions occur. `async with` uses `__aenter__` / `__aexit__`.

**Reference:**  
[PEP 343 – The “with” Statement](https://peps.python.org/pep-0343/) · [Data model — With Statement Context Managers](https://docs.python.org/3/reference/datamodel.html#with-statement-context-managers)

---

### Q2: How does `with` work under the hood?

**Common answer:**  
Call `__enter__` (return value bound via `as`), execute the block, then call `__exit__(exc_type, exc, tb)`. If `__exit__` returns a true value, the exception is suppressed; otherwise it propagates. `None`/false re-raises.

**Reference:**  
[The with statement](https://docs.python.org/3/reference/compound_stmts.html#the-with-statement)

---

### Q3: `@contextmanager` generator pattern?

**Common answer:**  
`contextlib.contextmanager` turns a generator into a context manager: code before `yield` is enter; after is exit; use `try/finally` around `yield` for cleanup. Lightweight alternative to a full class.

**Reference:**  
[`contextlib.contextmanager`](https://docs.python.org/3/library/contextlib.html#contextlib.contextmanager)

---

### Q4: Why prefer context managers over `__del__` for resources?

**Common answer:**  
Deterministic cleanup at block exit. Finalizers (`__del__`) are delayed/non-guaranteed with cycles and shutdown. Production code uses `with`, `closing`, `ExitStack`, and explicit close methods.

**Reference:**  
[`contextlib`](https://docs.python.org/3/library/contextlib.html) · [Data model — `__del__`](https://docs.python.org/3/reference/datamodel.html#object.__del__)

---

### Q5: What is `ExitStack`?

**Common answer:**  
A programmable stack of context managers and callbacks—enter variable numbers of resources dynamically and unwind them safely. Essential when the set of resources isn’t fixed statically.

**Reference:**  
[`contextlib.ExitStack`](https://docs.python.org/3/library/contextlib.html#contextlib.ExitStack)

---

### Q6: Reentrant locks and context managers?

**Common answer:**  
Many lock types support `with lock:` via context manager protocol. `RLock` allows same-thread re-acquisition. Always document lock ordering to avoid deadlocks when nesting.

**Reference:**  
[`threading.Lock`](https://docs.python.org/3/library/threading.html#lock-objects)

---

### Q7: Async context managers — examples?

**Common answer:**  
`async with aiohttp.ClientSession()`, DB async pools, `asyncio.TaskGroup` (3.11+), `asyncio.timeout`. Never call async enter/exit from sync code without a running loop.

**Reference:**  
[Async context managers](https://docs.python.org/3/reference/datamodel.html#asynchronous-context-managers) · [`contextlib.asynccontextmanager`](https://docs.python.org/3/library/contextlib.html#contextlib.asynccontextmanager)

---

### Q8: Suppressing exceptions intentionally?

**Common answer:**  
`contextlib.suppress(ExceptionType)` or returning true from `__exit__`. Prefer explicit suppress for narrow cases (e.g. ignore `FileNotFoundError` on cleanup) over bare `except:`.

**Reference:**  
[`contextlib.suppress`](https://docs.python.org/3/library/contextlib.html#contextlib.suppress)

---

## Related

- [[Python Advanced - Data Model And Dunders]]
- [[Python Advanced - Asyncio]]
- [[Advanced Python Interview Index]]
