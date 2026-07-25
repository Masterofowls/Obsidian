# Python Advanced — Asyncio (RU)

> Формат: **Вопрос** → **Типичный ответ** → **Источник**  
> EN: [[Python Advanced - Asyncio]] · Практика: [[Python Advanced - Practical Experience RU]]

---

### В1: Что такое `asyncio` и когда использовать?

**Типичный ответ:**  
Фреймворк stdlib для конкурентного I/O: корутины, event loop, неблокирующие сокеты. Хорош при большом числе ожиданий. CPU-bound — в процессы/executor, не в loop.

**Источник:**  
[`asyncio`](https://docs.python.org/3/library/asyncio.html)

---

### В2: Coroutine vs Task vs Future?

**Типичный ответ:**  
Coroutine — объект `async def` (нужен await/schedule). Task — запланированная корутина, отменяемая. Future — низкоуровневый placeholder результата (Task — подтип Future).

**Источник:**  
[Coroutines and Tasks](https://docs.python.org/3/library/asyncio-task.html)

---

### В3: Что делает `await`?

**Типичный ответ:**  
Приостанавливает корутину до завершения awaitable и отдаёт управление loop. Работает в `async def`. Блокировка loop (sync I/O, тяжёлый CPU) останавливает все task.

**Источник:**  
[PEP 492](https://peps.python.org/pep-0492/)

---

### В4: `create_task` vs просто `await coro()`?

**Типичный ответ:**  
`await coro()` — последовательно с точки зрения вызывающего. `create_task` — параллельный schedule, Task можно await позже. Fire-and-forget требует обработки исключений.

**Источник:**  
[`create_task`](https://docs.python.org/3/library/asyncio-task.html#asyncio.create_task)

---

### В5: Как работает cancellation?

**Типичный ответ:**  
`task.cancel()` → `CancelledError` на следующем `await`. Cleanup в `finally` / `async with`. С 3.8 `CancelledError` — `BaseException`.

**Источник:**  
[Task cancellation](https://docs.python.org/3/library/asyncio-task.html#task-cancellation)

---

### В6: `gather` vs `TaskGroup`?

**Типичный ответ:**  
`gather` — собрать результаты; `return_exceptions=True` не валит всё сразу. `TaskGroup` (3.11+) — structured concurrency: ошибка → отмена siblings, `ExceptionGroup`.

**Источник:**  
[`TaskGroup`](https://docs.python.org/3/library/asyncio-task.html#task-groups) · [PEP 654](https://peps.python.org/pep-0654/)

---

### В7: Как вызывать blocking-код из asyncio?

**Типичный ответ:**  
`asyncio.to_thread()` или `run_in_executor`. CPU-heavy — `ProcessPoolExecutor`.

**Источник:**  
[`to_thread`](https://docs.python.org/3/library/asyncio-task.html#asyncio.to_thread)

---

### В8: Concurrency vs parallelism здесь?

**Типичный ответ:**  
Asyncio — concurrency (переключение на await) в одном потоке. Parallelism — несколько ядер (процессы / free-threaded / native).

**Источник:**  
[asyncio intro](https://docs.python.org/3/library/asyncio.html)

---

### В9: Типичные грабли asyncio?

**Типичный ответ:**  
Нет `await`; blocking в loop; Task без ссылок; threads без `call_soon_threadsafe`; нет timeout.

**Источник:**  
[Developing with asyncio](https://docs.python.org/3/library/asyncio-dev.html)

---

### В10: «Использовали async в проекте — как?»

**Типичный ответ:**  
См. практику: зачем (I/O), стек (ASGI + async DB + httpx), проблемы, тесты — [[Python Advanced - Practical Experience RU]] В5–В10.

**Источник:**  
Практическая заметка + docs выше

---

## Связанное

- [[Python Advanced - Asyncio]]
- [[Python Advanced - GIL Concurrency Multiprocessing RU]]
- [[Advanced Python Interview Index RU]]
