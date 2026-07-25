# Python Advanced — Asyncio

> Interview format: **Question** → **Common answer** → **Reference**

---

### Q1: What is `asyncio` and when do you use it?

**Common answer:**  
`asyncio` is the standard library framework for concurrent I/O using coroutines, an event loop, and non-blocking sockets. Best for many concurrent network/file waits in one thread. Not a silver bullet for CPU-bound work (offload that to processes or executors).

**Reference:**  
[`asyncio` — Asynchronous I/O](https://docs.python.org/3/library/asyncio.html) · [PEP 3156 – Asynchronous IO Support](https://peps.python.org/pep-3156/)

---

### Q2: Coroutine vs task vs future?

**Common answer:**  
- **Coroutine object**: result of calling an `async def` function; must be awaited or scheduled.  
- **Task**: schedules a coroutine on the event loop; tracks completion; cancellable.  
- **Future**: low-level awaitable placeholder for a result set later (Tasks are Futures).  

**Reference:**  
[Coroutines and Tasks](https://docs.python.org/3/library/asyncio-task.html)

---

### Q3: What does `await` actually do?

**Common answer:**  
`await` suspends the current coroutine until the awaitable completes, yielding control to the event loop so other tasks can run. It only works inside `async def` (or async comprehensions). Blocking the event loop (CPU-heavy sync code, sync I/O) freezes all tasks.

**Reference:**  
[PEP 492 – Coroutines with async and await syntax](https://peps.python.org/pep-0492/) · [Awaitable objects](https://docs.python.org/3/library/asyncio-task.html#awaitables)

---

### Q4: `create_task` vs awaiting a coroutine directly?

**Common answer:**  
`await coro()` runs that coroutine now (structured, sequential from the caller’s view). `asyncio.create_task(coro())` schedules it concurrently and returns a Task you can await later. Fire-and-forget tasks need strong exception handling (they can log “Task exception was never retrieved”).

**Reference:**  
[`asyncio.create_task`](https://docs.python.org/3/library/asyncio-task.html#asyncio.create_task)

---

### Q5: How does cancellation work?

**Common answer:**  
`task.cancel()` injects `CancelledError` at the next `await`. Code should use `try/finally` or `async with` for cleanup. From 3.8+, `CancelledError` inherits `BaseException` (not `Exception`) so bare `except Exception` won’t swallow cancellation incorrectly in the same way—still handle carefully.

**Reference:**  
[Task cancellation](https://docs.python.org/3/library/asyncio-task.html#task-cancellation) · [What’s New 3.8 — CancelledError](https://docs.python.org/3/whatsnew/3.8.html#asyncio)

---

### Q6: `gather` vs `TaskGroup`?

**Common answer:**  
`asyncio.gather` runs awaitables concurrently and collects results; `return_exceptions=True` avoids failing fast. `asyncio.TaskGroup` (3.11+) is structured concurrency: if one task fails, others are cancelled and errors surface as an `ExceptionGroup`. Prefer TaskGroup for safer lifetime management in modern code.

**Reference:**  
[`asyncio.gather`](https://docs.python.org/3/library/asyncio-task.html#asyncio.gather) · [`asyncio.TaskGroup`](https://docs.python.org/3/library/asyncio-task.html#task-groups) · [PEP 654 – Exception Groups](https://peps.python.org/pep-0654/)

---

### Q7: How do you run blocking code from asyncio?

**Common answer:**  
Use `asyncio.to_thread()` (3.9+) or `loop.run_in_executor()` so blocking work doesn’t stall the event loop. CPU-heavy work often belongs in a `ProcessPoolExecutor`.

**Reference:**  
[`asyncio.to_thread`](https://docs.python.org/3/library/asyncio-task.html#asyncio.to_thread) · [Executors](https://docs.python.org/3/library/concurrent.futures.html)

---

### Q8: What is the difference between concurrency and parallelism here?

**Common answer:**  
Asyncio provides **concurrency** (interleaved waiting) on one thread via cooperative multitasking. **Parallelism** means simultaneous execution on multiple cores (processes / multi-threaded free-threaded builds / native extensions). Asyncio overlaps I/O waits; it does not multi-core pure Python CPU by itself.

**Reference:**  
[Asyncio intro](https://docs.python.org/3/library/asyncio.html)

---

### Q9: Common asyncio pitfalls in interviews?

**Common answer:**  
1) Calling async functions without awaiting.  
2) Blocking the loop.  
3) Creating tasks without retaining references.  
4) Mixing threads and asyncio without thread-safe APIs (`call_soon_threadsafe`).  
5) Forgetting timeouts (`asyncio.wait_for`, `timeout` context manager in 3.11+).

**Reference:**  
[`asyncio.timeout`](https://docs.python.org/3/library/asyncio-task.html#asyncio.timeout) · [Developing with asyncio](https://docs.python.org/3/library/asyncio-dev.html)

---

## Related

- [[Python Advanced - GIL Concurrency Multiprocessing]]
- [[Python Advanced - Iterators Generators]]
- [[Advanced Python Interview Index]]
