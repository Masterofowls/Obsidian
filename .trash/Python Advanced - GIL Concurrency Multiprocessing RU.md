# Python Advanced — GIL, Concurrency, Multiprocessing (RU)

> Формат: **Вопрос** → **Типичный ответ** → **Источник**  
> EN: [[Python Advanced - GIL Concurrency Multiprocessing]]

---

### В1: Что такое GIL?

**Типичный ответ:**  
Global Interpreter Lock в CPython — мьютекс, из‑за которого в одном процессе в каждый момент выполняет Python bytecode только один поток. Упрощает refcount; ограничивает CPU multi-threading. I/O часто отпускает GIL.

**Источник:**  
[GIL glossary](https://docs.python.org/3/glossary.html#term-global-interpreter-lock)

---

### В2: Threads vs processes?

**Типичный ответ:**  
`threading` — I/O, shared memory, GIL на pure-Python CPU. `multiprocessing` — отдельный интерпретатор, true parallel CPU, IPC через queue/pipe. `concurrent.futures` — high-level API.

**Источник:**  
[`threading`](https://docs.python.org/3/library/threading.html) · [`multiprocessing`](https://docs.python.org/3/library/multiprocessing.html)

---

### В3: Почему threads не ускоряют pure-Python CPU loop?

**Типичный ответ:**  
GIL: один поток с bytecode. Параллелизм — processes, native с release GIL, free-threaded builds.

**Источник:**  
[GIL glossary](https://docs.python.org/3/glossary.html#term-global-interpreter-lock)

---

### В4: Когда multi-threading всё же полезен?

**Типичный ответ:**  
I/O-bound, ожидания, UI; библиотеки с release GIL (часто NumPy). Для high concurrency I/O — ещё asyncio.

**Источник:**  
[`threading`](https://docs.python.org/3/library/threading.html)

---

### В5: Free-threading / no-GIL?

**Типичный ответ:**  
Экспериментальные free-threaded сборки CPython (с 3.13): GIL можно отключить. Trade-off single-thread perf и совместимость экосистемы. В интервью — opt-in, version-dependent.

**Источник:**  
[What's New 3.13](https://docs.python.org/3/whatsnew/3.13.html#free-threaded-cpython) · [PEP 703](https://peps.python.org/pep-0703/)

---

### В6: Per-interpreter GIL?

**Типичный ответ:**  
PEP 684: у subinterpreter свой GIL → параллель между интерпретаторами с изоляцией. Не то же самое, что free-threading внутри одного.

**Источник:**  
[PEP 684](https://peps.python.org/pep-0684/)

---

### В7: Как безопасно шарить state между threads?

**Типичный ответ:**  
Locks, Condition, `queue.Queue`, меньше shared mutable. GIL ≠ корректная синхронизация ваших структур.

**Источник:**  
[`queue`](https://docs.python.org/3/library/queue.html)

---

### В8: spawn vs fork?

**Типичный ответ:**  
fork (Unix): COW, опасно с multithreaded parent. spawn (Windows/macOS default): свежий интерпретатор, медленнее, безопаснее. Всегда `if __name__ == "__main__"`.

**Источник:**  
[start methods](https://docs.python.org/3/library/multiprocessing.html#contexts-and-start-methods)

---

### В9: Race и deadlock?

**Типичный ответ:**  
Race — результат зависит от расписания без sync. Deadlock — циклический захват lock. Митигация: меньше shared state, порядок lock, timeout, message-passing.

**Источник:**  
[`Lock`](https://docs.python.org/3/library/threading.html#lock-objects)

---

### В10: Как GIL влиял на решение в проекте?

**Типичный ответ:**  
См. [[Python Advanced - Practical Experience RU]] В11–В12: threads не дали speedup на CPU → process pool / native.

**Источник:**  
Практическая заметка

---

## Связанное

- [[Python Advanced - GIL Concurrency Multiprocessing]]
- [[Python Advanced - Asyncio RU]]
- [[Advanced Python Interview Index RU]]
